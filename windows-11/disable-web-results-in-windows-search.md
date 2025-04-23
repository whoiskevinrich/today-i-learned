# Disable Web Results in Windows Search

Web results in Windows 11 Pro Search can be disabled by editiing the group policy. This will prevent web results from appearing when searching from the `Win` key.

1. Run `gpedit.msc` to open the Group Policy Editor
2. Go to "Computer Configuration" > "Administrative Templates" > "Windows Components" > "Search"
3. Find and open "Do not allow web search"
4. Toggle setting to "Enabled"
5. Restart Windows