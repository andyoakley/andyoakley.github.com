---
title: Learning about PowerShell script modules psm1
layout: post
tags:
- powershell
---
I cleaned up a few Active Directory related PowerShell scripts this evening with a view to sharing them more broadly. More on that in another post. In honesty much of my recent PowerShell work has been rather hacky, just cobbling together script files until they run for a specific task at hand. Not exactly anything to be proud of or the readily reusable stuff I'd like to share so I figured it was time to brush up [PowerShell modules](http://msdn.microsoft.com/en-us/library/windows/desktop/dd878324.aspx) which are well suited to exposing functionality.

In my case I'm not doing anything too fancy and my module will be very similar to the existing ps1 script. The major difference (and benefit) with a script module is the scope in which variables and functions are defined (i.e. not necessarily global) and the level of control the author retains over what is exposed (e.g. functions can be defined for use by other functions in the module but not exposed outside of it).

###To convert a ps1 to psm1 PowerShell script module

1. Make sure your functionality is neatly wrapped up in functions. A script which actually does work stuff in its script scope may need slight rework.
1. Identify the functions to expose. Use the `Export-ModuleMember -function fun1, fun2` to expose `fun1` and `fun2`.

###To install the module (optional)

1. Make sure you have a `Modules` folder in place. If not, create it with `new-item -type directory -path $home\Documents\WindowsPowerShell\Modules`
1. Copy the module folder containing the psm1 file into the `Modules` folder. Use `copy-item -path c:\ps-test\MyModule -dest $home\Documents\WindowsPowerShell\Modules`

### To use the module
To use the module, simply use `import-module <modulename>`. If you haven't installed the module into the well-known path defined above, `import-module` can also take a full path to a psm1 file as a parameter. The exposed functions and variables will now be defined and ready for use.

Once you see how this model works it's very clean and organized.
