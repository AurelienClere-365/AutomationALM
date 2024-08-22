<a id="readme-top"></a>

<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->

[![LinkedIn][linkedin-shield]][linkedin-url]
[![MIT License][license-shield]][license-url]

![image](https://github.com/user-attachments/assets/7bc02206-732d-47d0-bf52-e40d633aa1c0)

# 🚀 AutomationALM for Power Platform and Dynamics 365 CE/CRM

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/AurelienClere-365/AutomationALM">
  </a>

  <p align="center">
    A solution to improve the ALM process in Power Platform and Dynamics 365 (CRM/CE). This solution is based on top of the ALM Accelerator made in the CoE Starter Kit.
    <br />
    <a href="https://www.powerazure365.com/blog-1/automation-alm-power-platform"><strong>Read my article »</strong></a>
    <br />
    <br />
    <a href="https://github.com/AurelienClere-365/AutomationALM/wiki"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://www.youtube.com/channel/UCVcla2nTDw1HLOx-Vio0Z2w">View YouTube Demo</a>
    ·
    <a href="https://github.com/AurelienClere-365/AutomationALM/issues/new?assignees=AurelienClere-365&labels=bug&projects=&template=bug_report.md&title=%5BBUG%5D+Title+of+the+bug">Report Bug</a>
    ·
    <a href="https://github.com/AurelienClere-365/AutomationALM/issues/new?assignees=AurelienClere-365&labels=enhancement&projects=&template=feature_request.md&title=%5BFEATURE+REQUEST%5D+Title+of+the+requirement">Request Feature</a>
  </p>
</div>


<!-- ABOUT THE PROJECT -->
## 🏡 About The Project

My goal here is to give to the community a solution for Power Platform to improve ALM process in terms of deployment. While the ALM Accelerator for me is the best tool (coupled with an Azure DevOps to manage solution deployment), it was still a manual process to release Dataverse solution. Coming from a D365 Finance Operations background at first, it was for me important (as a lazy guy) to decrease the amount of time needed to release something on a Dataverse environment !

Here's why:
* Your time should be focused on creating something amazing. A project that solves a problem and helps others
* You shouldn't be doing the same tasks over and over 🔁
* You should have a quality/rigorous release package for each new deployment without manual actions 💆‍♂️
* No manual deployment for Dataverse !
* Your source code is on GIT Control
* Pipelines from Microsoft in managed environment are not good 
* The solution will help you to manage the process in which sometimes Microsoft will also release something on your Dataverse at the same as time as you. (Retry process)

My solution is *just* on top of the ALM Accelerator solution. I will not cover in the repo how to setup it, but I will do it in my long article as usual 😄

The ALM Accelerator is a very good starter kit to configure a DevOps for Power Platform (end to end) and avoid taking a lot of times to configure it on your side manually. With the Automation ALM in top of it, believe me, you will save a LOT of times !

<!-- GETTING STARTED -->
## 🚀 Download the latest release

To get the managed solution to install, download the ZIP on the latest one available [HERE](https://github.com/AurelienClere-365/AutomationALM/releases) *Latest Release August 2024 - v1.0.20240822.1*

## ❗Prerequisites

As explained before, my solution is on top of ALM Accelerator, as a reminder you should install first those 2 solutions. If you need help on how to install and configure it, you can again [read my article](https://www.powerazure365.com/blog-1/automation-alm-power-platform)
* Creator Kit latest release - [Download it here](https://aka.ms/creatorkitdownload)
* ALM Accelerator latest release *March 2024* - [Download it here](https://github.com/microsoft/coe-starter-kit/releases/download/CoEStarterKit-March2024/CenterofExcellenceALMAccelerator_1.0.20240305.1_managed.zip)

You should have a Dataverse to install it of course 😙 , 3 connectors are used (check if you have any DLP before) : Outlook Office 365, Azure DevOps, Dataverse.
I will suggest a dedicated one, same one as you have used for the CoE Starter Kit and/or the ALM Accelerator.
Since I presume you already have install ALM Accelerator, you have in this case already an Azure Dev Ops organization and a DevOps Project. Remember that you have 1 Orga per tenant but could have multiple projects on it. You have 5 basic users licence and 1800 minutes/month of build pipelines for free.

* You DevOps organization should accept OData API Access.
  
![image](https://github.com/user-attachments/assets/8f79be51-adc9-4215-bd71-5f92278e22a8)

* Check that classic pipelines could be created too

![image](https://github.com/user-attachments/assets/4757ed71-f10a-4eb9-bd49-4b4f962e8a12)


* [Double check that the ALM Accelerator account can create policy for the validation build pipeline](https://github.com/microsoft/coe-starter-kit/issues/7930#issuecomment-2024283993)

* Finally as a reminder maybe, but in DevOps you have also some group variables for ALM Accelerator, so you could change it if you like, like me :

![image](https://github.com/user-attachments/assets/932fa4fa-e03a-4eba-a066-a0046bffa10d)


## 📖 Installation (first time)

_Below is the intrusctions to use the solution._

1. Install it
2. For the Connection references, use a service account and dedicated one that have access to the DevOps Organization and Project with the right permissions. Same thing for the Dataverse connector. You could setup a different one if you like for the Office 365 Outlook
3. You have multiple environment variables to setup too. A dedicated Flow (after installation called : *0 - Setup - GetDevOps Config* will help you to fill 3 of them : ApproverId + RepositoryId + ExportGit) so at first you could leave it empty for those 3 ones.
4. Go to the Model Driven App installed, change your personal settings with the right timezone. You could also share it to other users in your Dataverse.
5. Change the default view on the Environment variables section in the Model Driven App, my side I have added the field *Environment variable definition* + doing a filter on *dyna_* and then after pin as the default view and share to everyone. You could after review the list and check if all is good.
6. Activate FLOWS and in the right order ! Yes, there are 18 Power Automate. I made it normally simple based on the name and the number convention (to read it like an order by DESC :smile:) so 99 first and last are 10
7. On the Model Driven App, in Settings Group, you have to create your DEV environment(s) (with a / at the end) , the URL should be the same as the service connection name in DevOps. Create also all your solutions you have activated with ALM Accelerator Profile. Finally, you could also create your Power Pages (name could be retrieve in the Portal Management Model Driven App) *Be careful this part is only for Power Pages in standard model and not the enhanced model* - For enhanced model you could just put your Power Pages site on a normal Dataverse solution for ALM Process.
8. You are good to go for the Usage part 😈 

## 📖 Upgrade to the latest release

Just install it as an upgrade process in your Dataverse. Double check that each Power Automate flows are still "ON" after. I will in each release specifiy if there are any manual post actions or any new flow to activate.

## 📚 Usage

Remember here that you need first for the solution you want to deploy automatically to assign an ALM Profile in the ALM Accelerator Canvas App. Also, you still need to setup the *Configure Deployment settings* for each step (Validation,Test,Prod) in each solution. Globally, I don't replace those 2 parts, you still need to do it BEFORE using it with the AutomationALM.

But then, you can create ALM Deployments. I support 2 types : Validation then Test, Production

Assign your DEV environment in which your solution(s) are installed in unmanaged, and of course the right ALM Profile explained before.

You have 3 types : right away, on-demand (delay until a datetime), scheduling. 

For the scheduling you need to have a format scheduler in ISO 8601 (e.g I want to deliver this solution each day is PT1D, each week : PT1W , every 12 hours : PT12H)

Click Save, then assign all the ALM Solutions in the right order you want to deliver and just click launch it button ! That's it :smile: 

You will have an history log attached for each steps.

At the end you can also clone an existing deployment, or even ReLaunch it if it was of type "Right away"

You can also access in this case the Model Driven App via a Mobile (Power Apps iOS / Android) to remotely launch an existing deployment you already have done before, or pre-existing one.

You could check also the whole [WIKI](https://github.com/AurelienClere-365/AutomationALM/wiki) for more details.

<!-- ROADMAP -->
## 💡Roadmap / Subscribe

See the [Project Roadmap](https://github.com/users/AurelienClere-365/projects/2) for the backlog and current progress.

See the [open issues](https://github.com/AurelienClere-365/AutomationALM/issues) for a full list of proposed features (and known issues).

Don't forget that you can subscribe and get notifications on the repository for each new release, issues, discussions etc...

<!-- CONTRIBUTING -->
## 👐 Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please open an issue with the tag "enhancement".
While as of now, **I don't share the source code behind and give you only the managed solution of Power Platform**, if you want to contribute with me, go the [Discussion space](https://github.com/AurelienClere-365/AutomationALM/discussions)

Don't forget to give the project a star! Thanks again!

 
<!-- LICENSE -->
## 📝 License

Distributed under the MIT License. See [LICENSE](https://github.com/AurelienClere-365/AutomationALM/blob/main/LICENSE) in the repo for more information.


<!-- CONTACT -->
## 📢 Contact

Aurelien CLERE - [@aurelien_clere](https://twitter.com/aurelien_clere) 
LinkedIn : [Follow Me](https://www.linkedin.com/in/aurelien-clere/)

<!-- SPONSOR -->
## 👐 Support me

While I always do everything for free for the community, if you want to support me you can do it [here](https://buymeacoffee.com/aurelienclere) 

<!-- ACKNOWLEDGMENTS -->
## 👐 Acknowledgments

* [Thanks to my colleague Simon Parent for his help and feedbacks](https://www.linkedin.com/in/simon-parent-5377b215a/)


## 📚 Resources

* [CoE Starter Kit](https://github.com/microsoft/coe-starter-kit/)
* [ALM Accelerator](https://learn.microsoft.com/en-us/power-platform/guidance/alm-accelerator/overview)

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[issues-shield]: https://img.shields.io/github/issues-search/AurelienClere-365/AutomationALM?query=is%3Aissue%20is%3Aopen
[issues-url]: https://github.com/AurelienClere-365/AutomationALM/issues
[license-shield]: https://img.shields.io/github/license/othneildrew/Best-README-Template.svg?style=for-the-badge
[license-url]: https://github.com/AurelienClere-365/AutomationALM/blob/main/LICENSE
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/aurelien-clere
