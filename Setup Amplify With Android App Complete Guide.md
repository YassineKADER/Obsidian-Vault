First of all move to the root  directory of you project:
```powershell
PS C:\Users\GK\Desktop\Foodly-master\Foodly-master> amplify init
```
Give a name for the project :
```powershell
? Enter a name for the project Foodlymaster
```
By Default amolify will detect you project and give you the configuration necessary but in our case this for an android app so we will need to reject the default config because it's related to vscode and web projects:
```powershell
Project information
| Name: Foodlymaster
| Environment: dev
| Default editor: Visual Studio Code
| App type: javascript
| Javascript framework: none
| Source Directory Path: src
| Distribution Directory Path: dist
| Build Command: npm.cmd run-script build
| Start Command: npm.cmd run-script start

? Initialize the project with the above configuration? (Y/n) n 
```
