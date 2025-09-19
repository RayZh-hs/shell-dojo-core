#!/mnt/sudo/bash

# Check argument count
if [ "$#" -ne 1 ]; then
    echo "Please pass exactly one arg to /challenge/run: filesystem"
    echo "eg. /challenge/run filesystem"
    exit 1
fi

# The required argument value
if [ "$1" != "filesystem" ]; then
    echo "The only accepted argument is: filesystem"
    exit 1
fi

# Check current working directory
if [ "$(pwd)" != "/challenge/.robin" ]; then
    echo "You must be in /challenge/.robin to run this script"
    exit 1
fi

# Check for /challenge/.robin/to_cp
if [ ! -e "/challenge/.robin/to_cp" ]; then
    echo "Missing: /challenge/.robin/to_cp"
    exit 1
fi

# Check for /challenge/directory/cp_end/to_cp
if [ ! -e "/challenge/challenge_tmp/directory/cp_end/to_cp" ]; then
    echo "Missing: /challenge/challenge_tmp/directory/cp_end/to_cp"
    exit 1
fi

# Check for /challenge/directory/mv_end/to_mv
if [ ! -e "/challenge/challenge_tmp/directory/mv_end/to_mv" ]; then
    echo "Missing: /challenge/challenge_tmp/directory/mv_end/to_mv"
    exit 1
fi

# Ensure /challenge/.robin does NOT contain to_mv
if [ -e "/challenge/.robin/to_mv" ]; then
    echo "/challenge/.robin should NOT contain to_mv"
    exit 1
fi

# Ensure /challenge/.robin does NOT contain to_delete
if [ -e "/challenge/.robin/to_delete" ]; then
    echo "/challenge/.robin should NOT contain to_delete"
    exit 1
fi

echo "Correct! Filesystem layout matches requirements."
cat /flag