# import the key
```
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
```
# Add the repo
```
sudo dnf config-manager --add-repo https://packages.microsoft.com/yumrepos/edge
```
# Refresh meta cache
```
sudo dnf update --refresh
```
# Install Software
```
sudo dnf install microsoft-edge-stable
```
