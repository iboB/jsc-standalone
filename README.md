# JSC Standalone

Binaries for using JavaScriptCore in your own project.

## Features

* Header files
* 32-bit binaries for Windows. 
	* 64-bit is not planned. Apple don't offer instructions or Support libraries for 64-bit builds. It definitely seems possible, but I don't have the time to pursue this.

## Rationale

Building JSC from source takes a lot of time and setup. This repo contains binaries so you don't have to do it.

If you do want to do it:

* The instructions for Windows are [here](https://webkit.org/webkit-on-windows/)

With a little help and good will from Apple, this repository will soon become obsolete (or replaced by something similar to [CEF-CMake](https://github.com/iboB/cef-cmake), which downloads what's needed in a configure step). In fact Apple [are almost there](https://build.webkit.org/). The problem is they only package the bin directory from the build and there are no libs and headers in the package.

## Usage

There's an optional `CMakeLists.txt` file enclosed with some basic functionality. It creates the `javascriptcore` interface library with include paths and library files.

Additionally some more setup steps are needed

### Windows

If you have Safari or iTunes installed you already have the Apple Application Support (AAS) DLLs needed. They should be in `Program Files (x86)\Common Files\Apple\Apple Application Support`. If not, `HKLM\SOFTWARE\Apple Inc.\Apple Application Support` will show you where they are.

If you dot not have the AAS DLLs, you can either install Safari or iTunes, or, if you don't want to do it, follow these steps:
* Download an [installation for iTunes](https://www.apple.com/itunes/download/win64)
* Extract the installation executable with some archiving software (7zip, or WinRAR, or other).
* You will get a bunch of .msi files
* Install `AppleApplicationSupport.msi` (if you want 64 bit AAS, also install `AppleApplicationSupport64.msi`)

Now, when you have the AAS DLLs, you need make them visible to your applications which use JSC. You can either add them to your path, copy them to you binary directory, or use other means of loading them.

## License and Copyright

* WebKit (including JavaScriptCore) is under [GNU LGLPL v2.1](https://www.gnu.org/licenses/old-licenses/lgpl-2.1.en.html). These binaries were compiled using the source from [this revision](https://github.com/WebKit/webkit/tree/e9dc079846e3070904223e8ab1a5b3f906aedbc3) of the WebKit's GitHub mirror.
* I release the `CMakeLists.txt` file in the public domain.
