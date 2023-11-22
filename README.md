## Contents
This is a crash course for using PowerShell. It serves as a refresher for occasional users of the language. 

[Quick Start](#Quick-Start)  | [Variables](#Variables) | [Strings](#Strings) | [Arrays](#Arrays) | [Hashtables](#Hashtables) | [Input](#Input) | [Output](#Output) |
[Basic Operators](#Basic-Operators) | [Branching](#Branching) | [Looping](#Looping) | 
[Functions](#Functions) | [Scripts](#Scripts) | [Comments](#Comments)

## Quick Start
To access PowerShell:
- Run the _Windows PowerShell_ app for a command line interface 
- Or launch _Windows PowerShell ISE_ for an editor

## Variables
```powershell
$example = "World";       # Variable names start with $
$digits  = 12345          # Semicolons are optional
$output  = Get-Help       # Variables also store the output of commands
```

## Strings
```powershell
# Initialization
$example = "World"        # Quotes make strings
$example = 'World'        # Single quotes make strings too

"Hello $example"          # This becomes 'Hello World'
'Hello $example'          # But this stays as 'Hello $example'

# Operations
"Hello" + $example        # Use '+' to join strings
$example.Substring(0, 2)  # Strings have methods. This returns 'Wo'
$example.Replace("l","")  # And this returns 'Word'

# Comparison
$example.StartsWith("W")  # Returns true
$example.Contains("or")   # Returns true too
$example.EndsWith("ld")   # Returns true as well
```

## Arrays
```powershell
# Initialization
$items = @()              # Creates an empty array
$stock = @("C","D","E")   # Creates an array with existing elements
$stock.Length             # Returns 3
$stock[0]                 # Returns 'C'

# Operations
$items = $items + "A"     # This adds 'A' to the empty array
$items += "B"             # This adds 'B'
$items += $stock          # Array now has 'A', 'B', 'C', 'D', 'E'
$items -contains "C"      # Returns true
```

## Hashtables
```powershell
# Initialization
$table = @{}               # Creates an empty hashtable
$table.Planet = 'Earth'    # Adds a key-value pair 
$table['Dog'] = 'Corgi'    # Also adds a key-value pair

$table = @{                # Creates a hashtable with existing items
    Planet = 'Earth';      # Semicolons are needed to separate items here
    Dog    = 'Corgi';
}

# Properties
$table.Keys                # Returns Planet, Dog
$table.Values              # Returns Earth, Corgi
$table.Count               # Returns 2
$table.ContainsKey('Dog')  # Returns true
```

## Input
```powershell
$data = Read-Host              # Captures user input
$data = Get-Content notes.txt  # Captures contents of a file
$data = cat notes.txt          # This Unix-like alias also works
$data = cat "notes.txt"        # Quotes around the filename works too
```

## Output
```powershell
Write-Host $data      # Writes to console
echo $data            # This alias also writes to console
$data >> notes.txt    # Writes to a file, appending to it
$data > notes.txt     # Writes to a file, overwriting it
$data | Some-Command  # Pipes to a PowerShell command
```

## Basic Operators
```powershell
+     # Addition, joining, concatenation
++    # Increment by 1
-     # Subtraction, number negation
--    # Decrement by 1
*     # Multiplication, repeater
/     # Division
%     # Modulo
-not  # Logical negation
-and  # Logical And
-or   # Logical Or
-eq   # Equal to
-ne   # Not equal to
-gt   # Greater than
-lt   # Less than
-ge   # Greater than or equal
-le   # Less than or equal

# Examples
$value = (28 / 2) * 3   # Evaluates to 42 
$value -eq 42           # Returns true
-not ($value -eq 42)    # Returns false
```

## Branching
```powershell
if (-not $table) {
    echo "table is not defined"
}
elseif ($table[$key]) {
    echo "$key is defined in table"
}
else 
    echo "$key is not defined"
}
```

## Looping
```powershell
# The classic for-loop works
for ($i = 0; $i -lt 10; $i++) {
    echo $i
}

# A foreach-loop works for arrays
foreach ($item in $array) {
    echo $item
}

# Classic while-loop also works
while ($number -lt 10) {
    $number++
}

# Less popular do-loop also works
do {
    $number--
} while($number -gt 0)
```

## Functions
```powershell
# Declares a basic function
function Show-Message { 
    echo "Hello World"
}

# Call the function using its name
Show-Message  

# Declares a function with arguments and a return value
function Get-Message {
    param(
        $Greeting,
        $Name
    )         
    return "$Greeting $Name"
}

# Call the function with arguments
Get-Message -Greeting "Hello" -Name "World"

# Using positional arguments also works
Get-Message "Hello" "World"
```

## Scripts
```powershell
# When calling other scripts, you'll need
# to know their location
$script = "/Path/To/Script.ps1"

# Then to call the script use the & operator
& $script $arg1 $arg2 
```

## Comments
```powershell
# This is a single line comment.
# And here is another single line comment.

<#
   This is a multi-line comment block.
   Everything inside this block will
   be ignored!
#>
```

## Notes
This was originally published on my [personal site](https://turtlesort.com/) in 2013. Last updated November 2023.
