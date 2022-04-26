# PowerShell Refresher<a name="top"></a>

This is a minimalistic refresher for PowerShell syntax. It is meant for occasional users of the language who only need to get back into the language periodically. 

**Contents**:
[Variables](#Variables) | [Strings](#Strings) | [Arrays](#Arrays) | [Hashtables](#Hashtables)
[Branching](#Branching) | [Looping](#Looping) | [Operators](#Operators) | [Output](#Output)
[Functions](#Functions) | [Scripts](#Scripts) | [Comments](#Comments)

## Variables
```powershell
$number = 1              # Variables start with a dollar sign
$string = "Hello World"; # Semicolons are optional
$output = ls             # Captures the output of command 'ls'
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
-and -or   # And, Or
-eq -ne    # Equal to, Not equal to
-gt -lt    # Greater than, Less than
-ge        # Greater than or equal
-le        # Less than or equal
-xor       # Exclusive or
-contains  # Test if array has item
-match     # Compare against regex
```

## Output
```powershell
echo "display $value in console"

# Output to file and overwrite that file
$value > overwritten_file.txt

# Output to file and append to end of file
$value >> appended_file.txt

# Pipe output to command ‘program’
$value | program 
```

## Functions
```powershell
function work([int]$value){
   return "$value as string"
}

work 42 # Call function
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
