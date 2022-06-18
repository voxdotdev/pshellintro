#  [Introduction to PowerShell](https://docs.microsoft.com/en-us/learn/modules/introduction-to-powershell/)

## Introduction

<p>PowerShell is a command-line shell and a scripting language all in one. It was designed as a task engine that uses cmdlets to wrap tasks that people need to do. In PowerShell, you can run commands on local or remote machines. You can do tasks like managing users and automating workflows.</p>

<p>Whether you're part of an operations team or a development team that's adopting DevOps principles, PowerShell can help. You can use it to address various tasks, such as managing cloud resources and continuous integration and continuous delivery (CI/CD). PowerShell offers many helpful commands, but you can expand its capabilities at any time by installing modules.</p>

### Learning objectives

When you finish this module, you'll be able to:

  *  Understand what PowerShell is and what you can use it for
  *  Use commands to automate tasks

### Prerequisites

To complete this module, you should:

  *  Basic familiarity with using a command-line shell like Command Prompt or Git Bash
  *  Visual Studio Code installed
  *  Ability to install Visual Studio Code extensions
  *  Ability to install software on your computer, if you're not using a Windows operating system


## What is PowerShell?

PowerShell is a command-line shell and a scripting language all in one.

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

[PowerShell extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell)

## Exercise - Run your first PowerShell commands

### `$PSVersionTable` - command to verify PowerShell installation 

<details>
    <summary>
        Returns
    </summary>
    <table>
        <tr>
            <th>Name</th>
            <th>Value</th>
        </tr>
        <tr>
            <td>PSVersion</td>
            <td>5.1.19041.1682</td>
        </tr>
        <tr>
            <td>PSEdition</td>
            <td>Desktop</td>
        </tr>
    </table>
    ...and so on.
</details>

Because `$PSVersionTable` is an object, you can append it with a period to acess a specific property, for example, `$PSVersionTable.PSVersion`

<details>
    <summary>Returns</summary>
    <table>
        <tr>
            <th>Name</th>
            <th>Value</th>
        </tr>
        <tr>
            <td>PSVersion</td>
            <td>5.1.19041.1682</td>
        </tr>
    </table>
</details>

## Locate Commands 

### Cmdlets 
<p>A cmdlet is a compiled command. A cmdlet can be developed in .NET or .NET Core, and invoked as a command within PowerShell. </p>

Cmdlets are named according to a verb-noun naming standard.
This pattern can help you to understand what a cmdlet does and how to search for one. You can see a list of approved verbs by using the `Get-Verb` cmdlet. 
Verbs are organized by activity type and function. </p>

<details>
    <summary><strong>Part of the output from running Get-Verb</strong></summary>
    <table>
        <tr>
            <th>Verb</th>
            <th>AliasPrefix</th>
            <th>Group</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>Add</td>
            <td>a</td>
            <td>Common</td>
            <td>Adds a resource to a container, or atta…</td>
        </tr>
        <tr>
            <td>Clear</td>
            <td>cl</td>
            <td>Common</td>
            <td>Removes all the resources from a contai…`</td>
        </tr>
    </table>
</details>

<p>This listing shows the verb and its description. 
Cmdlet developers should use an approved verb, and ensure the verb description fits their 
cmdlet's function. </p>

### Examples

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

### Run `Get-Command -Noun File*`

<details>
    <summary>Output</summary>
    <table>
        <tr>
            <th>CommandType</th>
            <th>Name</th>
            <th>Version</th>
            <th>Source</th>
        </tr>
        <tr>
            <td>Cmdlet</td>
            <td>Get-FileHash</td>
            <td>7.0.0.0</td>
            <td>Microsoft.PowerShell.Utility</td>
        </tr>
        <tr>
            <td>Cmdlet</td>
            <td>Out-File</td>
            <td>7.0.0.0</td>
            <td>Microsoft.PowerShell.Utility</td>
        </tr>
        <tr>
            <td>Cmdlet</td>
            <td>Unblock-File</td>
            <td>7.0.0.0</td>
            <td>Microsoft.PowerShell.Utility</td>
        </tr>
    </table>
</details>

### Further filter the response via the `-Verb` flag 

<details>
    <summary>Hint</summary>
    <code>syntax: `Get-Command -Verb Get -Noun File*</code>
</details>

<details>
    <summary>Output</summary>
    <table>
        <tr>
            <th>CommandType</th>
            <th>Name</th>
            <th>Version</th>
            <th>Source</th>
        </tr>
        <tr>
            <td>Cmdlet</td>
            <td>Get-FileHash</td>
            <td>7.0.0.0</td>
            <td>Microsoft.PowerShell.Utility</td>
        </tr>
    </table>
</details>

Only one record matches because you specified both the `-Noun` parameter and the `-Verb`

## Knowledge Check 

<details>
<summary>
What's a correct way to locate a command in PowerShell?
</summary>
Call <code>Get-Command 'name of command'</code>
</details>

<details>
<summary>
How would you search for commands that deal with files?
</summary>
Call <code>Get-Command -Noun File*</code>
</details>

## Summary

<p>In this module, you started by learning what PowerShell is and what you can use it for.
You then learned about compiled commands called cmdlets. 
You looked specifically at a command called Get-Command that helps you locate the command you need.</p>

## Resources
[Getting Started with PowerShell](https://docs.microsoft.com/en-us/powershell/scripting/learn/ps101/01-getting-started?preserve-view=true&view=powershell-7.2&WT.mc_id=academic-16634-chnoring&viewFallbackFrom=powershell-7.1)

## [Next Lesson](/docs/2_Discover-commands-in-PowerShell.md)

<sup>[Return to README.md](/README.md)</sup>