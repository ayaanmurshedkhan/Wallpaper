1. Write a shell program that takes a number from user and prints the reverse of the number.

#!/bin/bash

# Read number from the user
echo "Enter a number:"
read number

# Reverse the number using a loop
reverse=0
while [ $number -gt 0 ]
do
    remainder=$(( number % 10 ))
    reverse=$(( reverse * 10 + remainder ))
    number=$(( number / 10 ))
done

# Output the reversed number
echo "Reversed Number: $reverse"


2. Write a shell script to determine whether two numbers input through keyboard are prime to each other.

#!/bin/bash

# Function to compute GCD using Euclidean algorithm
gcd() {
    a=$1
    b=$2
    while [ $b -ne 0 ]; do
        temp=$b
        b=$(( a % b ))
        a=$temp
    done
    echo $a
}

# Read two numbers from the user
echo "Enter first number:"
read num1
echo "Enter second number:"
read num2

# Calculate GCD
gcd_result=$(gcd $num1 $num2)

# Check if GCD is 1
if [ $gcd_result -eq 1 ]; then
    echo "The numbers $num1 and $num2 are co-prime."
else
    echo "The numbers $num1 and $num2 are not co-prime."
fi


3. Write a shell script to find whether a number is divisible by 11.

#!/bin/bash

# Read number from user
echo "Enter a number:"
read number

# Check divisibility by 11
if [ $(( number % 11 )) -eq 0 ]; then
    echo "The number $number is divisible by 11."
else
    echo "The number $number is not divisible by 11."
fi


4. Write a shell script that produces a shell calculator to perform the following operations:
   1. Addition
   2. Subtraction
   3. Multiplication
   4. Division

#!/bin/bash

# Function to perform the arithmetic operations
calculator() {
    case $2 in
        "+")
            echo "$(($1 + $3))"
            ;;
        "-")
            echo "$(($1 - $3))"
            ;;
        "*")
            echo "$(($1 * $3))"
            ;;
        "/")
            if [ $3 -ne 0 ]; then
                echo "$(($1 / $3))"
            else
                echo "Division by zero is not allowed."
            fi
            ;;
        *)
            echo "Invalid operation."
            ;;
    esac
}

# Read two numbers and an operation from user
echo "Enter first number:"
read num1
echo "Enter second number:"
read num2
echo "Enter the operation (+, -, *, /):"
read operation

# Perform the operation
result=$(calculator $num1 $operation $num2)
echo "Result: $result"







1. Write a shell script that displays a list of all files in the current directory to which you have read, write and execute permissions.

#!/bin/bash

# List all files in the current directory with read, write, and execute permissions for the user
echo "Files with read, write, and execute permissions for the user:"
for file in *; do
    if [ -r "$file" ] && [ -w "$file" ] && [ -x "$file" ]; then
        echo "$file"
    fi
done


2. Write a shell script that lists files by modification time when called with lm and by access time when called with la. By default, the script should show the listing of all files in the current directory.

#!/bin/bash

# Check the argument provided to the script
if [ "$1" == "lm" ]; then
    # List files sorted by modification time (newest first)
    echo "Listing files by modification time:"
    ls -lt
elif [ "$1" == "la" ]; then
    # List files sorted by access time (newest first)
    echo "Listing files by access time:"
    ls -lu
else
    # Default: List all files in the current directory
    echo "Listing all files in the current directory:"
    ls
fi


3. Write a shell script to display the files created or updated within fourteen days from the current date.

#!/bin/bash

# Find and display files in the current directory modified within the last 14 days
echo "Files modified within the last 14 days:"
find . -type f -mtime -14


4. Develop a shell script which displays all files with all attributes those have been created or modified in the month of November.

#!/bin/bash

# Display all files created or modified in the month of November
echo "Files created or modified in November:"
find . -type f -newermt "2023-11-01" ! -newermt "2023-12-01" -ls






1. Write a shell script, which reports names and sizes of all files in a directory (directory should be supplied as an argument to the shell script) whose size exceeds 100 bytes. The filenames should be printed in decreasing order of their sizes. The total number of such files should also be reported.

#!/bin/bash

