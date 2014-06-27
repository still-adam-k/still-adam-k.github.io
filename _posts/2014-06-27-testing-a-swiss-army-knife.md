---
layout: post
title: "Testing - A Swiss Army Knife"
modified: 2014-06-27 14:40:52 +0100
category:
tags:
image:
  feature: 
  credit: 
  creditlink: 
comments: 
share: 
---

Tests - A Swiss Army Knife

Let's start by making something cool. Let's start by making our own fluent test builder.
First is the test. It usually looks something like this:
{% highlight c# linenos %}
[Fact]
public void Probably_first_test_of_adding_user_to_our_service()
{
    var userData = new UserAccountRequest
    {
        Name = "John Kovalsky",
        Email = "someone@somedomain.com",
        DateOfBirth = DateTime.Parse("1990-10-01"),
        Password = "password",
        PhoneNumber = "123456789"
    };
    var subject = new UserManagementService();

    subject.AddUser(userData);

    Assert.Contains("123456789", subject.Users.Select(user => user.PhoneNumber));
}
{% endhighlight %}

Now, creating of our UserAccountRequest is simple, but crude. And when we get more tests, it should be extracted to separate method. Like:

{% highlight c# linenos %}
private static UserAccountRequest CreateUserAccountRequest()
{
    return new UserAccountRequest
    {
        Name = "John Kovalsky",
        Email = "someone@somedomain.com",
        DateOfBirth = DateTime.Parse("1990-10-01"),
        Password = "password",
        PhoneNumber = "123456789"
    };
}
{% endhighlight %}


But inevitably there will be more tests. One will require to test our account with invalid email, other with no password, and yet another one could check what happens if our account was born in the future. Each will require slightly different setup. So our options are:
- leave them as the are in the tests - but that will darken what we are actually testing, and unnecessery bloat the test
- have each method create separate - will bloat our test class, and is a nightmare to maintain
- create default, then customize - nice, but we don't want to have public setters just for the sake of tests

No, today we create - A builder!

So let's start by:

{% highlight c# linenos %}
class UserRequestBuilder
{
	private string defaultName;
    private string defaultEmail;
    private string defaultPhoneNumber;
    private string defaultPassword;
    private DateTime defaultBirthDate;


    public UserRequestBuilder()
    {
        defaultName = "John Kovalsky";
        defaultEmail = "someone@somedomain.com";
        defaultPhoneNumber = "123456789";
        defaultPassword = "password";
        defaultBirthDate = DateTime.Parse("1990-10-01");
    }

    internal UserAccountRequest Build()
    {
        return new UserAccountRequest
        {
            Name = defaultName,
            Email = defaultEmail,
            DateOfBirth = defaultBirthDate,
            Password = defaultPassword,
            PhoneNumber = defaultPhoneNumber
        };
    }
}
{% endhighlight %}

This creates a default variant equivalent for first test. Usage would be:

{% highlight c# linenos %}
var userData = new BuildUserRequest().Build();
{% endhighlight %}

Now, we can add customization methods for our default build values:

{% highlight c# linenos %}
public BuildUserRequest WithDateTime(string dateTime)
{
    this.defaultBirthDate = DateTime.Parse(dateTime);
    return this;
}

public BuildUserRequest WithEmail(string email)
{
    this.defaultEmail = email;
    return this;
}

public BuildUserRequest WithName(string email)
{
    this.defaultName = email;
    return this;
}

public BuildUserRequest WithPassword(string password)
{
    this.defaultPassword = password;
    return this;
}

public BuildUserRequest WithPhoneNumber(string phoneNumber)
{
    this.defaultPhoneNumber = phoneNumber;
    return this;
}
{% endhighlight %}

This way, we can create our objects like:

{% highlight c# lineos %}
var userData = new BuildUserRequest()
                .WithName("Malcolm")
                .WithEmail("malcolm@somecompany.com")
                .Build();
{% endhighlight %}

Pretty neat! But, we could get rid of one more thing, the Build method, by having:

{% highlight c# lineos %}
public static implicit operator UserAccountRequest(BuildUserRequest builder)
{
    return builder.Build();
}
{% endhighlight %}

So our final builder call for custom object looks like four lines of code:

{% highlight c# lineos %}
[Fact]
public void Probably_first_test_of_adding_user_to_our_service()
{
    var userData = new BuildUserRequest().WithPhoneNumber("123456789");
    var subject = new UserManagementService();

    subject.AddUser(userData);

    Assert.Contains("123456789", subject.Users.Select(user => user.PhoneNumber));
}
{% endhighlight %}

That may not be much impressive for simple POCO objects - but really shines with more complicated use cases e.g what would mysterious setup like:

{% highlight c# lineos %}
var service = new UserManagementService();
var mock = new Mock<IUserRepository>();
mock.Setup(o => o.GetUser(It.IsAny<int>())).Returns(expectedUser);
service.UsersRepository = mock.Object;
{% endhighlight %}

could look like:

{% highlight c# lineos %}
var service = new BuildUserManagementService().Returning(expectedUser);
{% endhighlight %}

now thats cutting out the crap!
