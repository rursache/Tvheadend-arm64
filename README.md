# Tvheadend-arm64
The easy way to compile Tvheadend on Raspberry Pi (arm64)

> **Note**
>
> I **strongly** recommend you to use [this docker image](https://hub.docker.com/r/linuxserver/tvheadend) instead of trying to compile this yourself. The below instructions should work but they are not tested anymore and no new releases will be provided

## Requirements
- 2GB+ Raspberry Pi (add swap space if needed)
- 1.5GB+ free space

## How to
```
cd ~/Downloads
git clone https://github.com/tvheadend/tvheadend &&
cd tvheadend &&
sudo apt update && sudo apt upgrade -y &&
sudo apt install ffmpeg ccache debhelper gettext libavahi-client-dev liburiparser-dev cmake libpcre2-dev libpcre3-dev libdvbcsa-dev -y &&
AUTOBUILD_CONFIGURE_EXTRA="--enable-ccache --build=arm64" ./Autobuild.sh -t raspbianbuster-armhf
```
The result .deb file will be in `~/Downloads`

**NOTES**:
- If you don't want **ffmpeg**, replace `--build=arm64` with `--disable-ffmpeg_static` in `AUTOBUILD_CONFIGURE_EXTRA`
- If you don't want **ccache**, remove `--enable-ccache` from `AUTOBUILD_CONFIGURE_EXTRA`

## Installing
Run sudo `dpkg -i <FILE>.deb` and follow the install script.

After the installation is done, you can access tvheadend in your browser on <PI-IP>:9981 and the user/pass you set during the install

## Releases
The releases section contains already build .deb files with updated versions of tvheadend
