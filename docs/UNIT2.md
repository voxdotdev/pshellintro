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

## Improve the reading experience
Running `Get-Help` returns the entire help page.  A better approach is to use the `help` alias
</br>
This will pipe `Get-Help` through a function to limit output line by line by section.
<details>
<summary>Example</summary>
<code>help Get-FileHash</code>
</details>

# Exercise - Using help

1. Run the command `Get-Help -Name Get-FileHash`
2. Run the command `help Get-FileHash`
3. Run `help Get-FileHash -Examples`

For commands, add the flag `-Examples` when you search for help to quickly see an example if available.

# Discover objects
<p>When a cmdlet runs, it returns an object. The response you see on invoking a cmdlet has been formatted
and might not necessarily represent all the available information for the response. </p>

To know more about what's being returned and how you can modify it, you can use the `Get-Member`

## Discover objects by using `Get-Member`
The `Get-Member` cmdlet is meant to be piped on top of the command you run so you can filter the output. </br> 
<code>Get-Process</code> returns a matching process running on target machine</br>
<code>Get-Member</code> gets the properties (Name, MemberType, Definition) of objects</br>
To get a list of the processes running on your machine, run <code>Get-Process</code>.</br>

`Get-Process -Name 'name-of-process' | Get-Member`

</details>

## Search by type
Running <code>Get-Process</code> returns an object, which is then passed to <code>Get-Member</code>
by using the pipe <code>|</code>


<details>
    <summary>Let's say you invoked the PoweShell command that lists all members for the windows process "explorer". </br>
    </summary>
    <code>Get-Process -Name explorer | Get-Member</code>
</details>
    <table>
        <strong>TypeName: System.Diagnostics.Process</strong></br>
        The first row indicates that the type is System.Diagnostics.Process.</br>
        <tr>
            <th>Name</th>
            <th>MemberType</th>
            <th>Definition</th>
        </tr>
        <tr>
            <td>Handles</td>
            <td>AliasProperty</td>
            <td>Handles = Handlecount</td>
        </tr>
        <tr>
            <td>Name</td>
            <td>AliasProperty</td>
            <td>Name = ProcessName</td>
        </tr>
        <tr>
            <td>NPM</td>
            <td>AliasProperty</td>
            <td>NPM = NonpagedSystemMemorySize64</td>
        </tr></br>
    </table>
   
    
Use this type, `Process`, as a search argument to look for other cmdlets that use this type. </br>
`Get-Command -ParameterType Process`</br>
    <table>
        <tr>
            <th>CommandType</th>
            <th>Name</th>
            <th>Version</th>
            <th>Source</th>
        </tr>
        <tr>
            <td>Cmdlet</td>
            <td>Get-PSHostProcessInfo</td>
            <td>3.0.0.0</td>
            <td>Microsoft.PowerShell.Core</td>
        </tr>
        <tr>
            <td>Cmdlet</td>
            <td>Enter-PSHostProcess</td>
            <td>3.0.0.0</td>
            <td>Microsoft.PowerShell.Core</td>
        </tr>
    </table>
    The result is a list of cmdlets that operate on this type.
</br>


## Filter a `Get-Member` result by using Select-Object
When you run `Get-Member`, the result is verbose, many rows are returned.
To make things easier to read, you can filter on sepcific columns, as well as descibe which columns to display.

<details>
<summary>Take a look at at a <code>Get-Member</code> response that includes many columns. 
    By introducting the <code>Select-Object</code> cmdlet, you can choose which columns appear in the response.
    The command expects either a comma-separated list of columns names, or a wildcard character <code>*</code>,
    which indicates all columns.</summary>
<code>Get-Process -Name explorer | Get-Member | Select-Object Name, MemberType</code>
</details>
    <table>
        <tr>
            <th>Name</th>
            <th>MemberType</th>
        </tr>
        <tr>
            <td>Handles</td>
            <td>AliasProperty</td>
        </tr>
        <tr>
            <td>Name</td>
            <td>AliasProperty</td>
        </tr>
        <tr>
            <td>NPM</td>
            <td>AliasProperty</td>
        </tr>
    </table>

Definition column was ommited from the results

<details>
<summary>
    You also can filter the response by rows.
</summary>
<code>Get-Process -Name explorer | Get-Member -MemberType AliasProperty</code>
</details>

</br>
<a href="https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-process?view=powershell-7.2">Additional Reading</a>


#
<sup>[Return to README.md](/README.md)</sup>

