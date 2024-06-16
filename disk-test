#!/bin/bash

# Check if the script is run as sudo
if [ "$EUID" -ne 0 ]; then 
  echo "Please run this script as sudo to avoid entering the password in the middle of the test."
  exit 1
fi

# Check if folder name is provided
if [ -z "$1" ]; then
  echo "Usage: $0 <folder_name>"
  exit 1
fi

# Assign folder name to a variable
FOLDER=$1

# Create the folder if it doesn't exist
mkdir -p $FOLDER

# Start time
START_TIME=$(date +%s)

# Clear the cache
echo "Clearing cache..."
sudo sh -c "/usr/bin/echo 3 > /proc/sys/vm/drop_caches"

# Perform disk test
echo "Starting disk test in folder: $FOLDER"
echo "Writing test..."
dd if=/dev/zero of=$FOLDER/testfile bs=1M count=1024 conv=fdatasync

# Clear the cache again before reading
echo "Clearing cache again..."
sudo sh -c "/usr/bin/echo 3 > /proc/sys/vm/drop_caches"

echo "Reading test..."
dd if=$FOLDER/testfile of=/dev/null bs=1M count=1024

# End time
END_TIME=$(date +%s)

# Calculate elapsed time
ELAPSED_TIME=$((END_TIME - START_TIME))

# Show testing summary
echo "Disk test completed."
echo "Elapsed time: $ELAPSED_TIME seconds"

# Clean up
rm -f $FOLDER/testfile
echo "Temporary files deleted."

exit 0
