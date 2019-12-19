---
layout: default
title: Automation
parent: Fyde CLI Client
nav_order: 7
---

# Automation

fyde-cli is built with automation in mind, and has a number of features to make it easier to integrate in scripts.

## JSON output

By default, fyde-cli will provide its output in JSON format when a non-interactive terminal is detected.
This behavior is adjustable.
See [Output formats]({{ site.baseurl }}{% link fyde-cli/use.md %}#output-formats) for more information.

## JSON input and command chaining

`add` and `edit` commands can read input from JSON files, as detailed in [Batch mode operations]({{ site.baseurl }}{% link fyde-cli/batch-mode-operations.md %}).
Some commands can take arguments either from the command line or from JSON-formatted standard input:

```
echo [{"id": 724},{"id":741}] | fyde-cli user enable
+-----+---------+
|  ID | Result  |
+-----+---------+
| 724 | success |
| 741 | success |
+-----+---------+
(2 records out of 2)
```

The expected input format is designed such that some commands can be chained.
For example, to create a user and immediately return its enrollment link, one could do:

```
$ fyde-cli user add --username "John Doe" | fyde-cli user enrollment get
https://www.fyde.com/enroll?endpoint=[...]
```

To disable all users in the search results for "John Doe", one could do:

```
$ fyde-cli user list -q "John" --list-all | fyde-cli user disable
+-----+---------+
|  ID | Result  |
+-----+---------+
| 770 | success |
+-----+---------+
(1 record out of 1)
```

Commands which accept JSON lists of IDs, on the standard input, include:

 - `device delete`
 - `device revoke`
 - `domain delete`
 - `group delete`
 - `policy delete`
 - `resource delete`
 - `user delete`
 - `user enable`
 - `user disable`
 - `source enable`
 - `source disable`
 - `user enrollment generate`
 - `user enrollment revoke`
 - `user enrollment change`
 - `user enrollment get`

Input to these commands has the following precedence:

1. `--id` flag value (positional arguments and stdin are ignored)
2. Positional arguments (stdin is ignored)
3. Stdin