# Squad Processes

This document captures processes and, high-level ways of working between the engineers. Our goal is to promote collaboration and communication; avoiding working in silos as much as possible.

## Implementation posts

An implementation post is posted in Slack (and ideally a discussion) around the planned path for building a given feature. Thinking through the expected path from the development aspect provides some aspects of foresight and ensures your solution correctly understands the problem, and maintains typical practices, approaches, and standards here at Vaan.

The implementation post also provides a great launch pad for your PR description to detail your approach and gives the squad members who will ultimately be reviewing your PR a place to provide input upfront and before you start coding. A PR review should be about small changes and improvements, not large overhauls, and the implementation meeting helps to avoid the need for drastic changes in approach.

While they may take some time to write (the first example took 5 minutes, the second took about an hour with some light testing of Flow, Marketing Email automation, and research for Klaviyo transactional emails), the benefits of thinking through the problem wholistically and doing up front investigations for what is possible can avoid getting stuck and large time investments on incomplete solutions.

The implementation meeting can be as simple or complex as the feature requires. Here are some examples of implementation meetings:

**Examples:**

- Building out a hero section that leverages the theme starter hero with a few modifications:

> “Hey all I am starting on TICKET-1234. After review, I believe we can approach this utilizing the hero from the theme starter. Most the functionality will be out of the box with styling to match the brand. I am utilizing our CSS modules for the styles.
>
> The one difference is that this client requires the border of the section to be editable via the customizer. I will be adding settings border-color and border-size that will control this.
>
> I don’t have any open questions that need to be addressed”

- Building a Membership feature powered by tags and Recharge subscriptions and talking out the subtasks for each part

> Hey all, I am starting on TICKET-4321. This is a pretty complex concept that will likely require several subtasks.
>
> Essentially, they want the ability for a user to ‘request membership’. The membership then unlocks the ability to access more cookie boxes for purchase. The membership should be automatically approved after x time. Upon approval, they should be sent an email to create their password.
>
> Once they are approved and logged in, they will be able to access these additional products as well as have a store experience that is unique to the members.
>
> They can also skip the approval process by making a purchase.
>
> There is also the ability to upgrade their membership from Base member, to Red membership, to Platinum membership. Red and platinum members are on a subscription (monthly and quarterly respectively). Each membership level gets them access to additional perks, a slightly different store experience and additional products.
>
> Here is how I am thinking about it so far
>
> - User signs up for an account with their email.
>   - We leverage the create account form, but hide the password field
>   - And accepts marketing field (or don’t select this, but apply for Klaviyo reset email to be transactional email)
>   - Password is randomly generated
>   - User is tagged with applied
> - Modify account creation email to instead say ‘application received’
> - Shopify flow tags a customer with membership level x amount of time after account is created
>   - Have the time either be in flow itself or based on Shop metafield
> - Klaviyo email is used to send customer reset password link (ideal) or reset password page link once new tag is applied
> - Ideally we have slightly different messaging for reset page based on coming from Klaviyo vs coming from traditional reset flow.
>   - Should be doable with a query param
> - Tags will be checked for getting membership levels for store experience
> - If subscription changes, user is tagged with membership level
>
> Outstanding Questions:
>
> - Will Klaviyo approve the email as transactional?
> - Do we usually setup Klaviyo emails? If not, are we able to do it in this case since part of transactional/core functionality
> - Do we need a specific page for the reset password form as part of this flow or can we link to it easily?

## Slack Notifications & Focus Time

Slack is the greatest tool for collaboration, and yet one that can be extremely disruptive particularly when deep thought and creativity is required. It is highly recommended that you find several times throughout the day to hide, close, or silence slack to get in focused work. Whether by using a formalized technique like Pomodoro or simply blocking time, it can greatly impact your productivity and ability to focus on a problem.

Communication of these focus times can be updating your slack status or blocking off time on your calendar. The more communication around it to the team, lets them know that they shouldn’t expect an immediate response even though it is working hours, but that you will check in. A focus block shouldn’t typically exceed more than 2 hours to come up for air, address any mentions/comments/feedback, and provide an opportunity for reviewing PRs.

A final benefit of focus time is that it can streamline tracking time in harvest and not having to balance starting new timers as you hop around to different tasks and projects.

## Github Notifications

While not required, it is recommended to enable Github notifications in slack. This allows us to know we have been mentioned or assigned and can help to unblock other’s work. As with slack notifications, the expectation isn’t that the response is immediate, but that the next time you are in slack, you would see a notification from the github integration and be aware that you should carve out time in your next break to address these items.

For setup of these, see this
[article](https://rasim.pro/blog/personal-slack-github-notifications-for-pull-requests-reviewers-how-to-set-up/).

## Hotfixes

Sometimes clients will require Hotfixes to a live theme. In my opinion, this should be a last resort and each team member should feel empowered to ask for the need of the hotfix while communicating the timing of getting an RC theme prepared.

If it is determined that a hotfix is the appropriate solution, the solution added as a hotfix should also be committed to the repo ASAP. It is recognized that this might mean it isn’t until the next morning, or later in the day, but it should be made a top priority and ideally a PR be opened at the same time the hotfix is implemented. This allows for tracking these changes and provides a reference to it through git history rather than just capturing it with live theme changes.
