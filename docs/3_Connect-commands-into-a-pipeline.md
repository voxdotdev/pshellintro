# [Connect commands into a pipeline](https://docs.microsoft.com/en-us/learn/modules/connect-commands/)

## NOTE: Unit abridged 
This unit seeks solely to provide more detail about the fundamentals regarding identifying pre-existing cmdlets and their expected behavior. This section has been narrowed or otherwise has had entire sections omitted. This may be updated in the future. For now, review the unabridged course directly on Microsoft's website.

## Introduction
<p>In PowerShell, you run compiled commands, or cmdlets. By connecting these cmdlets, you can create powerful combined statements, or pipelines. You'll find such combined statements useful as you're looking to automate your workflows.</p>

<p>As part of creating these pipelines, it's beneficial to understand how to format the output to your liking. For example, a carefully selected output format might allow you to quickly get an overview of a situation, or make it easier to fit the output into a report.</p>

### Learning objectives
After you complete this module, you'll be able to:

* Explore cmdlets further and construct a sequence of them in a pipeline.
* Apply sound principles to your commands by using filtering and formatting.

## Selecting data

<p>Most commands operate on objects, as input or as output, or both. Objects have properties and you may want to access a subset of those properties and present them in a report. You might also want to sort the data based on one or more properties. But how do you get there?</p>

### Use Get-Member to inspect output

When you pass the results of a command to `Get-Member`, `Get-Member` returns information about the object, such as: 

* The type of object being passed to `Get-Member`
* The Properties of the object that may be evaluated. 
* The Methods of the object that may be executed.  

<details>
<summary>
Example Command 
</summary>
<code>Get-Process | Get-Memeber</code>  
</details>

<details>
    <summary>
Result
</summary>
    <code>Get-Process | Get-Memeber</code>  
    </details>
    <p>Note how you are using the pipe <code>|</code> 
        and that by calling <code>Get-Member</code>, 
        you are in fact creating a pipeline already. 
        The first few lines of output from the preceding statement 
        look like so:</p>
        <table>
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
                <td>NPM = NonpagesSystemMemorySize64</td>
            </tr>
        </table>
        The output shows the type of object that the Get-Process 
        command returns <code>(System.Diagnostics.Process)</code>. 
        The rest of the response shows the name, type, and definition of
        the object's members. You can see that If you want to fit 
        <code>Get-Process</code> with another command in a pipeline, 
        pairing it with <code>Get-Member</code> is a good first step. 
        
        
        
### Select-Object
By default, when you run a command that is going to output to the screen, PowerShell automatically adds the command `Out-Default`. If the data is not just a collection of strings, but objects - PowerShell looks at the object type to determine if there is a registered view for that object type, and if so, it uses that view.

You can override the default view by using `Select-Object` and choosing your own list of properties. You can then send those properties to `Format-Table` or `Format-List`, to display the table however you like.

### Getting the full response
<details>
<summary>
What you've seen so far is a limited response. To present the full response, you use a wildcard <code>*</code>
</summary>
<code>Get-Process zsh | Format-List -Property *</code>
</details>

The `*` character shows you every attribute and its value, which allows you to investigate the values you are interested in. The full response also uses presentation names for properties instead of the actual property names, and presentation names look good in a report.</br>


`Get-Process explorer | Select-Object *` 
</br>vs</br>
`Get-Process explorer | Select-Object StartTime`

`Get-Process explorer | Format-List -Property *` 
</br>vs</br>
`Get-Process explorer | Format-List -Property StartTime`

## Exercise - Construct a pipeline

### Discover the most-used processes on your machine

To manage your machine, you sometimes need to discover what processes run on
it and how much memory and CPU they consume. 
This information tells you what the machine spends its resources on. 

Run the following command: </br> 
`Get-Process | Where-Object CPU -gt 2 | Sort-Object CPU -Descending | Select-Object -First 3`


The exact output you see depends on your machine, 
but you should see a result where the first 3 processes whose 
CPU value is greater than 2 are sorted in descending order, 
with the greatest CPU value at the top of the list. 

What you see is a view that represents what you most likely want to see from this command. However, this view does not show you a complete set of information.

## Knowledge Check

<details>
<summary></summary>
<code></code>
</details>

<details>
<summary></summary>
<code></code>
</details>

<details>
<summary></summary>
<code></code>
</details>

## Summary

## Resources
[]()
[]()

## [Next Lesson - Write your first PowerShell code](/docs/4_Write-your-first-PowerShell-code.md)
<sup>[Return Home](/README.md)</sup>