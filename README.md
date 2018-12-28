# macOS-ISO
Steps to create a macOS ISO image from Install.app

## Purpose
Convert installer to ISO image for usage in VMware Fusion or Workstation

## Code (macOS 10.14 Mojave)

### Create disk image
    hdiutil create -o /tmp/macOS-10.14-Mojave -size 6000m -layout SPUD -fs HFS+J

### Mount disk image
    hdiutil attach /tmp/macOS-10.14-Mojave.dmg -noverify -mountpoint /Volumes/macOS-10.14-Mojave

### Run `createinstallMedia`
    sudo /Applications/Install\ macOS\ Mojave.app/Contents/Resources/createinstallmedia --volume /Volumes/macOS-10.14-Mojave

### Move image to desktop
    mv /tmp/macOS-10.14-Mojave.dmg ~/Desktop

### Convert image to ISO
    hdiutil convert ~/Desktop/macOS-10.14-Mojave.dmg -format UDTO -o ~/Desktop/macOS-10.14-Mojave.iso

### Rename image from `.iso.cdr` to `.iso`
mv ~/Desktop/macOS-10.14-Mojave.iso.cdr ~/Desktop/macOS-10.14-Mojave.iso
