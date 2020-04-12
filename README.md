# Platform Event Toast [![Tweet](https://img.shields.io/twitter/url/http/shields.io.svg?style=social&logo=twitter)](https://twitter.com/intent/tweet?text=Check%20out%20this%20amazing%20lwc%20toast%20component%20that%20uses%20platform%20events%20for%20real%20time%20notifications.%20&url=https://github.com/rahulmalhotra/Platform-Event-Toast-LWC&via=rahulcoder&hashtags=salesforce,sfdcstop,lightning,lwc,salesforceohana)

Platform Event Toast is a generic, reusable and admin-friendly toast component built in lwc.

## Overview

Platform Event Toast use platform events to display a toast as and when required. Once you install it in your org, you can drag and drop platform event toast in any lightning page using the app builder and even use inside custom lighting/lwc components. It'll help you to solve a variety of use cases one of which is described in the [Usage](#usage) section of this readme.

### Prerequisites

There are no such pre-requisites for installing and using this framework.
If you want to download the code in your local system, you can do it by the executing the below command or downloading the code directly as a zip file.

```
git clone https://github.com/rahulmalhotra/Platform-Event-Toast-LWC.git
```

### Installing

Platform Event Toast is very easy to use both for developers and admins. You can install this application in your salesforce org by using the **deploy to salesforce** button
present in the [deployment](#deployment) section of this readme. Installing this will add the following to your org :-

1. platformEventToast - Lightning Web Component
2. TostEvent - Platform Event

**Platform Event Toast** is now ready for use.

## Deployment

I have created an unmanaged package so that you can install it in your org very easily. <a href="https://login.salesforce.com/packaging/installPackage.apexp?p0=04t7F000005ZBuw">Click Here</a> to install the package now or use the below URL:-

```
https://login.salesforce.com/packaging/installPackage.apexp?p0=04t7F000005ZBuw
```

## Usage

### Displaying a warning when a record is saved

*Have you ever faced a requirement where you need to show warning message to the user who is trying to save a record but you also want that the record should be saved successfully without any restriction ?*

We have **Validation Rules** provided by salesforce but the issue with them is that they restrict the user and don't allow him/her to save a record.

**Use Case :-** Let's say you wanna show a warning to the user who is updating the Annual Revenue of the account. The new annual revenue is >= $50,000 but the user forgot to update the rating to **"Hot"**. In this scenario, the client doesn't want to restrict the user from saving the record but the user should know that the preferred rating for this account is **"Hot"**

Our **AWESOME Salesforce Admin** can fulfill this requirement using Platform Event Toast. All he has to do is to create a process builder on Account as shown below:-

Process Builder will run when an account record is created or edited as we want to show warning when a record is updated by the user.

![AccountProcessObject](https://github.com/rahulmalhotra/Platform-Event-Toast-LWC/blob/master/Images/AccountProcessObject.jpg)

We're setting the criteria that all of the conditions are met and we've added two conditions:-

1. Annual Revenue >= $50,000
2. Rating != Hot

We'll execute the process builder only when the specified changes are made to the record as we wan't to show warning only once.

![AccountProcessCriteria](https://github.com/rahulmalhotra/Platform-Event-Toast-LWC/blob/master/Images/AccountProcessCriteria.jpg)

At the end, we added an action where we're creating a Toast Event record by setting up properties of toast as shown below:-

![AccountProcessAction](https://github.com/rahulmalhotra/Platform-Event-Toast-LWC/blob/master/Images/AccountProcessAction.jpg)

*Note:-* **Key** is a required field and must be filled. A key is used to uniquely identify a toast event when it's displayed on a page.

Once your process builder is ready and activated, it's time to add our component to the lightning page. We just have to make sure that we're adding the same key here as we specified in the process builder:-

![AccountRecordPage](https://github.com/rahulmalhotra/Platform-Event-Toast-LWC/blob/master/Images/AccountRecordPage.jpg)

We can leave the other fields empty for this toast as we've setup everything from the process builder. In case, we haven't specified value of other fields in the process builder, we can fill those fields here.

*Once you've setup the toast successfully, you'll see the below result when Account's Annual Revenue >= $50,000 and Rating != Hot*

![AccountToast](https://github.com/rahulmalhotra/Platform-Event-Toast-LWC/blob/master/Images/AccountToast.jpg)

This is just a single use case. However, there can be multiple use cases where you can use this toast. You also have an option as:- **Run in System Mode** which will allow a toast to run in system mode i.e. the toast will be visible to all users of the org if the toast exists on the page that is opened by the user. This option can be used to create **Org Wide Announcements** by adding the toast as a part of utility bar so that it's available at application level no matter which page is opened by the user.

## Tools and Softwares used

You just need a salesforce org to run this application.
If you want to make any changes in the component, you can do that by pulling the LWC Component in VS Code IDE once you've deployed it in your org.
Below are the tools or softwares I use personally :-

* [VS Code](https://code.visualstudio.com) - Open Source IDE for Salesforce

## Todo

- [ ] Fix deployment issue in platform event with inline help text
- [ ] Fix :- GitHub Salesforce Deploy Tool not able to deploy LWC (Refer gsdt branch for that)

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on code of conduct and the process for submitting pull requests.

## Authors

* **Rahul Malhotra** - [@rahulcoder](https://twitter.com/rahulcoder)

## License

This project is licensed under the BSD 3-Clause License - see the [LICENSE.md](LICENSE.md) file for details.
