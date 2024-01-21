[<center><img src="https://raw.githubusercontent.com/sourajitk/STX-Logo/main/stx-2023.png" height="50%" width="50%;" /></center>](https://github.com/StatiXOS)

## Building Statix Special Edition ##
Your one-stop destination for all the documentation about building Android can be found [here](https://source.android.com/setup/build/building).

## Repo Init ##
```bash
repo init --depth=1 --no-repo-verify -u https://github.com/yehonatan2020/statix_android_manifest.git -b udc-qpr1 --git-lfs
```
## Sync Source ##
```bash
repo --no-pager --color=always sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags --optimized-fetch --prune
```
## Build A GSI that can be loaded with DSU ##
```bash
source build/envsetup.sh
lunch statix_arm64-userdebug (or statix_arm64-user)
m gsi -j$(nproc --all)
```
## Build A complete ROM (Fastboot) ##
```bash
source build/envsetup.sh
lunch statix_<device>-userdebug (or statix_<device>-user)
m updatepackage -j$(nproc --all)
```
## Build A complete ROM (Sideload) ##
```bash
source build/envsetup.sh
lunch statix_<device>-userdebug (or statix_<device>-user)
m bacon -j$(nproc --all)
```

### Submitting Patches ###

Patches are welcomed here at StatiXOS.

To start contributing, register at https://review.statixos.com and follow the steps below:

First, we need to create an SSH key that is required to push patch sets to Gerrit. Type the following command into the terminal:

```bash
ssh-keygen
```

Head to our Gerrit and click on your avatar in the top right corner. Then click "Settings."

In settings, click on "SSH Keys" on the left-hand side of the screen.

Now on your computer, type in cat ~/.ssh/id_rsa.pub, copy the output and paste the copied contents in the box that says "New SSH key" and press on the "Add New SSH Key" button.

Make your changes and commit with a detailed message. The commit message should start with the name of the current project to help us during the review process.

We are almost there! Now to push your patch set to Gerrit, type in the following in your terminal:

```bash
    git push ssh://<username>@review.statixos.com:29419/<project> HEAD:refs/for/<branch>
```

* `<username>` - Your Gerrit username (which can be seen/set [here](https://review.statixos.com/#/settings/))
* `<project>` - The git repo you are pushing to; all options can be viewed at [this link](https://review.statixos.com/#/admin/projects/)
* `<branch>` - The git branch your change is based on; for projects using this manifest, it is `udc-qpr1`

[View Code Review](https://review.statixos.com/)

[XDA Thread Template](https://downloads.statixos.com/template/template.txt)
