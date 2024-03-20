PS C:\Users\GK\Desktop\Foodly-master\Foodly-master> amplify init
Note: It is recommended to run this command from the root of your app directory
? Enter a name for the project Foodlymaster
The following configuration will be applied:

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

? Initialize the project with the above configuration? (Y/n) 
PS C:\Users\GK\Desktop\Foodly-master\Foodly-master> ls


    Directory: C:\Users\GK\Desktop\Foodly-master\Foodly-master


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----         2/16/2024   8:27 PM                .gradle
d-----         2/16/2024   8:08 PM                .idea
d-----         2/16/2024   7:37 PM                app
PS C:\Users\GK\Desktop\Foodly-master\Foodly-master> ls


    Directory: C:\Users\GK\Desktop\Foodly-master\Foodly-master


Mode                 LastWriteTime         Length Name                                                                                                                               
----                 -------------         ------ ----                                                                                                                               
d-----         2/16/2024   8:27 PM                .gradle                                                                                                                            
d-----         2/16/2024   8:08 PM                .idea                                                                                                                              
d-----         2/16/2024   7:37 PM                app                                                                                                                                
PS C:\Users\GK\Desktop\Foodly-master\Foodly-master> amplify init
Note: It is recommended to run this command from the root of your app directory
? Enter a name for the project Foodlymaster
The following configuration will be applied:

Project information
PS C:\Users\GK\Desktop\Foodly-master\Foodly-master\app> amplify init
Note: It is recommended to run this command from the root of your app directory
? Enter a name for the project foodlyand
The following configuration will be applied:

Project information
PS C:\Users\GK\Desktop\Foodly-master\Foodly-master> amplify init
Note: It is recommended to run this command from the root of your app directory
? Enter a name for the project Foodlymaster
The following configuration will be applied:

Project information
| Name: Foodlymaster
| Environment: dev

For more information on AWS Profiles, see:
https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-profiles.html

? Please choose the profile you want to use default
Adding backend environment dev to AWS Amplify app: d26wa1gjpkavn

Deployment completed.
Deployed root stack Foodlymaster [ ======================================== ] 4/4
        UnauthRole                     AWS::IAM::Role                 CREATE_COMPLETE                Fri Feb 16 2024 20:32:06…
        AuthRole                       AWS::IAM::Role                 CREATE_COMPLETE                Fri Feb 16 2024 20:32:06…
        DeploymentBucket               AWS::S3::Bucket                CREATE_COMPLETE                Fri Feb 16 2024 20:32:19…
        amplify-foodlymaster-dev-2031… AWS::CloudFormation::Stack     CREATE_COMPLETE                Fri Feb 16 2024 20:32:22…

√ Help improve Amplify CLI by sharing non-sensitive project configurations on failures (y/N) · no

    You can always opt-in by running "amplify configure --share-project-config-on"
Deployment state saved successfully.
√ Initialized provider successfully.
✅ Initialized your environment successfully.
✅ Your project has been successfully initialized and connected to the cloud!
Some next steps:

"amplify status" will show you what you've added already and if it's locally configured or deployed
"amplify add <category>" will allow you to add features like user login or a backend API
"amplify push" will build all your local backend resources and provision it in the cloud
"amplify console" to open the Amplify Console and view your project status
"amplify publish" will build all your local backend and frontend resources (if you have hosting category added) and provision it in the cloud


Pro tip:
Try "amplify add api" to create a backend API and then "amplify push" to deploy everything

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

✅ Some next steps:
"amplify push" will build all your local backend resources and provision it in the cloud
"amplify publish" will build all your local backend and frontend resources (if you have hosting category added) and provision it in the cloud

PS C:\Users\GK\Desktop\Foodly-master\Foodly-master> amplify push
√ Successfully pulled backend environment dev from the cloud.

    Current Environment: dev

┌──────────┬──────────────────────┬───────────┬───────────────────┐
│ Category │ Resource name        │ Operation │ Provider plugin   │
├──────────┼──────────────────────┼───────────┼───────────────────┤
│ Auth     │ foodlymaster13f777f5 │ Create    │ awscloudformation │
└──────────┴──────────────────────┴───────────┴───────────────────┘
√ Are you sure you want to continue? (Y/n) · yes

Deployment completed.
Deploying root stack Foodlymaster [ ====================-------------------- ] 1/2
        amplify-foodlymaster-dev-2031… AWS::CloudFormation::Stack     UPDATE_IN_PROGRESS             Fri Feb 16 2024 20:36:42…
        authfoodlymaster13f777f5       AWS::CloudFormation::Stack     CREATE_COMPLETE                Fri Feb 16 2024 20:38:40…
Deployed auth foodlymaster13f777f5 [ ======================================== ] 14/14
        UserPoolClientRole             AWS::IAM::Role                 CREATE_COMPLETE                Fri Feb 16 2024 20:37:11…
        UserPool                       AWS::Cognito::UserPool         CREATE_COMPLETE                Fri Feb 16 2024 20:36:54…
        HostedUICustomResource         AWS::Lambda::Function          CREATE_COMPLETE                Fri Feb 16 2024 20:37:22…
        HostedUIProvidersCustomResour… AWS::Lambda::Function          CREATE_COMPLETE                Fri Feb 16 2024 20:37:22…
        HostedUICustomResourcePolicy   AWS::IAM::Policy               CREATE_COMPLETE                Fri Feb 16 2024 20:37:43…
        HostedUIProvidersCustomResour… AWS::IAM::Policy               CREATE_COMPLETE                Fri Feb 16 2024 20:37:44…
        HostedUICustomResourceLogPoli… AWS::IAM::Policy               CREATE_COMPLETE                Fri Feb 16 2024 20:38:03…
        HostedUIProvidersCustomResour… AWS::IAM::Policy               CREATE_COMPLETE                Fri Feb 16 2024 20:38:04…
        HostedUICustomResourceInputs   Custom::LambdaCallout          CREATE_COMPLETE                Fri Feb 16 2024 20:38:11…
        HostedUIProvidersCustomResour… Custom::LambdaCallout          CREATE_COMPLETE                Fri Feb 16 2024 20:38:11…
        UserPoolClientWeb              AWS::Cognito::UserPoolClient   CREATE_COMPLETE                Fri Feb 16 2024 20:38:16…
        UserPoolClient                 AWS::Cognito::UserPoolClient   CREATE_COMPLETE                Fri Feb 16 2024 20:38:16…
        IdentityPool                   AWS::Cognito::IdentityPool     CREATE_COMPLETE                Fri Feb 16 2024 20:38:21…
        IdentityPoolRoleMap            AWS::Cognito::IdentityPoolRol… CREATE_IN_PROGRESS             Fri Feb 16 2024 20:38:24…

Deployment state saved successfully.

Hosted UI Endpoint: https://foodlymaster13f777f5-13f777f5-dev.auth.us-east-1.amazoncognito.com/
Test Your Hosted UI Endpoint: https://foodlymaster13f777f5-13f777f5-dev.auth.us-east-1.amazoncognito.com/login?response_type=code&client_id=1derv3ani6kecftbaqclms7s1b&redirect_uri=foodly://callback/


PS C:\Users\GK\Desktop\Foodly-master\Foodly-master> 