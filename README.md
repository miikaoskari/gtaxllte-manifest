# Manifest for building LineageOS 20 for gtaxllte

`gtaxllte` is the codename for the LTE variant of the Samsung Galaxy Tab A 10.1" (2016), with model SM-T585, and also with SM-T585N0 and SM-T585C for Korea and China respectively.

Some extremely basic instructions:
- Make a new directory for LineageOS sources and enter it:
```
mkdir lineage-20
cd lineage-20
```

- Initialize repo in this directory with the LineageOS 20 android repository:
```
repo init -u https://github.com/LineageOS/android.git -b lineage-20 --git-lfs
```

- Clone this repository to .repo/local_manifests for roomservice.xml containing the repositories needed to build for these devices:
```
git clone https://github.com/K9100ii/gtaxl-manifests.git -b lineage-20 .repo/local_manifests
```

- Sync all of the repositories in manifests (including LineageOS manifests):
```
repo sync --force-sync --no-tags --no-clone-bundle -c
```

- Finally, build as you like. For example, for a recovery-installable package for gtaxlwifi:
```
. build/envsetup.sh
lunch lineage_gtaxlwifi-userdebug
mka otapackage
```
