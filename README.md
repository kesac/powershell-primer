# Overview
- This is a primer for casual users of PowerShell
- It serves as a refresher for basic syntax
- Reading time is 60 seconds or less
---
### Contents
- 🚀 [1.Variables](#Variables) | [2.Strings](#Strings) | [3.Arrays](#Arrays) | [4.Hashtables](#Hashtables) 
- 💬 [5.Input](#Input) | [6.Output](#Output)
- 🔢 [7.Basic Operators](#Basic-Operators) | [8.Branching](#Branching) | [9.Looping](#Looping) 
- 🛠 [10.Functions](#Functions) | [11.Scripts](#Scripts) | [12.Comments](#Comments)

---
### 1. Variables
```powershell
$example = "World";       # Variable names start with $
$digits  = 12345          # Semicolons are optional
$output  = Get-Help       # Variables also store the output of commands
```
---
### 2. Strings
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
---
### 3. Arrays
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
---
### 4. Hashtables
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
---
### 5. Input
```powershell
$data = Read-Host              # Captures user input from console
$data = Get-Content notes.txt  # Captures contents of a file
$data = cat notes.txt          # This Unix-like alias also works
$data = cat "notes.txt"        # Quotes around the filename works too
```
---
### 6. Output
```powershell
Write-Host $data      # Writes to console
echo $data            # This alias also writes to console
$data >> notes.txt    # Writes to a file, appending to it
$data > notes.txt     # Writes to a file, overwriting it
$data | Some-Command  # Pipes to a PowerShell command
```
---
### 7. Basic Operators
```powershell
# The usual math operators exist
$value = (5 + 3) - 1  # Evaluates to 7
$value = (6 / 3) * 2  # Evaluates to 4
$value = 10 % 4       # Evaluates to 2 (modulo)

# Incrementing/decrementing
$value++   # Goes up by 1
$value--   # Goes down by 1

# Operators for equality and boolean logic
$value -gt 0            # True if $value is a positive number
$value -eq 42           # True if $value is 42
!($value -eq 42)    # Negation for previous statement

# Commonly used operators
-and     # Logical And
-or      # Logical Or
-not, !  # Negation
-eq      # Equal to
-ne      # Not equal to
-gt      # Greater than
-lt      # Less than
-ge      # Greater than or equal
-le      # Less than or equal
```
---
### 8. Branching
```powershell
# The usual if-else statements will work, but 
# in this language, 'elseif' has no space in it

if (-not $value) {
    # Executed if $value is not defined
}
elseif (($value % 14) -eq 0) {
    # Executed if $value is divisible by 14
}
else {
    # Executed if no other condition matched
}
```
---
### 9. Looping
```powershell
# This language supports the classic for-loop
# plus the foreach-loop as a bonus

for ($i = 0; $i -lt 10; $i++) {
    echo $i
}

foreach ($item in $array) {
    echo $item
}

# Classic while-loops and do-loops also work

while ($number -lt 10) {
    $number++
}

do {
    $number--
} while($number -gt 0)
```
---
### 10. Functions
```powershell
# Declares a basic function
function Show-Message { 
    echo "Hello World"
}

# Call the function using its name
Show-Message  

# Defines a function with arguments and a return value
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
---
### 11. Scripts
```powershell
# Use the & operator to execute scripts
$script = "/Path/To/Script.ps1" 
& $script

# Like functions, scripts can accept arguments
& $script -Greeting "Hello" -Name "World"
```
---
### 12. Comments
```powershell
# This is a single line comment.
# And here is another single line comment.

<#
   This is a multi-line comment block.
   Everything inside this block will
   be ignored!
#>
```
---
### And you're done!
