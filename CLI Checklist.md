# AEON CLI BETA TESTING                 

## PULL REQUEST and RELEASE TESTING GUIDELINES
The purpose of Pull Request (PR) testing is to find, if any, pre-merge issues with a build from upstream patches or new patches to Aeon core code. Sometimes, new issues are created by merging upstream or new code.  We do this testing because we want to find if there are specific Operating System (OS) issues or if there are general issues with the build process or function of the soon to be integrated code. Beta testing helps streamline the PR merge process so that updates and changes can be done in a timely manner. Testing of candidates must be done after creating your build testing environment using the guidelines found on the Aeonix CLI Readme.md located here. Note that dependencies do change over time and please verify your build environment reflects the latest changes. Below are the steps that are requested with results for individual building and testing:

## 1.	PULL REQUEST BUILDING:

```
1.	Create a new folder and pull the latest PR from the Aeonix GitHub repo:
i.	“ git clone --recursive https://github.com/aeonix/aeon ”
2.	Move to the Aeon folder and fetch the PR you are testing:
i.	“ cd aeon && git fetch origin pull/93/head:PR-93 ”
3.	Checkout the PR you are testing:
i.	“ git checkout PR-93 ”
4.	Update the modules for that PR:
i.	“ git submodule init && git submodule update ”
5.	Build the PR candidate
i.	“ make release-static ” 
```


## 2.	RELEASE CANDIDATE BUILDING:

```
1.	Create a new folder and pull the latest PR from the Aeonix GitHub repo:
i.	“ git clone --recursive https://github.com/aeonix/aeon ”
2.	Move to the Aeon folder update the modules:
i.	“ cd aeon && git submodule init && git submodule update ”
3.	Build the release candidate:
i.	“ make release-static ”
```

If the CLI builds properly, you should be left with the following binaries in your build folder as noted on the command prompt after successful completion:

* Aeon-blockchain-blackball

*	Aeon-blockchain-export

*	Aeon-blockchain-import

*	Aeon-blockchain-usage

*	Aeon-wallet-cli

*	Aeon-wallet-rpc

*	Aeond

If your build was not successful, please search on the Aeon GitHub bug list to see if there are any similar build errors. If you do not find them, search the Monero GitHub bug list to see if there are any issues related to yours. Chances are that someone else has had the same issue in the past, especially with PR builds. If you do not find this bug anywhere, try building the latest Monero release and see if you have the same issue. If you do have the same build errors, create a bug in the Monero GitHub. If you do NOT have the same error building on Monero, please consult the Aeon discord or Aeon IRC for assistance before creating an Aeon bug. Chances are someone else may have seen this issue on the same build process and OS as you. If needed, create a bug on the Aeon GitHub for your issue. 


If your build of the binaries was successful, we need to test them. Each candidate needs testing for all possible functions. Of course, not everyone can test every command and every little detail, so we suggest at least testing the following on your desired OS and report back the findings. 

```
After successful completion, please test the following:
1 – Do the executables open properly?
2 – Do the executables close properly with no errors.?
3 – Are the executables named properly with no spelling errors?
4 – Do the built binaries show the correct build version?
-	You can check the hash version at the header of the CLI daemon and Wallet cli and compare to the latest PR commit or Release commit.
5 – Daemon testing:
-	Run the daemon and sync blockchain from your latest blockchain file.
-	Run the daemon and sync from block 0.
-	Run the daemon and sync from a desired block height you enter.
-	Once synced check as many commands as you can with the CLI specifically “version” and “status”. See additional commands here.
-	After the daemon syncs, run the daemon for at least 24 hours and check status and block height for errors. Run the daemon for a long as possible to verify no longer term issues arise from the build. 
-	Close daemon with “exit” and verify daemon closes with no errors.
-	Report any issues on the PR or if a release version contact devs via IRC or Discord channel.
6 – Wallet CLI testing:
-	Open the CLI and create a new wallet. Make sure to save the seed and keys for regenerating  later. Make sure the wallet syncs with the daemon properly.
-	Open the CLI and open an already generated wallet file. Make sure it syncs with the daemon properly. 
-	Open the wallet and connect to a remote node and verify it syncs properly with no errors. 
-	Send and Receive a transaction on both local daemon and remote node and verify no issues.
-	Check as many CLI commands that you can find here. 
-	Report any issues found on the PR or to devs on the IRC channel or Discord
7 – Wallet RPC testing:
-	Open the RPC wallet and create a new wallet. Make sure the wallet syncs with the daemon properly.
-	Open the CLI and open an already generated wallet file. Make sure it syncs with the daemon properly. 
-	Open the wallet and connect to a remote node and verify it syncs properly with no errors. 
-	Check as many CLI commands that you can for RPC wallet found here.  
-	Report any issues found on the PR or to devs on the IRC channel or Discord
8 – Aeon Blockchain Import and Export:
-	After syncing with the daemon and saving the blockchain file, move the data.db file to another location you know on your computer and use the Import function to import that DB to your new daemon. Verify it properly imports and the daemon syncs like it should. 
-	Use the Export to move the DB to a zip file and verify that it does create this file.
-	Report any issues found on the PR or to devs on the IRC channel or Discord
```

When you have tested as much as you can, please report back findings for PR testing on the actual pull request on GitHub. If testing a release, feel free to comment on the announcement thread. If you have any issues at all with the testing of build or functional process, please contact the dev team on IRC first then any other available resource. Dev team members are most active on IRC. If unable to contact on IRC, use other media platforms to contact the community and dev team. Report listings with the following information so that we can determine if a Release or PR is good to go:

```
-	VM build or Standard OS build type
-	Operating system you used to build and test 
-	Any specific build variables you used
-	Processor type , core count used, and RAM used
-	Any issues you encountered on the build process
-	Any issues you encountered on the testing process
-	Any comments for stability or enhancements for the build
-	Any additional comments from build/testing 

```
