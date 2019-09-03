---
title: Configuration
---

In the `ignition` config file you can tweak the way the Ignition error page behaves and looks like.  

## Setting your editor

On a typical error screen paths to source file names are displayed. Next to the file name is a pencil icon. Clicking the pencil icon will open that file in your editor of choice. You can configure that editor in the `editor` key of the `ignition` config file. 

You can choose between `phpstorm`, `vscode`, `vscode-insiders`, `sublime`, and `atom`.

## Remote Development Server Support
To allow the edit URL to be created properly, you should specify the following variables in your `.env` file. Leave these empty if you are developing locally and are serving your site from the same filesystem you are editing on.

### IGNITION_REMOTE_SITES_PATH
Specify the full path (not URL) to your projects or sites folder on your remote dev server, be this Homestead, Docker, or in the cloud. For example:
```
IGNITION_REMOTE_SITES_PATH="/home/vagrant/Sites"
```

### IGNITION_LOCAL_SITES_PATH
Specify the full path (not URL) to your projects or sites folder as it resides on your local machine, the way your IDE or editor accesses the. For example:
```
IGNITION_LOCAL_SITES_PATH="/Users/me/Developer/Sites"
```

## Theme support

You can configure a theme in the `theme` key of the `ignition` config file. Out of the box there are two beautiful themes supported.

`light`

![Screenshot of light ignition theme](/images/docs/ignition-light.png)

`dark`

//TODO: add screenshot of dark theme
