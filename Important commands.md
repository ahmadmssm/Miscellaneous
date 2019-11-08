## Android :
- Export SHA1 key :
```keytool -list -v -keystore ~/.android/debug.keystore -alias androiddebugkey -storepass android -keypass android ```

	For Release mode :
	``keytool -list -v -keystore {keystore_name} -alias {alias_name}``

Ref: https://stackoverflow.com/questions/15727912/sha-1-fingerprint-of-keystore-certificate

- List all available tasks for your project in Gradle:
	``gradle tasks``

- Verify that your APK is signed:
``apksigner verify my-app-release.apk``

- Run the first Android emulator available:
``
~/Library/Android/sdk/tools/emulator -avd `~/Library/Android/sdk/tools/emulator -list-avds | awk '{print $1}'`
``
- Kill adb: `adb kill-server`.
- Start adb: `adb start-server`.


## iOS :

### Cocoapods:
- Get information on a pod:
`pod trunk info [pod]`

- Verify your local account:
`pod trunk me`

- Deleting the pod:
`pod trunk delete NAME VERSION`

- Push/Update pod to remote repo:
`pod trunk push PODSPEC`

## Git:

- Push with detach HEAD mode:
`git push origin HEAD:remote-branch-name`
- Delete all remote tags:
`git tag -l | xargs -n 1 git push --delete origin`
- Delete all local tags:
`git tag | xargs git tag -d`




To rebase all commits made since branching out from master you might use the following command:

git rebase -i `git merge-base HEAD master`

https://stackoverflow.com/questions/43978823/how-to-squash-commits-in-one-branch

================================================================
Base64 Encoding/Decoding:

- Convert file to base64 string: 
`cat myfile.txt | base64`
- Convert base64 string into a file:
`echo $MYFILE | base64 -D > /any/path/myfile.txt`
`echo "Base64String" | base64 -D > downloads/myFile.txt`

    gem uninstall fastlane
gem install fastlane -v 2.110.0


## Docker:
- List all containers:
`docker ps -a`

- Delete container:
`docker rm e5d container_name`



