---
title: PowerShell - Pester Notes
hero_image: "powershellLogosmaller.png"
date: "2018-09-23"
---

# Pester

### Time to learn Pester. Not so much a blog post as it is a reading/reference list.

## What is Pester?

"Pester is the ubiquitous test and mock framework for PowerShell" or in other words, tests written to test the functions you have created without actually running those commands.  
Are you asking yourself "why bother? just run the code and see if it works?"  Yeah me too, but seems like everyone is doing it... so might as well jump off a bridge also, hopefully by the end I will see its value.

Create a new test

```powershell
#Change directory into the desired location
cd C:\temp\my_PesterTests

#Create new test boilerplate
New-Fixture -Path C:\temp\my_PesterTests\Pester_Test -Name Pester_Test
```

Invoke-Pester will execute the Powershell file ending with the name .Tests.ps1 against the other file that just ends in .ps1 (in the current directory).  
In the terminal (not in the ISE part but at the *>*) execute something like this:

```powershell
cd C:\temp\my_PesterTests

Invoke-Pester 
```

- [Pester](https://github.com/pester/Pester)
- [Introduction to Testing Your PowerShell Code with Pester](https://www.red-gate.com/simple-talk/sysadmin/powershell/introduction-to-testing-your-powershell-code-with-pester/)
- [Unit Testing PowerShell Code with Pester](https://blogs.technet.microsoft.com/heyscriptingguy/2015/12/16/unit-testing-powershell-code-with-pester/)
- [Example using Ping](https://blogs.msdn.microsoft.com/mvpawardprogram/2017/05/30/testing-powershell-with-pester/)
- [More Examples and Explinations](https://www.robinosborne.co.uk/2016/06/27/unit-testing-powershell-with-pester/)
- [Example: Automate Infrastructure Testing with Pester](https://www.cardinalsolutions.com/blog/2018/02/automate_infrastructure_testing_with_pester)
- [Another good Example](http://powershelldistrict.com/pester-test-part3-advanced-concepts/)

Code Coverage refers to the percentage of lines of code that are tested by a suite of unit tests.
- [Code Coverage](https://github.com/pester/Pester/wiki/Code-Coverage)


## Advanced docs

- [Testing Infrastructure - DSC & Pester](https://sysnetdevops.com/2017/06/05/testing-infrastructure-with-pester/)
- [Release Pipeline WhitePaper](https://docs.microsoft.com/en-us/powershell/dsc/whitepapers#the-release-pipeline-model)
- [building-a-simple-release-pipeline-in-powershell-using-psake-pester-and-psdeploy](https://devblackops.io/building-a-simple-release-pipeline-in-powershell-using-psake-pester-and-psdeploy/)
- [CI/CD pipeline for a new module](https://kevinmarquette.github.io/2017-01-21-powershell-module-continious-delivery-pipeline/?utm_source=blog&utm_medium=blog&utm_content=titlelink)

## Pester -TestCases

- [Of course AB has me covered!](https://mcpmag.com/articles/2017/03/23/powershell-test-case-code-with-pester.aspx)
- [More TestCases](https://sqldbawithabeard.com/2017/11/28/2-ways-to-loop-through-collections-in-pester/)

## Pester Tags

- [Tags in Pester for Targeted Testing](https://blog.techsnips.io/how-to-use-tags-in-pester-for-targeted-testing/)

