> ❗ This document is a work in progress

## Overview
This is a primer for extracting, transforming, and processing data inside flat files using PowerShell. It is meant for casual users of PowerShell who have had exposure to the language before.

## Checking if a Folder/File Exists
```powershell
Test-Path "/Folder/"          # Returns true if the folder exists
Test-Path "/Folder/Data.txt"  # Returns true if the file exists

if (Test-Path "/Folder/Data.txt") {
    # Do something if the file exists
}
```

## Checking Folder Contents
```powershell
# Get contents of a folder as an array 
$items      = Get-ChildItem "/Folder/" 

# Separate files from subfolders
$subfolders = $items | Where-Object { $_.PSIsContainer }
$files      = $items | Where-Object { -not $_.PSIsContainer }

# Shorthand form of above to get files in a folder
$files      = ls "/Folder/" | ? { !$_.PSIsContainer }
```

## Processing a Text File
Pretend a `data.txt` file contains the following:
```
Fruit:Apple:Red:1205781234
Fruit:Banana:Yellow:1506777267
Fruit:Grape:Purple:1873161441
Fruit:Mango:Yellow:1628450950
```

You can extract all the color values in the file by doing the following:
```powershell
$colors = @()

Get-Content "data.txt" | ForEach-Object {
	$tokens = $_.Split(':')   # $_ is the current line of text    
	$colors += $tokens[2] 
}

# Get unique colors in text file
$unique = $colors | Select -Unique
```

Or as a one-liner using aliases:
```powershell
cat "data.txt" | % { $_.Split(':')[2] } | Select -Unique
```

## Processing a CSV File
Pretend a `data.csv` file contains the following:
```
"Type","Name","Color","Id"
"Fruit","Apple","Red","1205781234"
"Fruit","Banana","Yellow","1506777267"
"Fruit","Grape","Purple","1873161441"
"Fruit","Mango","Yellow","1628450950"
```

You can extract the unique color values in the file by doing the following:
```powershell
$colors = Get-Content "data.csv" | ConvertFrom-Csv | Select Color -Unique
```

## Processing a JSON file
Pretend a `data.json` file contains the following:
```
{
  "Fruit": [
    {
      "Id": "1205781234",
      "Name": "Apple",
      "Color": "Red"
    },
    {
      "Id": "1506777267",
      "Name": "Banana",
      "Color": "Yellow"
    },
    {
      "Id": "1873161441",
      "Name": "Grape",
      "Color": "Purple"
    },
    {
      "Id": "1628450950",
      "Name": "Mango",
      "Color": "Yellow"
    }
  ]
}
```

You can extract the unique color values in the file by doing the following:
```powershell
$colors = Get-Content "data.json" | ConvertFrom-Json | Select Color -Unique
```

## Finding a String Inside a File
```powershell
# Find all occurrences of "substring" inside a data file
Select-String "data.txt" -Pattern "substring"

# You can pipe text into the command, but it won't show the line number
Get-Content "data.txt" | Select-String "substring"
```

## Finding a String in a Folder and all its Subdirectories
```powershell
$items   = Get-ChildItem  "/Folder/" -Recurse
$files   = $items | Where-Object { -not $_.PSIsContainer }
$result  = $files | Select-String -Pattern "substring"
```

Or as a one-liner:
```powershell
ls "/Folder/" -r | ? { !$_.PSIsContainer } | Select-String "substring"
```

## Using Hashtables as Pseudo Objects
If your data file is not in JSON or CSV format, you can load them in as hashtables 
```powershell
# Basically, creating hashtables of hashtables
# Converting hashtables to JSON or CSV
```

## Using custom .NET objects
```powershell
# Instantiating an object
# Converting a hashtable into an object
```

## Detecting duplicate IDs in a TXT/CSV/JSON file
```powershell
# Using a hashtable to detect key collisions to detect dupes
```

## Writing arrays and hashtables to disk
```powershell
# Using a hashtable to detect key collisions to detect dupes
```

## Advanced
```powershell
- Advanced
	- Working with JSON
	- Working with XML (processing node-by node)
	- Working with HTML (ConvertTo-Html)
	- Outputting to ASCII
	- Using -f for formatting
```
> ❗ This document is a work in progress
