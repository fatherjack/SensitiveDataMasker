# SensitiveDataMasker

## Description

PowerShell script to parse a directory of files and replace sensitive content with a generic string, providing a mapping between sensitive string and replacement string so that technical advice can refer to a generic value eg 'Server1' and the original server name can be identified.

## Process

- step 1 - set up SensitiveStrings.txt as list of what needs removing
- step 2 - adjust the reference in the script to the location where the above txt file is
- step 3 - run the code to build the function
- step 4 - execute the function supplying the directory where the log files are stored

### What types of data are in scope

Currently the script recognises data that represents the following objects

- "Server"
- "Account"
- "IP"
- "System"
- "URL"
- "Database"
- "Domain"  

### Caveats

- If the supplied string is part of a larger (non-sensitive) string it will be replaced in all contexts.
- If the replacement (non-sensitive) string is already a string that is found in the original file then searching for the replacement string will result 
in finding occurrences that represent the places where the sensitive content was replaced as well as the places where the original file already contained the non-sensitive value.



### Examples

````powershell
Assert-DataMask C:\Temp\TVP\Destination

# This will mask all sensitive values in files found in the specified directory
````

````text
SensitiveValues.txt 

ItemValue, ItemType, Mask
Ultron, System,
127.0.0.1, IP,
Jarvis, Server,
Adventureworks, Database,
www.contoso.com, url,
````
