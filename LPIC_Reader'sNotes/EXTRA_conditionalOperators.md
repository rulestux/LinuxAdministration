## Bash Conditional Test Operators

| Category | Operator | Test Description | Example | Returns True When |
|----------|----------|-----------------|---------|-------------------|
| **String Tests** | <b>-n</b> | String is non-empty | <b>[[ -n "$var" ]]</b> | String has length > 0 |
| | <b>-z</b> | String is empty | <b>[[ -z "$var" ]]</b> | String length is 0 |
| | <b>=</b> | Strings are equal | <b>[[ "$a" = "$b" ]]</b> | Strings match exactly |
| | <b>!=</b> | Strings are not equal | <b>[[ "$a" != "$b" ]]</b> | Strings differ |
| | <b>==</b> | String matches pattern | <b>[[ "$file" == *.txt ]]</b> | Matches wildcard pattern |
| **Numeric Comparisons** | <b>-eq</b> | Equal to | <b>[[ 5 -eq 5 ]]</b> | Numerically equal |
| | <b>-ne</b> | Not equal | <b>[[ 5 -ne 6 ]]</b> | Numerically different |
| | <b>-lt</b> | Less than | <b>[[ 4 -lt 5 ]]</b> | Left is less than right |
| | <b>-le</b> | Less than or equal | <b>[[ 5 -le 5 ]]</b> | Left <= right |
| | <b>-gt</b> | Greater than | <b>[[ 6 -gt 5 ]]</b> | Left is greater than right |
| | <b>-ge</b> | Greater than or equal | <b>[[ 5 -ge 5 ]]</b> | Left >= right |
| **File Tests** | <b>-d</b> | Is directory | <b>[[ -d /home ]]</b> | Path is a directory |
| | <b>-f</b> | Is regular file | <b>[[ -f file.txt ]]</b> | Path is a regular file |
| | <b>-e</b> | File exists | <b>[[ -e file.txt ]]</b> | File or directory exists |
| | <b>-r</b> | File is readable | <b>[[ -r file.txt ]]</b> | File has read permission |
| | <b>-w</b> | File is writable | <b>[[ -w file.txt ]]</b> | File has write permission |
| | <b>-x</b> | File is executable | <b>[[ -x script.sh ]]</b> | File has execute permission |
| | <b>-L</b> | Is symbolic link | <b>[[ -L symlink ]]</b> | Path is a symbolic link |
| **Logical Operators** | <b>&&</b> | AND | <b>[[ -f file && -r file ]]</b> | Both conditions true |
| | <b>\|\|</b> | OR | <b>[[ -d dir \|\| -f file ]]</b> | At least one true |
| | <b>!</b> | NOT | <b>[[ ! -d dir ]]</b> | Inverts the test |

### Pro Tips
- <b>Use [[ ]] for modern bash scripts</b>
- <b>Prefer [[ ]] over [ ] for more features</b>
- <b>Always quote variables to prevent word splitting</b>

### Common Pitfalls
- Unquoted variables can cause unexpected behavior
- Some tests work differently in <b>[ ]</b> vs <b>[[ ]]</b>

### Best Practices
```bash
# Good: Quoted variables
if [[ -n "$variable" ]]; then
    echo "Variable is set"
fi

# Avoid: Unquoted variables
if [ -n $variable ]; then  # Potential issue
    echo "Risky test"
fi
```