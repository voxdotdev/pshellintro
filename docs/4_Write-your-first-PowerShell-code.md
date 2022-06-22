# [Write your first PowerShell code](https://docs.microsoft.com/en-us/learn/modules/powershell-write-first/)

## Introduction

In this module, you begin learning the basics of programming by writing and running code in PowerShell.

### Learning objectives

After you've completed this module, you'll be able to:

   * Manage PowerShell inputs and outputs.
   * Diagnose errors when you type code incorrectly.
   * Identify PowerShell elements such as cmdlets, parameters, inputs, and outputs.

## Exercise - "Hello World"
One of the best ways to learn to code is to write many tiny programs. 

`New-Item` command creates a new .ps1 file in the directory the terminal is in. 

The `code` command followed by the file name will open the file in your default editor. This command is not unique to PowerShell. 

1. Confirm the directory you're in is your intended, if not, navigate there via [CD](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/cd) - for this repo, this execise can be located in [scripts](./scripts/helloworld.ps1).

2. Invoke the following command in your terminal: `New-Item HelloWorld.ps1`
to create your powershell script file. 

3. Invoke `code HelloWorld.ps1` to open your new script in your default IDE.

4. Within the now-opened file, write `Write-Output 'Hello World!'`, save the file. 

5. Run the file in the terminal via the following command
`. ./HelloWorld.ps1`

6. If error, check your spelling. Otherwise, Rejoice, retire. you are now epic programmer.

### To be continued

<sup>[Return Home](/README.md)</sup>