# ClearCase Guide

## Introduction

IBM Rational ClearCase is a version control system that manages source code and other software development assets. It provides branching, merging, and configuration management capabilities.

## Basic Concepts

- **VOB (Versioned Object Base)**: Repository storing files, directories, and metadata.
- **View**: Workspace that provides a dynamic or snapshot access to files.
- **Config Spec**: Rules that define file versions in a view.
- **Checkout/Checkin**: Process of editing and saving changes in ClearCase.

## Setting Up ClearCase

### Starting the ClearCase Service (Linux/Unix)

```sh
cleartool startup
```

### Starting ClearCase on Windows

```sh
net start Atria
```

## Working with Views

### Creating a View

#### Dynamic View:

```sh
cleartool mkview -tag my_dynamic_view /path/to/storage
```

#### Snapshot View:

```sh
cleartool mkview -snapshot -tag my_snapshot_view /path/to/storage
```

### Activating a View

```sh
cleartool setview my_dynamic_view
```

## Checking Out and Checking In Files

### Checkout a File

```sh
cleartool checkout -c "Fixing bug" filename
```

### Edit the File, then Check In

```sh
cleartool checkin -c "Bug fixed" filename
```

### Cancel Checkout

```sh
cleartool uncheckout filename
```

## Version History

### Viewing File History

```sh
cleartool lshistory filename
```

### Comparing Versions

```sh
diff -u old_version new_version
```

## Branching

### Creating a Branch

```sh
cleartool mkbranch branch_name filename
```

### Switching to a Branch

Modify the config spec:

```sh
element * CHECKEDOUT
element * .../branch_name/LATEST
element * /main/LATEST -mkbranch branch_name
```

Apply the config spec:

```sh
cleartool setcs -current
```

## Merging Changes

### Find Merge Candidates

```sh
cleartool findmerge . -fversion /main/LATEST -print
```

### Perform a Merge

```sh
cleartool merge -to filename -version /main/LATEST
```

### Resolve Conflicts

Use a text editor or GUI tools to manually resolve conflicts.

## Managing Views

### List Active Views

```sh
cleartool lsview
```

### Remove a View

```sh
cleartool rmview -tag view_name
```

---

## Additional Resources

- [IBM ClearCase Documentation](https://www.ibm.com/docs/en/rational-clearcase)
- [ClearCase Commands Reference](https://www.ibm.com/docs/en/rational-clearcase/9.0.1?topic=commands)

---
## Conclusion

ClearCase is a powerful tool for version control in enterprise environments. By mastering its workflows, teams can effectively manage and track software changes.
