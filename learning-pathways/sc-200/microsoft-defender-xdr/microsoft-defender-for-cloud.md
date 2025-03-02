# Microsoft Defender for Cloud

Intro

Defender for Cloud used to be seperate but now is intergrated into the Defender XDR suite of product to make it one pane of glass.

<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

All of the data is discoved via network traffic which can give you an overview of your current estate.

Cloud Discovery - Network applications discovered

Cloud App Catalog - very similar to Cloud Discovery but these have been added via Microsoft or yourselves to onboard an application. This can be useful to target particular known applications.

OAuth Apps - some cloud applications require Authorisation to link into other application, of which depending on the level chosen I would highly suggest only allowing an Admin to approve the OAuth app as an when an applicaiton has been approved for the business requirements.

App Governance - Apps have different standards and technologies that score an application, when expanding a particular application. More information can be found here: [https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-manage-app-governance](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-manage-app-governance)



I have used this within the business to manage web applications that gives a great insight into what users use and if an possible data leakage is occouring.

For example, recent developments of Deekseek and various other AI models took the world by storm and many security professionals were also concerned about this.

Therefore, I created a Defender for cloud application policy that targets only the AI catergory and tag them as unsanctioned when a new application is found.&#x20;

{% hint style="info" %}
Create a workbook to ensure that the custom policies are working as exspected and this also gives you overall insight.&#x20;

There is always going to be excemption cases requried so please set up device groups when possible to manage them correctly within your company.
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

Sanctioned - Approved application that is used.

Unsanctioned - Blocked application that will display a blocked page when the user attempts to reach the webpage. (it takes up to 30mins for the site to be blocked)

Monitored - For end users, it prompts them them that when they go to the website, it suggests that the website is being monitored and this is where you can suggest an alternative applicaiton to be used.