# Check if the directory is supplied as an argument
if [ $# -ne 1 ]; then
    echo "Usage: $0 directory"
    exit 1
fi

directory=$1

# Check if the supplied argument is a directory
if [ ! -d "$directory" ]; then
    echo "$directory is not a valid directory."
    exit 1
fi

# List files larger than 100 bytes and sort by size in descending order
echo "Files larger than 100 bytes in $directory:"
files=$(find "$directory" -type f -size +100c -exec ls -lh {} + | sort -k5 -rh)

# Check if any files were found
if [ -z "$files" ]; then
    echo "No files larger than 100 bytes found."
else
    echo "$files"
    # Count and display the number of such files
    count=$(find "$directory" -type f


2. Write a shell script that shows the names of all the non-directory files in the current directory and calculates the sum of the size of them.

#!/bin/bash

# Initialize total size
total_size=0

# List non-directory files and calculate total size
echo "Non-directory files in the current directory:"
for file in *; do
    if [ -f "$file" ]; then
        file_size=$(stat -c%s "$file")
        echo "$file: $file_size bytes"
        total_size=$((total_size + file_size))
    fi
done

# Display the total size
echo "Total size of non-directory files: $total_size bytes"


3. Write a shell script to list the name of files under the current directory that starts with a vowel.

#!/bin/bash

# List files that start with a vowel in the current directory
echo "Files starting with a vowel:"
for file in [AaEeIiOoUu]*; do
    if [ -f "$file" ]; then
        echo "$file"
    fi
done


4. Write a shell script which receives two filenames as arguments and checks whether the two file‟s contents are same or not. If they are same then the second file should be deleted.

#!/bin/bash

# Check if exactly two filenames are supplied as arguments
if [ $# -ne 2 ]; then
    echo "Usage: $0 file1 file2"
    exit 1
fi

file1=$1
file2=$2

# Check if both files exist
if [ ! -f "$file1" ] || [ ! -f "$file2" ]; then
    echo "Both files must exist."
    exit 1
fi

# Compare the contents of the two files
if cmp -s "$file1" "$file2"; then
    echo "Files '$file1' and '$file2' have the same content. Deleting '$file2'."
    rm "$file2"
else
    echo "Files '$file1' and '$file2' are different."
fi






1. A file called list consists of several words. Write a shell script which will receive a list of filenames, the first of which would be list. The shell script should report all occurrences of each word in list in the rest of the files supplied as arguments.

#!/bin/bash

# Check if at least two files are provided (list file and other files)
if [ $# -lt 2 ]; then
    echo "Usage: $0 list file1 [file2 ...]"
    exit 1
fi

# First file is assumed to be the 'list' file
list_file=$1
shift  # Remove 'list' file from arguments, rest are the other files

# Check if list file exists
if [ ! -f "$list_file" ]; then
    echo "List file '$list_file' does not exist."
    exit 1
fi

# Read each word from 'list' and search in the provided files
while read -r word; do
    echo "Occurrences of the word '$word':"
    grep -w -n "$word" "$@"
    echo "----------------------------"
done < "$list_file"


2. Write a shell script which deletes all lines containing the word UNIX in the files supplied as arguments to this shell script.

#!/bin/bash

# Check if at least one file is provided
if [ $# -lt 1 ]; then
    echo "Usage: $0 file1 [file2 ...]"
    exit 1
fi

# Iterate over each file and delete lines containing "UNIX"
for file in "$@"; do
    if [ -f "$file" ]; then
        sed -i '/UNIX/d' "$file"
        echo "Deleted lines containing 'UNIX' from $file"
    else
        echo "File '$file' does not exist."
    fi
done


3. Write a shell script which would receive a log name during execution, obtain information about it from password file and display this information on the screen in easily understandable format.

#!/bin/bash

# Check if a log name (username) is provided
if [ $# -ne 1 ]; then
    echo "Usage: $0 username"
    exit 1
fi

username=$1

# Use the `getent` command to get user info from /etc/passwd
user_info=$(getent passwd "$username")

# Check if the user exists
if [ -z "$user_info" ]; then
    echo "User '$username' not found."
    exit 1
fi

# Extract information
IFS=":" read -r uname passwd uid gid desc home shell <<< "$user_info"

# Display information in an easily understandable format
echo "User Information for $username:"
echo "---------------------------------"
echo "Username     : $uname"
echo "User ID (UID): $uid"
echo "Group ID (GID): $gid"
echo "Description  : $desc"
echo "Home Directory: $home"
echo "Shell        : $shell"


4. Write a shell script, which will receive either the filename or the filename with its full path during execution. This script should print information about the file as given by ls –l command and display it in an informative manner.

#!/bin/bash

# Check if a filename is provided
if [ $# -ne 1 ]; then
    echo "Usage: $0 filename"
    exit 1
fi

file=$1

# Check if the file exists
if [ ! -e "$file" ]; then
    echo "File '$file' does not exist."
    exit 1
fi

# Get detailed information using ls -l
file_info=$(ls -l "$file")

# Extract specific attributes from ls output
permissions=$(echo "$file_info" | awk '{print $1}')
links=$(echo "$file_info" | awk '{print $2}')
owner=$(echo "$file_info" | awk '{print $3}')
group=$(echo "$file_info" | awk '{print $4}')
size=$(echo "$file_info" | awk '{print $5}')
date=$(echo "$file_info" | awk '{print $6, $7, $8}')
filename=$(echo "$file_info" | awk '{print $9}')

# Display the information in a user-friendly format
echo "File Information for $file:"
echo "----------------------------"
echo "Filename     : $filename"
echo "Permissions  : $permissions"
echo "Links        : $links"
echo "Owner        : $owner"
echo "Group        : $group"
echo "Size         : $size bytes"
echo "Last Modified: $date"
