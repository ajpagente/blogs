# Mercurial
## Large file error
When cloning a repo you may encounter this error
```
abort: remote error:

This repository uses the largefiles extension.

Please enable it in your Mercurial config file.
```
### Fix
To fix this, enable the largefiles extension by adding following lines in your Mercurial config file:
```
[extensions]
largefiles =
```
Now how do you find the config file?
Type the command:
```
hg config --debug
```
On Windows, the output will look like this:
```
starting pager for command 'config'
read config from: C:\Program Files\TortoiseHg\mercurial.ini
read config from: C:\Program Files\TortoiseHg\hgrc.d\EditorTools.rc
read config from: C:\Program Files\TortoiseHg\hgrc.d\Mercurial.rc
read config from: C:\Program Files\TortoiseHg\hgrc.d\MergePatterns.rc
read config from: C:\Program Files\TortoiseHg\hgrc.d\MergeTools.rc
read config from: C:\Program Files\TortoiseHg\hgrc.d\Paths.rc
read config from: C:\Program Files\TortoiseHg\hgrc.d\TerminalTools.rc
read config from: C:\Users\username\mercurial.ini
read config from: C:\Users\username\.hgrc
...
```
Add the lines mentioned above to mercurial.ini 


