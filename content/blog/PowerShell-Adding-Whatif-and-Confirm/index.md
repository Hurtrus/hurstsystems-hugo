---
title: PowerShell - Adding WhatIf and Confirm
author: "Scott Hurst"
date: "2018-10-23"
hero_image: "powershellLogosmaller.png"
---

So I planned to write a blog post about how to add WhatIf and Confirm to your PowerShell code and began to do research on the topic. I found that a bunch of awesome blogs that already had covered this topic, so I grabbed some information about each and threw it into this post. I will clean this up and make it more readable at a later time, just wanted to get this into my site so that I could find it and use it when needed.

<!-- end -->

# PowerShell Advanced Functions - Adding WhatIf and Confirm

Source:

[THE LONELY ADMINISTRATOR Blog](https://jdhitsolutions.com/blog/powershell/4319/powershell-blogging-week-supporting-whatif-and-confirm/) - jdhitsolutions.com

##### I take no credit, I am just taking notes. I don’t figure anyone will actually find this post until I have learned enough to re-write it using my own examples. No one has called me out on this, I just want credit to go where it is due.

##### again all credit goes to Jeff Hicks and his blog post. I take NONE of the credit.

If SupportsShouldProcess is listed it will enable the –WhatIf and –Confirm parameters on the function if you are using PowerShell cmdlets that already support –WhatIf.

Things gets a little trickier when you want to support WhatIf for a function where your commands don’t natively recognize SupportsShouldProcess. This would be true of any .NET static method or even a command line tool you might be running, to name a few examples. 
To add support you need to invoke the built-in $PSCmdlet object and its ShouldProcess() method. Here’s a simple example.

```powershell

Function Set-Folder {
[cmdletbinding(SupportsShouldProcess)]
 
Param(
[Parameter(Position=0,
ValueFromPipeline,
ValueFromPipelineByPropertyName)]
[Alias("pspath")]
[ValidateScript({Test-Path $_})]
[string]$Path=".")
 
Process {
$Path = (Resolve-Path -Path $Path).ProviderPath
if ($PSCmdlet.ShouldProcess($Path)) {
#do the action
$Path.ToUpper()
}
} #Process
 
} #end function

```

This function hypothetically is going to perform some action on a folder and I’m simply displaying the folder name in upper case. The important part is the If statement. This is the bare minimum that you need. If you specify –WhatIf you’ll be prompted.


provide more specific information by specifying ShouldProcess parameters for the target and action.
You must have the code for ShouldProcess otherwise even if you set the cmdletbinding attribute, PowerShell won’t know which commands need WhatIf. You can also have as many ShouldProcess statements as you need.


```powershell

Function Set-Folder2 {
[cmdletbinding(SupportsShouldProcess)]
 
Param(
[Parameter(Position=0,
ValueFromPipeline,
ValueFromPipelineByPropertyName)]
[Alias("pspath")]
[ValidateScript({Test-Path $_})]
[string]$Path=".")
 
Process {
$Path = (Resolve-Path -Path $Path).ProviderPath
if ($PSCmdlet.ShouldProcess($Path,"Updating")) {
#do the action
$Path.ToUpper()
}
} #Process
 
} #end function

```

Confirmation happens by comparing the value of ConfirmImpact with the built-in $ConfirmPreference variable which has a default value of High. If the value of $ConfirmPreference is equal to or greater than ConfirmImpact, PowerShell will prompt for confirmation. 


```powershell

Function Set-Folder6 {
[cmdletbinding(SupportsShouldProcess,ConfirmImpact="High")]

Param(
[Parameter(Position=0,
ValueFromPipeline,
ValueFromPipelineByPropertyName)]
[Alias("pspath")]
[ValidateScript({Test-Path $_})]
[string]$Path="."
)
Begin {
Write-Verbose "Starting $($MyInvocation.Mycommand)"
} #begin

Process {
$Path = (Resolve-Path -Path $Path).ProviderPath
Write-Verbose "Processing $path"
if ($PSCmdlet.ShouldProcess($Path,"Updating")) {
#do the action
$Path.ToUpper()
} #ShouldProcess
} #Process

End {
Write-Verbose "Ending $($MyInvocation.Mycommand)"
} #end

} #end function

```



Source:

[THE LONELY ADMINISTRATOR Blog](https://jdhitsolutions.com/blog/powershell/4319/powershell-blogging-week-supporting-whatif-and-confirm/) - jdhitsolutions.com