---
title: PowerShell - Error Handling
date: "2018-10-03"
hero_image: "powershellLogosmaller.png"
---

# PowerShell - Error Handling

Try Catch and Finally

## Try
When we need to watch a block of our code for errors, our new best friend is the `try` statement. Ever dillagent, `try` knows the danger that looms and is looking out for you when a "terminating" error occurs.  
We can also tell `try` to be on the lookout for other types of errors, those errrors that don't stop the function in its tracks (also known as Non-Terminating), but may cause problems later in our code because this function was unable to be successfully executed.  

An example of a Non-Terminating error would be `Remove-Item` not being able to find the object, or `Get-AdUser` not being able to find the user in Active Directory. The error thrown by these issues won't stop the show, it will flood our pretty terminal with a river of red text, but the execution of code will march ever forward.  

To instuct our good friend `try` to grab Non-Terminating errors we need to use the *_-ErrorAction_* property and set it to *_'Stop'_* now this Non-Terminating error will behave in a similar manner as a Terminating error (_although it is still a Non-Terminating error_) and `try` will once again do it's job.

## Catch


## Catching Specific Exceptions

When capturing an error and specifying an error in a catch, it only works with *Terminating* errors. Non-terminating errors cannot be _caught_ in this manner. 

```powershell
Try
{
    $AuthorizedUsers= Get-Content \\FileServer\RemoteShare\CoolListofStuff.txt -ErrorAction Stop
}
Catch [System.OutOfMemoryException]
{
    Restart-Computer localhost
}
Catch
{
    $ErrorMessage = $_.Exception.Message
    $FailedItem = $_.Exception.ItemName
    Send-MailMessage -From ExpensesBot@MyCompany.Com -To WinAdmin@MyCompany.Com -Subject "HR File Read Failed!" -SmtpServer EXCH01.AD.MyCompany.Com -Body "We failed to read file $FailedItem. The error message was $ErrorMessage"
    Break
}
```

## Putting the Error into Action

### Difference between ErrorAction and $ErrorActionPreference

`ErrorAction` is a different beast than `$ErrorActionPreference`

$ErrorActionPreference is a Preference Variable [About Preference Variables](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_preference_variables?view=powershell-6)
This preference variable enable you to customize the behavior and how it affects the PowerShell operating environment and all commands run in the environment.

ErrorAction is a Common Parameter [About CommonParameters](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-6)
This _common parameter_ affects the behavior of the specific cmdlet it is used with, and the environment itself is left unchanged. It is used to override the preference for a single command.

ErrorAction has the same valid values as the $ErrorActionPreference variable.

Valid values for $ErrorActionPreference and ErrorAction
 - Stop: Displays the error message and stops executing.
 - Inquire: Displays the error message and asks you whether you want to continue.
 - Continue: Displays the error message and continues (Default) executing.
 - Suspend: Automatically suspends a workflow job to allow for further investigation. After investigation, the workflow can be resumed.
 - SilentlyContinue: No effect. The error message is not displayed and execution continues without interruption.  


### Why you would need to change the $ErrorActionPreference

What do you do when ErrorAction parameter isn't available (it happens in rare cases)?
Well customize the $ErrorActionPreference of course!  
```powershell
# Here we capture the Original ErrorAction Preference settings
$OriginalErrorActionPreference = $ErrorActionPreference

function MySpecialCaseFunction
{
  $ErrorActionPreference = 'Stop' # Change the preference to Stop
    try
    {
      [rare.case]::WhereErrorAction.DoesntWork
    }
    catch
    {
      Do Something_Cool
    }
    finally
    {
      $ErrorActionPreference = $OriginalErrorActionPreference # Set the preference back to original
    }
}


```

### Using that Finally finally

Hey man... what was that _finally_ thing in that example above?
"Finally" executes regardless of the try being successful or not, so it is the perfect place to do some cleaning up.

## Throw

- Why you would need to use Throw?
- Using the Throw keyword says that the error being thrown is a terminating error?


## Additional Reading Resources:

[Try-Catch-Finally in PowerShell](https://www.vexasoft.com/blogs/powershell/7255220-powershell-tutorial-try-catch-finally-and-error-handling-in-powershell)

[A Look at Try/Catch in PowerShell](https://learn-powershell.net/2015/04/04/a-look-at-trycatch-in-powershell/)
