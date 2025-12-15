# Clean up disk space
```bash
# Check disk space
df -h

# Disk usage of every file + folder in directory
du -sh * .[!.]* 2>/dev/null | sort -h

# Usual suspects
rm -rf ~/.vscode-server
rm -rf ~/.cache/*
rm -rf node_modules # run from inside each project
```