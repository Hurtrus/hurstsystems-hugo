---
title: PowerShell Notes
date: "2018-10-04"
hero_image: "powershellLogosmaller.png"
---

Notes about various things that I wanted to find again later, or a few things that would be useful to others. From "Free eBooks" to links about HashTables and Arrays, there will not be any rhyme or reason to this post. Enjoy.

<!-- end -->

# Free eBooks:

[Historical Trend Reports in Powershell](https://legacy.gitbook.com/book/devops-collective-inc/ditch-excel-making-historical-trend-reports-in-po/details)

[Where and Foreach Methods](https://freecontent.manning.com/powershell-v4-where-and-foreach-methods/?utm_content=article_powershellv4whereandforeachmethods_oct2115)

[PowerShell Advanced Functions](http://mikefrobbins.com/2015/04/17/free-ebook-on-powershell-advanced-functions/)

[Kevin Marquette on PowerShell Theory](https://kevinmarquette.github.io/)

================

[Automatically Store Last Output](https://vexx32.github.io/Store-Last-Output/)

================

# Hashtables

[Everything you wanted to know about HashTables](https://kevinmarquette.github.io/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/?utm_source=blog&utm_medium=blog&utm_content=popref)

================

# Arrays

[Everything you wanted to know about arrays](https://kevinmarquette.github.io/2018-10-15-Powershell-arrays-Everything-you-wanted-to-know/?utm_source=blog&utm_medium=blog&utm_content=titlelink)

```powershell
##############################################################
    # Method 1
    # Create empty array then use the $variable.add("value") later

$Report = [System.Collections.ArrayList]@()
##############################################################
    # Method 2
    # Create and populate an array then use the $variable.add("value") later

$Report = [System.Collections.ArrayList]("A", "B", "C", "D")
##############################################################
    # Method 3
    # Create and populate an array then use the $variable.add("value") later

[System.Collections.ArrayList]$Report = "I", "J", "K", "L"
##############################################################

    # Methods 2 and 3 are the same just depending on how you want to initate it
    # All 3 methods use the following to add/remove values. 

$Collection = New-Object -TypeName System.Collections.ArrayList
$Random = New-Object -TypeName System.Random

$Collection.Add($Random.Next(0,1000)) | Out-Null 

```

More examples of System.Collections.ArrayList : 

[Write PowerShell for Speed](https://4sysops.com/archives/how-to-write-powershell-for-speed/)

[Userful .NET Classes for Powershell](https://4sysops.com/wiki/useful-net-classes-for-powershell/)

================

[Everything you ever wanted to know about the Switch statement](https://kevinmarquette.github.io/2018-01-12-Powershell-switch-statement/?utm_source=blog&utm_medium=blog&utm_content=titlelink)

# RegEx a Phonenumber

```powershell

# $a is the original phonenumber
$a = [int64]'1234567890'

# $b is the pattern we want to force $a into
$b = "{0:###-###-####}" -f $a

# output of our regex
$b

# get the last 4 digits of the number
$b.Substring($b.Length -4)

```

================

# Markdown template for Links

```Markdown

[Title](URL)

```
