This is a crash course for PowerShell syntax. It serves as a minimalistic refresher for occasional users of the language. 

[Variables](#Variables) | [Strings](#Strings) | [Arrays](#Arrays) | [Hashtables](#Hashtables) |
[Branching](#Branching) | [Looping](#Looping) | [Operators](#Operators) | [Input](#Input) | [Output](#Output) |
[Functions](#Functions) | [Scripts](#Scripts) | [Comments](#Comments)

## Variables
```powershell
$example = "World"      # Variable names start with a dollar sign
$digits  = 12345;       # Semicolons are optional for single statements
$output  = Get-Location # You can capture the output of commands in a variable
```

## Strings
```powershell
$example = "World"        # Declares new string variable

"Hello $example"          # Evaluates to Hello World
'Hello $example'          # Evaluates to Hello $example
"Hello" + "World"         # Evaluates to HelloWorld

$example.StartsWith("W")  # Evaluates to true
$example.Contains("or")   # Evaluates to true
$example.EndsWith("ld")   # Evaluates to true

$example.Substring(0, 2)  # Evaluates to Wo
$example.Replace("l","")  # Evaluates to Word
```

## Arrays
```powershell
$items = @()             # Initializes empty array
$items = $items + "A"    # Array now contains A
$items += "B"            # Array now contains A, B

$other = @("C","D","E")  # Initialize a non-empty array
$items = $items + $other # Array now contains A, B, C, D, E
 
$items[4]                # Returns E
$items[0..2]             # Returns A, B, C
$items.Length            # Returns 5
```

## Hashtables
```powershell
$table = @{}              # Initializes empty hashtable
$table.Planet = 'Earth'   # Defines new key-value pair 
$table['Fruit'] = 'Apple' # Also defines new key-value pair

$table.Keys               # Returns Planet, Fruit
$table.Values             # Returns Earth, Apple
$table.Count              # Returns 2
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
for ($i = 0; $i -lt 3; $i += 1) {
   echo $i
}

foreach ($item in $array) {
   echo $item
}

while ($number -ne 0) {
   $number -= 1
}

```

## Operators
```powershell
-not       # Negation
-and       # Logical And
-or        # Logical Or
-eq        # Equal to
-ne        # Not equal to
-gt        # Greater than
-lt        # Less than
-ge        # Greater than or equal
-le        # Less than or equal
-xor       # Exclusive or
-contains  # Test if array has item
-match     # Compare against regex
```
## Input
```powershell
# Captures user input as a string
$name = Read-Host 

# Presents a prompt when capturing user input
$realname = Read-Host "What is your actual name?"

# Reads the specified file to a variable
$file = Get-Content "notes.txt"

# This Unix-like alias also works
$file = cat "notes.txt

```

## Output
```powershell
# Writes a string to the console
Write-Host "Hello $name"

# This Unix-like alias also works
echo "Hello $realname"

# Outputs variable to file, overwriting it
$name > notes.txt

# Appends variable to end of file
$realname >> notes.txt

# Pipe output to command ‘program’
$name | program 
```

## Functions
```powershell
function DoWork {
   param($Name)
   return "Hello $Name"
}

DoWork                # Returns "Hello "
DoWork -Name "World"  # Returns "Hello World"
DoWork "World"        # Also returns "Hello World"
```

## Scripts
```powershell
$script = "/Path/To/Script.ps1"

# call script
& $script $arg1 $arg2 

# $args is an implicit array in
# every script containing arguments
```

## Comments
```powershell
# single line comment
<#
   This is a multi-line
   comment block
#>
```

## Notes
This was originally published on my [personal site](https://turtlesort.com/) in 2013.
