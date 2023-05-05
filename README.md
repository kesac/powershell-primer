# PowerShell Refresher<a name="top"></a>

This is a minimalistic refresher for PowerShell syntax. It is meant for occasional users of the language who only need to get back into the language periodically. 

[Variables](#Variables) | [Strings](#Strings) | [Arrays](#Arrays) | [Hashtables](#Hashtables) |
[Branching](#Branching) | [Looping](#Looping) | [Operators](#Operators) | [Input](#Input) | [Output](#Output) |
[Functions](#Functions) | [Scripts](#Scripts) | [Comments](#Comments)

All example code will execute as-is.

## Variables
```powershell
$string = "Hello World";  # Variables start with a dollar sign
$number = 12345           # And semicolons are optional


# You can assign the output of Powershell 
# commands directly to a variable
$output = Get-Location
```

## Strings
```powershell
$name = "World"
"Hello $name"            # "Hello World"
'Hello $name'            # "Hello $name"
"Hello" + "World"        # "HelloWorld"

"World".Substring(0, 2)  # Returns "Wo"
"World".substring(2)     # Method names are not case-sensitive. Returns "rld" 
"World".Replace("l","")  # Returns "Word"
"$(2 + 5 * 8)"           # Returns "42"
```

## Arrays
```powershell
$array = @()             # Initialize an empty array
$array = $array + "A"    # Array now contains element "A"
$array += "B"            # Array now contains elements "A" and "B"

$other = @("C","D","E")
$array = $array + $other # Array now contains five elements
 
$array[4]                # Gets single value
$array[1..4]             # Gets subset
$array.Length            # Gets size of array
```

## Hashtables
```powershell
$table = @{}             # Initialize an empty hashtable
$table.planet = 'Earth'
$table['fruit'] = 'apple'
$table.Keys              # Gets all keys
$table.Values            # Gets all values
$table.Count             # Size of table
```

## Branching
```powershell
if(-not $table){
   echo "table is not defined"
}
elseif($table[$key]){
   echo "$key is defined in table"
}
else{
   echo "$key is not defined"
}
```

## Looping
```powershell
for($i = 1; $i -lt 3; $i += 1){
   echo $i
}
foreach($item in $array){
   echo $item
}
while($number -ne 0){
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
