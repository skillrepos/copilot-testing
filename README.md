# Automated Testing with GitHub Copilot - lab setup

These instructions will guide you through configuring a GitHub Codespaces environment that you can use to run the course labs. 
If you prefer and if you know one of the other IDEs supported by Copilot, you can use that. But the instructions will reference the codespace version.

These steps **must** be completed prior to starting the actual labs.

## Step 1. Copilot access. 

GitHub has recently made a free version of Copilot available for limited use each month. You can use that version to do the labs in this course. If you prefer, you can signup for their paid individual planby following the details below, but this is optional for this training.

**If you want to signup for a paid Copilot option...**

When signed into GitHub, click on your profile picture/icon in the upper right and either select [Copilot](https://github.com/github-copilot/signup) 

![Signing up for Copilot](./images/ct01.png?raw=true "Signing up for Copilot")

**OR** select [Settings->Copilot](https://github.com/settings/copilot) and sign up.

![Signing up for Copilot](./images/ct02.png?raw=true "Signing up for Copilot")

You can also find help there for using Copilot in other supported IDEs, set the switch for whether or not to allow matching public code suggestions, etc.

![Using Copilot options](./images/ct03.png?raw=true "Using Copilot options")
<br/><br/>

## Step 2. To create your working environment for the labs, create a codespace by clicking on the button below:

Click on this button ⬇️
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/skillrepos/copilot-testing?quickstart=1)

<br/><br/>
Then click on the option to create a new codespace.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![Creating new codespace from button](./images/ct11.png?raw=true "Creating new codespace from button")

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**This will run for several minutes while it gets everything ready.**
  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- After the codespace has initialized there will be a terminal present.

<br/><br/>

## Step 3. Open the labs

After the codespace has started, open the labs document by going to the file tree on the left, find the file named **labs.md**, right-click on it, and open it with the **Preview** option.)

![Labs doc preview in codespace](./images/ct12.png?raw=true "Labs doc preview in codespace")

This will open it up in a tab above your terminal. Then you can follow along with the steps in the labs. 
Any command in the gray boxes is either code intended to be run in the console or code to be updated in a file.

Labs doc: [Copilot Testing Labs](labs.md)

## Step 4. Set codespace timeout (optional but recommended)

While logged in to GitHub, go to https://github.com/settings/codespaces.

Scroll down and find the section on the page labeled *Default idle timeout*. 

Increase the default timeout value to 90 minutes and then select the *Save* button.

![Increasing default timeout](./images/k8sdev33.png?raw=true "Increasing default timeout")

(**NOTE**: If your codespace does time out at some point in the course, there should be a button to restart it. In that case, you will need to run the *minikube start* command again.)
