# BARTENDER
![logo](./icon.png)

> A Framework for making PowerShell Modules

[releasebadge]: https://img.shields.io/static/v1.svg?label=version&message=6.1.21&color=blue
[datebadge]: https://img.shields.io/static/v1.svg?label=Date&message=2019-03-12&color=yellow
[psbadge]: https://img.shields.io/static/v1.svg?label=PowerShell&message=5.0.0&color=5391FE&logo=powershell
[btbadge]: https://img.shields.io/static/v1.svg?label=bartender&message=6.1.20.3&color=0B2047


| Language | Release Version | Release Date | Bartender Version |
|:-------------------:|:-------------------:|:-------------------:|:-------------------:|
|![psbadge]|![releasebadge]|![datebadge]|![btbadge]|


Authors: Adrian.Andersson

Company: Domain Group

Latest Release Notes: [here](./documentation/6.1.21/release.md)

***

<!--Bartender Dynamic Header -- Code Below Here -->

## What is this

A module framework for PowerShell


## Why did I make this

1) To make my PowerShell modules follow the Continuous Integration -> Continuous Delivery lifecycle

2) To make collaborating on PowerShell projects as easy as possible

3) To try and encourage good practices around Pester Testing and Documentation

## Quick Start Guide

### Install the module

```powershell
install-module -name bartender
```


### Setup your bartender publish repository


```powershell
save-btRepository -repository myRepo -token myNugetToken -credential $(get-credential)
```
> assumes a repository is already in place

> Check [here](https://powershellexplained.com/2018-03-03-Powershell-Using-a-NuGet-server-for-a-PSRepository/?utm_source=blog&utm_medium=blog&utm_content=tags) for an execelent blog post from Kevin Marquette for more details

> Token is used for publishing to nuget repositories and is not needed for fileshare repositories

> Credentials are used for checking module dependancies and are only required if the repository is private

### Setup your bartender defaults


```powershell
$myDefaults = @{
   author = 'myname'
   repository = 'myRepo'
   company = 'myCompany'
   tags = @('mydepartment')
   publishOnBuild = $true
   autoDocument = $true
   includeGitDetails = $true
   trimSpaces = $false
   removeEmptyLines = $true
   removeSingleLineQuotes = $false
   runPesterTests = $true
}
save-btDefaultSettings @myDefaults
```

### Create a new btProject

```powershell
md $newProjectFolder
cd $newProjectFolder

new-btProject -moduleName myBtProject -moduleDescription 'my bartender module'
```
![newproject](.\gifs\newproject.gif)

## Start Coding

### Create a function

![function](.\gifs\function.gif)

### Create Create a pester test
![pester](.\gifs\pester1.gif)

### Build your first revision and test it out
![build1](.\gifs\build1.gif)

### Increment your build/minor/major version to initiate a release build
![build1](.\gifs\build2.gif)

### Check out your fancy automated markdown
![build1](.\gifs\markdown.gif)


## Module Features

 ### 
 - Collaboration
    - Standard folder layout and file locations
    - Allow customisation of file orders and subfolders within the framework
    - Provide an integrated way of updating the framework
    - Simplify module creation and focus on function creation
    - Keep all the build settings in a single config file
    - Centralize your scripts
 - Separation of Concerns
    - Source files can be separated on a functional level
    - Classes, DSCClasses, Enums and Functions handled according to their needs
      - Separation of private and public functions
      - Use preload scripts for enums and classes to ensure they are scoped both privately and publicly
 - Easier Module-Wide Pester Testing
    - Include basic pester tests that:
      - Ensure we run in a clean-tree
      - Ensure the module compiles and loads correctly
    - Make adding new tests as simple as making a new ps1 script in the appropriate folder
 - Release Management
    - Automatic publishing to a repository on test-passing
    - Revision increasing for test cycles
    - Version increases (Major, Minor, Build) for releases
    - Integrate a basic release notes markdown
 - Better Module Customisation
    - Deal with extended module manifest PrivateData
 - Use PlatyPS for version documentation
    - Automatically compile the inline help into markdown
    - Allow for the documentation to evolve with the code naturally
    - Ensure properly documented advanced functions create appropriate markdown

###
Owned and maintained by Domain Group

[powershellbadge]: https://img.shields.io/static/v1.svg?label=language&message=PowerShell%20%3E_&color=blue&logo=powershell&style=plastic

