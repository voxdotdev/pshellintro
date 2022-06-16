### [Introduction to Powershell - Microsoft](https://docs.microsoft.com/en-us/learn/modules/introduction-to-powershell/1-introduction)



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

### [PowerShell extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell)

## Exercise - Run your first PowerShell commands
`$PSVersionTable` - command to verify PowerShell installation 

Because `$PSVersionTable` is an object, you can append it with a period to acess a specific property, for example, `$PSVersionTable.PSVersion`

## Locate Commands 

A cmdlet is a compiled command. A cmdlet can be developed in .NET or .NET Core, and invoked as a command within PowerShell. 

Cmdlets are named according to a verb-noun naming standard.
This pattern can help you to understand what a cmdlet does and how to search for one. You can see a list of approved verbs by using the Get-Verb cmdlet. 
Verbs are organized by activity type and function. 

Part of the output from running Get-Verb: 
<table>
<tr>
<th>Verb</th>
<th>AliasPrefix</th>
<th>Group</th>
<th>Description</th>
</tr>
<tr>
<th>Add</th>         
<th>a</th>
<th>Common</th>
<th>Adds a resource to a container, or atta…</th>
</tr>
<tr>
<th>Clear</th>       
<th>cl</th>  
<th>Common</th>        
<th>Removes all the resources from a contai…`</th>
</tr>
</table>

This listing shows the verb and its description. 
Cmdlet developers should use an approved verb, and ensure the verb description fits their 
cmdlet's function. 

- `Get-Command` lists all of the available cmdlets on your system.
    - To filter the list, keep in mind the verb-noun naming standard. 
    - For example, Get-Random, Get is the verb, Random is the noun.
    - Use flags to target either the verb or the noun in the command you want. 
    - The flag you specify expects a value that's a string. 
    - You can add pattern-matching characters to that string to ensure you express that. 
        - A flag's value should start or end with a certain string. 

    `Get-Command -Noun a-noun*`
    - `-Noun` flag targets the part of the command name that's related to the noun. 
        - It targets everything after the hyphen. 
    - This command searchs for all cmdlets whose noun part starts with a-noun.

    `Get-Command -Verb Get -Noun a-noun*`
    - `-Verb` flag targets the part of the command name that's related to the verb.
        - You can combine the `-Noun` flag and the `-Verb` flag to create even more detailed filters.

- `Get-Help` Invokes the built-in hlep system. alias: help 
- `Get-Member` When you call a command, the response is an object with many properties. 
    - Run this command to drill down into that response and learn more about it. 

## Exercise - Locate Commands
1. Run `Get-Command -Noun File*`

<table>
<tr>
<th>CommandType</th>
<th>Name</th>
<th>Version</th>
<th>Source</th>
</tr>
<tr>
<th>Cmdlet</th>
<th>Get-FileHash</th>
<th>7.0.0.0</th>
<th>Microsoft.PowerShell.Utility</th>
</tr>
<tr>
<th>Cmdlet</th>
<th>Out-File</th>
<th>7.0.0.0</th>
<th>Microsoft.PowerShell.Utility</th>
</tr>
<tr>
<th>Cmdlet</th>
<th>Unblock-File</th>
<th>7.0.0.0</th>
<th>Microsoft.PowerShell.Utility</th>
</tr>
</table>

## Knowledge Check 

## Summary

