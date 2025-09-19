#!/mnt/sudo/bash

# Check the number of arguments
if [ "$#" -ne 1 ]; then
    echo "Please pass exactly one argument to /challenge/run"
    exit 1
fi

# Check if the argument is Muelsyse
if [ "$1" != "Muelsyse" ]; then
    echo "The only accepted argument is: Muelsyse"
    exit 1
fi

# Check the current working directory
if [ "$(pwd)" != "/challenge/.robin" ]; then
    echo "You must be in the /challenge/.robin directory to run this script"
    exit 1
fi

# Check if /challenge/challenge_tmp/directory folder exists
if [ ! -d "/challenge/challenge_tmp/directory" ]; then
    echo "Missing directory: /challenge/challenge_tmp/directory"
    exit 1
fi

echo "Correct! /challenge/challenge_tmp/directory detected and argument is valid."
cat /flag