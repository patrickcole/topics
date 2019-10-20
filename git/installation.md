# Git - Installation

## mac os

### Using Git After Mac OS Update

If you are receiving the following error (or something similar):

`xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun`

You need to update your Xcode Command-Line Tools by running the following command in your terminal:

`xcode-select --install`

Follow the instructions in the new dialog that will pop up on the screen. This will update the command line tools which Git uses. It is recommended to **restart your terminal after the installation completes.**

[source](https://stackoverflow.com/a/52522566/6632985)
