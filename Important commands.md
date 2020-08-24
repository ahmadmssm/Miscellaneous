## Android :
- Export SHA1 key :
```
keytool -list -v -keystore ~/.android/debug.keystore -alias androiddebugkey -storepass android -keypass android
```

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
- Export adb (MAC):
```
export PATH=~/Library/Android/sdk/tools:$PATH
export PATH=~/Library/Android/sdk/platform-tools:$PATH
```


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

- Configure GPG Key:
  1. List agg GPG keys:
  ```
  gpg --list-secret-keys --keyid-format LONG
  ```
  2. List all GPG keys for an email:
  ```
  gpg --list-secret-keys --keyid-format LONG mail@gmail.com
  ```
  3. Export a GPG key:
  ```
  gpg --armor --export myKey
  ```
  4. Add a gpg key to git Repo.:
  ```
  git config user.signingkey myKey
  ```
  5. Add GPG key to an Email and Git name of a single Repo
  ```
  git config user.email "xyz@gmail.com"
  git config user.name "gitName"
  ```
  6. Sign All comits of a Repo:
  ```
  git config commit.gpgsign true
  ```
  7. Add GPG key to an Email and Git name to all Repos (Global configuration):
  ```
  git config --global user.email "xyz@gmail.com"
  git config --global user.name "gitName"
  ```

- Push with detach HEAD mode:
`git push origin HEAD:remote-branch-name`
- Delete all remote tags:
`git tag -l | xargs -n 1 git push --delete origin`
- Delete all local tags:
`git tag | xargs git tag -d`
- Create Empty branch :

    ```
    git checkout --orphan <branchname>
    // This will create a new branch with no parents. Then, you can clear the working directory with
    git rm --cached -r .
    // And then you just commit branch with empty commit and then push
    git commit -m <commit message> --allow-empty
    git push origin <newbranch>
    ```
Ref: https://stackoverflow.com/questions/13969050/how-to-create-a-new-empty-branch-for-a-new-project

- To rebase all commits made since branching out from master you might use the following command:

    ```
    git rebase -i
    git merge-base HEAD master
    ```

	Ref: https://stackoverflow.com/questions/43978823/how-to-squash-commits-in-one-branch


- How to get (only) author name or email for a given SHA1:
```
    // You can use the following command:
    git log --format='%ae' HASH^!
	// You need to include -s to suppress the diff.
    git show -s --format='%ae' HASH
```
   Ref: https://stackoverflow.com/questions/29876342/how-to-get-only-author-name-or-email-in-git-given-sha1
   

## Base64 Encoding/Decoding:

- Convert file to base64 string:
`cat myfile.txt | base64`
- Convert base64 string into a file:
`echo $MYFILE | base64 -D > /any/path/myfile.txt`
`echo "Base64String" | base64 -D > downloads/myFile.txt`

    gem uninstall fastlane
gem install fastlane -v 2.110.0

## Read me:

- Link to a section in the read me:
  ```
  // For the section:
  ## <a name="abcde">Heading One</a>
  // Link to the section:
  [link text](#abcde)
  ```
  Ref: https://stackoverflow.com/a/6494918/6927433


References:
1. https://www.makeareadme.com/
2. 

## Docker:
- List all containers:
`docker ps -a`

- Delete container:
`docker rm e5d container_name`




