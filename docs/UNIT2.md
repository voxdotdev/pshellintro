# [Discover commands in PowerShell](https://docs.microsoft.com/en-us/learn/modules/discover-commands/)

By using the built-in help system in PowerShell, you can find out more about a specific command. 

You use the `Get-Command` cmdlet to locate a command that you need. 

After you've located the command, you might want to know more about what the command does and various ways to call it.

## Discover cmdlets by using the help system and Get-Help

As previously mentioned in **[Unit 1](/UNIT1.md#locate-commands)**, you can use the `Get-Help`
cmdlet to learn more about a command. Typically you invoke `Get-Help` and add the `-Name` flag that contains the name of the cmdlet you want to learn about. 

<details>
<summary>Example</summary>
<code>Get-Help -Name Get Help</code>
</details>

You may need to update Help when running `Get-Help` for the first time, which can be done via the command below.

<details>
<summary>Update Help Command</summary>
<code>Update-Help -UICulture en-US</code><br>
<code>-UICulture</code> flag gives the flag en-US for US English help files. </br>
<em>
<a href= "https://docs.microsoft.com/en-us/answers/questions/405758/not-able-to-update-help-in-powershell.html">
if this returns an error, run PowerShell as admin, else disregard</a>
</em>
</details>

## Explore help sections
Invoking the Get-Help command returns information of the located cmdlet under some or all of the following categories: 

**NAME** Provides name of Command </br>
**SYNOPSIS** Describes behavior of command</br>
**SYNTAX** Displays possible combinations of flags and occassionally parameters</br>
**DESCRIPTION** Details the synopsis
**ALIASES** lists any aliases for a command, aka shortname for a command</br>
**RELATED LINKS / REMARKS** Provides information about what commands to run to get detailed help
</br>

## Filter the help response
If you don't want to display the full help page, narrow the response by adding flags to your `Get-Help` command. Some flags you can use: 

**FULL** Returns a detailed help page. </br>
**DETAILED** Returns a response that looks like the standard response, but it includes a section for parameters.</br>
**EXAMPLES** Returns only examples, if any exist.</br>
**ONLINE** Opens a web page for your command.
**PARAMETER** Requires a parameter name as an argument. </br>
It lists a specific parameter's properties.</br>

<details>
<summary>Example</summary>
<code>Get-Help Get-Help -Examples</code>
</details>
</br>

## Improve the reading experience
Running `Get-Help` returns the entire help page.  A better approach is to use the `help` alias
</br>
This will pipe `Get-Help` through a function to limit output line by line by section.
<details>
<summary>Example</summary>
<code>help Get-FileHash</code>
</details>

#
 <sup>[Return to README.md](/README.md)</sup>