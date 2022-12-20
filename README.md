"# AzureFullstackCICD" 
Author : Suresh Nallakula
suresh.nallakula@in.ibm.com



For CI-CD Implementation, please ensure the below prerequisites are installed locally or create a Windows 10 Virtual machine and install the same on them.

Download Dotnet https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/sdk-6.0.300-windows-x64-installer

Download GIT https://github.com/git-for-windows/git/releases/download/v2.36.1.windows.1/Git-2.36.1-64-bit.exe

Download visual studio code https://code.visualstudio.com/download#

Create a Folder IN VM - C:\MyProject and Get into the newly created directory dotnet new sln -o HelloworldApp

cd HelloworldApp dotnet new mvc -n HelloWorldApp.Web

Add project to solution dotnet sln HelloworldApp.sln add HelloWorldApp.Web Execute project and any libraries used like Nuget packages will be brought to local cache dotnet restore

Build for release configuration dotnet build --no-restore --configuration release

Verify: Visit your Project folder and navigate to the below directory to find the DLL

MyProject\HelloworldApp\HelloWorldApp.Web\bin\Release\net6.0 (dll file) C:\MyProject\HelloworldApp\HelloWorldApp.Web\bin\Release\net6.0\HelloWorldApp.Web.dll Go to the folder where all CSS and Website files are present in your project folder

cd HelloWorldApp.Web

Dotnet C:\MyProject\HelloworldApp\HelloWorldApp.Web\bin\Release\net6.0\HelloWorldApp.Web.dll

Kindly note, the project is on local machine and needs to be published dotnet publish --no-build --configuration release

Output created in HelloWorldApp.Web -> \HelloworldApp\HelloWorldApp.Web\bin\release\net6.0\publish\

Ensure you are in your Project HelloworldApp Folder HelloworldApp>git init

The above (Creates Hidden Folder), from the Windows Explore enable hidden files HelloworldApp>git add .

Add to gitconfig the user and email id git config --global user.email "xxx@mail.com" git config --global user.name "Suresh Nallakula"

Time to Commit the code HelloworldApp>git commit -m "Initial Status"

Navigate to Azure DevOps In the Project in DevOps, under Repo - Copy the Text under "Push an existing repository from command line"

Example: Assuming the project name was MyPro (COPY YOUR OWN CODE) git remote add origin https://user@dev.azure.com/user/ibmcicd/_git/ibmcicd

git push -u origin –-all

The DevOps may ask for username and password, navigate to files and your project is moved from local to Azure Repos.
