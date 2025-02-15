Powershell Module with a new cmdlet:

 

Get-SPOFolderFiles

Retrieves all files from a folder.  Not recursive.

 

Parameters

The cmdlet is using the following parameters:

 [string]$Username
The string specifies admin of the site

[string]$Url
Specifies the url of the parent site

[string]$AdminPassword,       
Admin's password

[string]$ServerRelativeUrl
Specifies the relative url of the folder, eg. "/Library/FolderName"

 

 

Examples

 

Get all files from a folder and their properties
Get-SPOFolderFiles -Username trial@trialtrial123.onmicrosoft.com -Url https://trialtrial123.sharepoint.com -AdminPassword Pass -ServerRelativeUrl "/chc1/fff" 



 

 

 

 

Get all files from a folder and list their names and dates of creation
Get-SPOFolderFiles -Username trial@trialtrial123.onmicrosoft.com -Url https://trialtrial123.sharepoint.com -AdminPassword Pass -ServerRelativeUrl "/chc1/fff" | select name, timecreated



 

 

 

Get all files from a folder and export their names and dates of creation to a CSV file
Get-SPOFolderFiles -Username trial@trialtrial123.onmicrosoft.com -Url https://trialtrial123.sharepoint.com -AdminPassword Pass -ServerRelativeUrl "/chc1/fff" | select name, timecreated | export-csv c:\filename.csv

 



 

 

 

 

If you want to get all files from all the folders, you can use Get-SPOFolder cmdlet to retrieve the folders and then for each folder retrieve the files.

 

 

 

Requirements

 

The following libraries (SharePoint Online SDK) are required. If those libraries are in different location on your computer, please edit the .psm1 file!

 

PowerShell
# Paths to SDK. Please verify location on your computer.    
Add-Type -Path "c:\Program Files\Common Files\microsoft shared\Web Server Extensions\15\ISAPI\Microsoft.SharePoint.Client.dll"     
Add-Type -Path "c:\Program Files\Common Files\microsoft shared\Web Server Extensions\15\ISAPI\Microsoft.SharePoint.Client.Runtime.dll" 
 
Under Windows Server 2012 R2 you may need to use:

<C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI>

 

 

 

 

 

Let me know about your experience in the Q&A section!
