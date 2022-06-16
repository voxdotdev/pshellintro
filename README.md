### Introduction to Powershell - Microsoft

https://docs.microsoft.com/en-us/learn/modules/introduction-to-powershell/1-introduction

### Introduction

PowerShell is a command-line shell and a scripting language all in one.
This course, provided by Microsoft, will offer introductory information to PowerShell. 

### Learning objectives

Understand what PowerShell is, uses 
Use commands to automate tasks 

### Prerequisites 
Command line shells (Command Prompt / Git Bash)
Basic understanding of Visual Studio Code + Extensions 

## What is PowerShell?

PowerShell is made up of two parts, a command-line shell and a scripting language.
PS is cross-platform. 

Command line shell: no graphical interface 
Typing text commands directly into a computer console
- Benefits: Faster than navigating through UI 
- Batch commands together in a script for automation
- Console interacts with cloud resources 
- Storing commands in a text file can be used as a source-control system
  - `git add .` , `git commit -m "iteration %num%"` 

### Features of PowerShell shared with traditional shells:
- Built in help - also integrates with online help articles
- Pipeline - The output of one command is the input for the next command
- Aliases - alternate names that can be used to run commands,
    - such as cls (clear the screen) and ls (list the files

### Features of PowerShell unique from traditional shells:
- It operates on objects over text
- In command-line shell you have to run scripts where output and input might differ
- In comparison, PowerShell uses objects as input and output, meaning less time formatting / extracting 
- Cmdlets. Commands in PowerShell are called cmdlets (pronounced commandlets)
    - these are built on a common runtime rather than separate executables. 
    - cmdlets typically take object input and return objects. Core cmdlets in PS are built into .NET Core and open source. 
    - You can expand PS by using more cmdlets, scripts, and functions from the community, or build your own. 
- Command Diversity - Commands in PowerShell can be native executables, cmdlets, functions, scripts, or aliases. 
    - Every command you run belongs to one of these types. Cmdlet being a type of command, the terminology is used interchangably. 

### Installation
- PowerShell is cross-platform but if using anything beyond Windows 8 or later, installation will be required. 
- Windows 8+, You can open Windows PowerShell from the Start menu.

### PowerShell extension for Visual Studio Code

Recommended Visual Studio Code Plugin (https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell)

## Exercise - Run your first PowerShell commands

## Locate Commands 

## Exercise - Locate Commands

## Knowledge Check 

## Summary

