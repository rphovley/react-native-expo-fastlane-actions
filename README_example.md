## Deployment Automation
Makes use of a tool called `fastlane` to automate building, testing, signing and deploying to beta and production channels.   
Used a template to help create this sample: [Example Repo](https://docs.google.com/document/d/1KKNUUf6x9zRm2rcmQG-7AFGIT6qazMpStBfN1-rfVxM/edit#)

### Fastlane Installation
> xcode-select --install  
> brew install fastlane 

**Steps**  
1. Copy `.env.sample` as `.env`. Used to provide sensitive data to the build process.  
    - MATCH_GIT_BASIC_AUTHORIZATION
        1. Get access to dev@qsciences.com github and create personal access token 
        2. `echo -n dev@qsciences.com:your_personal_access_token | base64` (reference `Git Storage on GitHub`)[https://docs.fastlane.tools/actions/match/]
        3. paste value in .env MATCH_GIT_BASIC_AUTHORIZATION
    - MATCH_PASSWORD
        1. Talk to dev ops to get access to this key to decrypt the certificates from the certificate repository
    - EXPO_USERNAME & EXPO_PASSWORD
        1. Obtain these from your expo login
2. Get App certificates
    > fastlane ios certificates
3. Build project
    > fastlane ios build
### Fastlane Notes / Sources
### **Fastlane Tools**: Match
Match is a way to simplify storing and pulling certificates. Makes use of a private github repo to do this. 
In the future, this would be better implemented using Google Cloud Storage and Hashicorp Vault.   

### **Fastlane Tools**: Turtle CLI
Turtle CLI is a build tool built by Expo to allow you to build expo projects on any device that would ordinarily be able to do react builds instead of having to rely on Expo's build servers. 

1. [Getting Started React-Native Fastlane docs](https://docs.fastlane.tools/getting-started/cross-platform/react-native/)
2. Fastfile built based off of [this link](https://carloscuesta.me/blog/shipping-react-native-apps-with-fastlane)
    1. [More react-native fastfile ideas](https://thecodingmachine.github.io/react-native-boilerplate/docs/BetaBuild/)
    2. [More](https://github.com/osamaqarem/reactnative-fastlane-appcenter)
3. CI used by Expo for build process [Turtle CI](https://docs.expo.dev/distribution/turtle-cli/)
4. [Setup Match](https://docs.fastlane.tools/actions/match/)
3. [Android signing directions](https://reactnative.dev/docs/signed-apk-android)
4. [Ideas for Automation](https://carloscuesta.me/blog/shipping-react-native-fastlane-travis)

