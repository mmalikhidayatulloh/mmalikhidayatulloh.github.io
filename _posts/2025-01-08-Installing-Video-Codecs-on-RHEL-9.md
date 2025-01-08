```
sudo subscription-manager repos --enable codeready-builder-for-rhel-9-x86_64-rpms
sudo dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-9.noarch.rpm
sudo dnf install https://download1.rpmfusion.org/free/el/rpmfusion-free-release-9.noarch.rpm
sudo dnf install https://download1.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-9.noarch.rpm
sudo dnf upgrade
sudo dnf install ffmpeg
sudo dnf install gstreamer1-libav
```
