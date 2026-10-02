# Windows Users & Permissions

## Objective

Learn how to create local Windows users, understand administrator vs standard accounts, and control access to files and folders using permissions.

## Local User Account Management

### `net user labuser /add`

**Purpose:** Creates and new local Windows user account.  
**Result:** Created a local standard user named `labuser`.

### `net user labuser`

**Purpose:** Displays information about the local user account.  
**Result:** Reviewed the account information for `labuser`.

### `net localgroup administrators`

**Purpose:** Displays the local accounts that have administrator access.  
**Result:** `labuser` was not listed in the Administrators group, confirming that it is a standard user account.

## File and Folder Permissions

### File and Folder Permissions

**Purpose:** Controls which users and groups can access, modify, or manage files and folders.  
**Result:** Opened the Security settings for the `AdminOnly` folder to review existing permissions.

### NTFS Folder Permissions

**Purpose:** Controls what specific users can do with files and folders.  
**Result:** Added `labuser` and granted read-only permissions without Modify or Full Control.

## Permission Testing

### Test 1

**Test:** Created `Testfile.txt` inside the `AdminOnly` folder while logged in as `labadmin`.  
**Purpose:** Test whether the standard user `labuser` can read the file but cannot modify it.

### Test 2

**Test:** Logged in as `labuser` and attempted to modify `TestFile.txt`.  
**Result:** `labuser` could open and read the file but could not save changes because the account only had read permissions.

### What I Learned

NTFS permissions can restrict a user to read-only access. I also learned that permissions can come from group memberships, so a user may have more access than their individual permissions show.

## Administrator Group Management

### `net localgroup administrators labuser /add`

**Purpose:** Adds a local user to the Administrators group.  
**Result:** `labuser` was successfully added to the local Administrators group.

### `net localgroup administrators`

**Purpose:** Displays members of the local Administrators group.  
**Result:** Verified that `labuser` was listed as an administrator.

### `net localgroup administrators labuser /delete`

**Purpose:** Removes a local user from the Administrators group.  
**Result:** `labuser` was successfully removed from the Administrators group.

### `net localgroup administrators`

**Purpose:** Verifies current members of the local Administrators group.  
**Result:** Confirmed that `labuser` was no longer an administrator.

## What I Learned

I learned how to create and manage local Windows user accounts, identify standard and administrator accounts, configure NTFS permissions, test read-only access, troubleshoot inherited group permissions, and manage membership in the local Administrators group.
