# React Native Expo Fastlane Actions
Template for creating react native projects using expo that can make use of CI/CD automation tools

## Getting Started
For more precise directions see the doc links (most directions here are for mac)
1. Install Node [nvm](https://github.com/nvm-sh/nvm)
2. Install Expo CLI
    > npm install -g expo-cli
3. Install Fastlane [docs](https://docs.fastlane.tools/getting-started/ios/setup/)
    > brew install fastlane  
4. Add the following to your .bashrc or .zshrc
    > export LC_ALL=en_US.UTF-8  
    > export LANG=en_US.UTF-8
5. Install Turtle CLI [docs](https://docs.expo.dev/distribution/turtle-cli/?redirected)
    > npm install -g turtle-cli

## Customize template to new App
1. Create Github Repo for Match [What is Match?](#match)
2. Create Apple Store App (must have an Apple organization created)
3. Use [.sample.env](./.sample.env) as template for required `.env` file in project  
    a. [MATCH_GIT_BASIC_AUTHORIZATION](https://docs.fastlane.tools/actions/match/) under `Git Storage on GitHub`.  
    b. `MATCH_PASSWORD` is the password you will generate to protect the iOS private. Save this to a password manager and add to the `.env`
4. Replace Matchfile values [fastlane/Matchfile](./fastlane/Matchfile)  
    a. git_url  
    b. app_identifier  
    c. username
5. Replace Appfile values [fastlane/Appfile](./fastlane/Appfile)  
    a. app_identifier
    b. apple_id
    c. itc_team_id
    d. team_id

5. Running and testing iOS commands
    1. Test app store certificate for your provided Matchfile credentials
        > fastlane ios certificates  
    2. Replace values in [fastlane/Fastfile](./fastlane/Appfile) from cert results
        a. cert_id
        b. provision_profile_file_name
    3. Test app store build command for generated certificates
        > fastlane ios build  
        
        *Note: you may have to run `expo build` once first because Turtle CLI won't setup some default settings that are required*
    
## Project was created by using the following steps
1. Create Expo project
    > expo init && cd react-native-expo-template
2. Initialize Fastlane.
    - Fastlane's `init` command does not support expo, so use the provided fastlane folder in the expo project as a template. Includes the Matchfile
3. Customized fastlane configuration to work with React Native through Expo and Turtle CI

### Match
Match is used by Fastlane to help store certificates for signing android and ios builds