# vscodeUse

# Q: Can not change vscode theme

Occurs when simply switching, or opening / closing a tab, and does not revert if "undoing" the tab change. Below gif's on a freshly reinstalled VSCode, though I didn't erase all cache, preferences, etc. when uninstalling.

## Solve

In my case, this was due to a rogue VSCode extension not behaving properly - disabling the [BioSyntax extension](https://marketplace.visualstudio.com/items?itemName=reageyao.biosyntax) fixed it.

