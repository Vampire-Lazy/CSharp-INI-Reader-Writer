# CSharp-INI-Reader-Writer
A Class to Read and Write configuration file in C#.

## How to use it
Open the INI file in one of the 3 following ways:

```
// Creates or loads an INI file in the same directory as your executable
// named EXE.ini (where EXE is the name of your executable)
var MyIni = new IniFile();

// Or specify a specific name in the current dir
var MyIni = new IniFile("Settings.ini");

// Or specify a specific name in a specific dir
var MyIni = new IniFile(@"C:\Settings.ini");
```

**You can write some values like so:**
```
MyIni.Write("DefaultVolume", "100");
MyIni.Write("HomePage", "http://www.google.com");
```
**To create a file like this:**
```
[MyProg]
DefaultVolume=100
HomePage=http://www.google.com
```

**To read the values out of the INI file:**
```
var DefaultVolume = MyIni.Read("DefaultVolume");
var HomePage = MyIni.Read("HomePage");
```

**Optionally, you can set [Section]'s:**
```
MyIni.Write("DefaultVolume", "100", "Audio");
MyIni.Write("HomePage", "http://www.google.com", "Web");
```
**To create a file like this:**
```
[Audio]
DefaultVolume=100

[Web]
HomePage=http://www.google.com
```
**You can also check for the existence of a key like so:**
```
if(!MyIni.KeyExists("DefaultVolume", "Audio"))
{
    MyIni.Write("DefaultVolume", "100", "Audio");
}
```

**You can delete a key like so:**
```
MyIni.DeleteKey("DefaultVolume", "Audio");
``
**You can also delete a whole section (including all keys) like so:**

`MyIni.DeleteSection("Web");`
