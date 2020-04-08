## [1.1.2](https://github.com/adrenak/usfb/compare/v1.1.1...v1.1.2) (2020-04-08)


### Bug Fixes

* Get Runtime and Runtime Common asmdefs to run on any supported ([3f0cd4b](https://github.com/adrenak/usfb/commit/3f0cd4bc23033aa3a3f8cc4844643adaa213d02c))

## [1.1.1](https://github.com/adrenak/usfb/compare/v1.1.0...v1.1.1) (2020-04-08)


### Bug Fixes

* Reorganise source for platform dependent compilation. Experimental... ([6c0df62](https://github.com/adrenak/usfb/commit/6c0df62a73985a532d4dabefeaa9e94c671ab0d7))

# [1.1.0](https://github.com/adrenak/usfb/compare/v1.0.0...v1.1.0) (2020-04-08)


### Features

* Change name from sfb to usfb ([04669e1](https://github.com/adrenak/usfb/commit/04669e1663ea86e1103ecb07ebbafc3ec7ea5445))

# 1.0.0 (2020-04-08)


### Features

* Modify for UPM ([4964bd9](https://github.com/adrenak/UnityStandaloneFileBrowser/commit/4964bd9ce93fe6b8938a2d30d7bec5da9d896a32))

# Unity Standalone File Browser

A simple wrapper for native file dialogs on Windows/Mac/Linux.

- Works in editor and runtime.
- Open file/folder, save file dialogs supported.
- Multiple file selection.
- File extension filter.
- Mono/IL2CPP backends supported.
- Linux support by [Ricardo Rodrigues](https://github.com/RicardoEPRodrigues).
- Basic WebGL support.

[Download Package](https://github.com/gkngkc/UnityStandaloneFileBrowser/releases/download/1.2/StandaloneFileBrowser.unitypackage)

Example usage:

```csharp
// Open file
var paths = StandaloneFileBrowser.OpenFilePanel("Open File", "", "", false);

// Open file async
StandaloneFileBrowser.OpenFilePanelAsync("Open File", "", "", false, (string[] paths) => {  });

// Open file with filter
var extensions = new [] {
    new ExtensionFilter("Image Files", "png", "jpg", "jpeg" ),
    new ExtensionFilter("Sound Files", "mp3", "wav" ),
    new ExtensionFilter("All Files", "*" ),
};
var paths = StandaloneFileBrowser.OpenFilePanel("Open File", "", extensions, true);

// Save file
var path = StandaloneFileBrowser.SaveFilePanel("Save File", "", "", "");

// Save file async
StandaloneFileBrowser.SaveFilePanelAsync("Save File", "", "", "", (string path) => {  });

// Save file with filter
var extensionList = new [] {
    new ExtensionFilter("Binary", "bin"),
    new ExtensionFilter("Text", "txt"),
};
var path = StandaloneFileBrowser.SaveFilePanel("Save File", "", "MySaveFile", extensionList);
```
See Sample/BasicSampleScene.unity for more detailed examples.

Mac Screenshot
![Alt text](/Images/sfb_mac.jpg?raw=true "Mac")

Windows Screenshot
![Alt text](/Images/sfb_win.jpg?raw=true "Win")

Linux Screenshot
![Alt text](/Images/sfb_linux.jpg?raw=true "Win")

Notes:
- Windows
    * Requires .NET 2.0 api compatibility level 
    * Async dialog opening not implemented, ..Async methods simply calls regular sync methods.
    * Plugin import settings should be like this;
    
    ![Alt text](/Images/win_import_1.jpg?raw=true "Plugin Import Ookii") ![Alt text](/Images/win_import_2.jpg?raw=true "Plugin Import System.Forms")
    
- Mac
    * Sync calls are throws an exception at development build after native panel loses and gains focus. Use async calls to avoid this.

WebGL:
 - Basic upload/download file support.
 - File filter support.
 - Not well tested, probably not much reliable.
 - Since browsers require more work to do file operations, webgl isn't directly implemented to Open/Save calls. You can check CanvasSampleScene.unity and canvas sample scripts for example usages.
 
 Live Demo: https://gkngkc.github.io/
