## Running on Windows

On Windows, you'll need to install some additional dependencies:

1. [node-gyp](https://github.com/TooTallNate/node-gyp/) (`npm install -g node-gyp`)
2. [Python 2.7](http://www.python.org/download/releases/2.7.3#download) (not 3.3)
3. Visual Studio 2010 or higher (the free Express edition is fine)
  - Windows XP/Vista/7:
    - Microsoft Visual Studio C++ 2010 ([Express](http://go.microsoft.com/?linkid=9709949) version works well)
       - For VS 2010, also install [Microsoft Visual Studio 2010 Service Pack 1](http://www.microsoft.com/en-us/download/details.aspx?displaylang=en&id=23691)
       - For 64-bit builds of node and native modules you will _**also**_ need the [Windows 7 64-bit SDK](http://www.microsoft.com/en-us/download/details.aspx?id=8279)
       - If you get errors that the 64-bit compilers are not installed you may also need the [compiler update for the Windows SDK 7.1](http://www.microsoft.com/en-us/download/details.aspx?id=4422)
  - Windows 8:
       - Microsoft Visual Studio C++ 2012 for Windows Desktop ([Express](http://go.microsoft.com/?linkid=9816758) version works well)
3. [OpenSSL](http://slproweb.com/products/Win32OpenSSL.html) (normal, not light) in the same bitness as your Node.js installation.
  - The build script looks for OpenSSL in the default install directory  (`C:\OpenSSL-Win32` or `C:\OpenSSL-Win64`)
  - If you get `Error: The specified module could not be found.`, copy `libeay32.dll` from the OpenSSL bin directory to this module's bin directory, or to Windows\System32.