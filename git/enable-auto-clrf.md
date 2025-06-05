# Enabling Auto CRLF for Windows

f you’re programming on Windows and working with people who are not (or vice-versa), you’ll probably run into line-ending issues at some point. This is because Windows uses both a carriage-return character and a linefeed character for newlines in its files, whereas Mac and Linux systems use only the linefeed character. This is a subtle but incredibly annoying fact of cross-platform work; many editors on Windows silently replace existing LF-style line endings with CRLF, or insert both line-ending characters when the user hits the enter key.

Git can handle this by auto-converting CRLF line endings into LF when you add a file to the index, and vice versa when it checks out code onto your filesystem. You can turn on this functionality with the core.autocrlf setting. If you’re on a Windows machine, set it to true – this converts LF endings into CRLF when you check out code:

```bash
$ git config --global core.autocrlf true
```

Source: https://stackoverflow.com/a/5834094/2449105

---

To turn off the warning about CRLF line endings, you can set the `core.safecrlf` option to false. This will allow you to commit files with mixed line endings without Git warning you about it.

```bash
$ git config --global core.safecrlf false
```

Source: https://stackoverflow.com/a/14640908/2449105