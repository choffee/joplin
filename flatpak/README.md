Building for flatpak

This should build up the package for a flatpak

You first need to build the package list, which has all the node deps in.
I used the local lock file to create this using the flatpack-builder-tools npm
installer.
https://github.com/flatpak/flatpak-builder-tools/tree/master/npm

   python3 flatpak-npm-generator.py ../ElectronClient/app/package-lock.json

Then Build the package with the following. Now set the node version in the
net.cozic.joplin.json file to be the same as the one in the package-lock file.
You may also have to delete any entries that start with "data:" in the package
locks as that seems to break things.

   flatpak-builder build net.cozic.joplin.json

That should give you a flatpak.

Not sure what happens next but would be nice to get this on flathub
