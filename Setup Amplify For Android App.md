first of all move to the root  directory of you project:
```powershell
ps c:\users\gk\desktop\foodly-master\foodly-master> amplify init
```
give a name for the project :
```powershell
? enter a name for the project foodlymaster
```
by default amolify will detect you project and give you the configuration necessary but in our case this for an android app so we will need to reject the default config because it's related to vscode and web projects:
```powershell
project information
| name: foodlymaster
| environment: dev
| default editor: visual studio code
| app type: javascript
| javascript framework: none
| source directory path: src
| distribution directory path: dist
| build command: npm.cmd run-script build
| start command: npm.cmd run-script start

? initialize the project with the above configuration? (y/n) n 
```
choose a name for the environment and choose android studio
``` powershell
? enter a name for the environment dev
? choose your default editor:
  visual studio code
 >android studio
  xcode (macos only)
  atom editor
  sublime text
  intellij idea
  vim (via terminal, macos only)
```
for sure choose android
```powershell
(move up and down to reveal more choices)
? enter a name for the environment dev
? choose your default editor: android studio
? choose the type of app that you're building ...  (use arrow keys or type to filter)
❯ android
  flutter
  ios
  javascript
```
if the location is the same app/src/main/res just hit enter
```powershell
please tell us about your project
? where is your res directory:  (app/src/main/res)
```
okay it's almost done just choose a way to authenticate:
```powershell
? select the authentication method you want to use: (use arrow keys)
> aws profile
  aws access keys
```
 So if everything okay you'll see this message
 ```powershell
deployment state saved successfully.
√ Initialized provider successfully.
✅ Initialized your environment successfully.
✅ Your project has been successfully initialized and connected to the cloud!
```
Great !!!
this is an example for adding auth on this example a just add google in your case you can add more than me;
>**Note:!!!!!!!!!!!!!!!!**
>>F**or the signin uri use:** `foodly://callback/`
>>**For the sighiut uri use:** `foodly://signout/`

```powershell

PS C:\Users\GK\Desktop\Foodly-master\Foodly-master> amplify add auth
Using service: Cognito, provided by: awscloudformation

 The current configured provider is Amazon Cognito.

 Do you want to use the default authentication and security configuration? Default configuration with Social Provider (Federation)
 Warning: you will not be able to edit these selections.
 How do you want users to be able to sign in? Username
 Do you want to configure advanced settings? No, I am done.
 What domain name prefix do you want to use? foodlymaster13f777f5-13f777f5
 Enter your redirect signin URI: foodly://callback/
? Do you want to add another redirect signin URI No
 Enter your redirect signout URI: foodly://signout/
? Do you want to add another redirect signout URI No
 Select the social providers you want to configure for your user pool: Google

 You've opted to allow users to authenticate via Google.  If you haven't already, you'll need to go to https://developers.google.com/identity and create an App ID.

 Enter your Google Web Client ID for your OAuth flow:  863194034923-gc12jp7n8tm6123hh0sklqfja4lf4ip2.apps.googleusercontent.com
 Enter your Google Web Client Secret for your OAuth flow:  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
✅ Successfully added auth resource foodlymaster13f777f5 locally
```
in my case with google you need to add the cognito domain to the allowed:
- Go to the [Google developer console](https://console.developers.google.com).
- On the left navigation bar, look for _APIs and Services_ under _Pinned_ or under _More Products_ if not pinned.
- Within the _APIs and Services_ sub menu, choose _Credentials_.
- Select the client you created in the first step and click the _Edit_ button.
- Type your user pool domain into the _Authorized Javascript origins_ form.
- Type your user pool domain with the `/oauth2/idpresponse` endpoint into _Authorized Redirect URIs_.
  ![[Pasted image 20240229131917.png]]
Do the same for the other providers and that's all wath you need to do, for the app code you don't need to change anything