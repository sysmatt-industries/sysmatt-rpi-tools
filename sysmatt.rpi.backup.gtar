#!/bin/bash 
# 20140804-1708 Matthew E Hoskins / Twitter: @sysmatt (c) GNU GPL

set -x  # debugging

bomb () {
	echo "BOMB: ${1}"
	exit 1
}

# Default destination directory
DSTDIR=/home/pi/backups
DEFAULT_DFILE="${DSTDIR}/pi.`uname -n`.`date +%Y%m%d%H%M%S`.backup.tar.gz"

# If we get a filename on the command line, use it instead of the default.
DFILE="${1:-$DEFAULT_DFILE}"
DEST_DIR_SANITY=`dirname "${DFILE}"`

# Make sure the destination exists
[ -d "${DEST_DIR_SANITY}" ] || bomb "Destination directory ${DEST_DIR_SANITY} does not exist"

# Run the tar archive
tar --exclude="${DFILE}" --one-file-system -cvzf "${DFILE}" / /boot

echo "Created archive: ${DFILE}"
