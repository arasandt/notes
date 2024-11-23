### Create a terminals.json using the below JSON file
{
  "autorun": false,
  "terminals": [
    {
      "name": "Single",
      "description": "This is a description",
      "focus": true,
      "command": "echo \"Hello World\""
    },
    {
      "name": "Multi",
      "commands": [
        "echo \"Did you know?\"",
        "echo \"You can execute multiple commands\""
      ]
    },
    {
      "name": "Single - No execution",
      "execute": false,
      "command": "Press enter to run me"
    },
    {
      "name": "Multi - No execution",
      "execute": false,
      "commands": [
        "echo \"Only the last command won't be executed\"",
        "Press enter to run me"
      ]
    },
    {
      "name": "Persistent",
      "focus": true,
      "onlySingle": true,
      "persistent": "demo_persistent",
      "command": "echo \"I'm persistent! Try to reload the window and re-execute this command\""
    },
    {
      "name": "Variable Substitution",
      "description": "Many special strings can be substituted dynamically",
      "command": "echo \"workspaceFolder: [workspaceFolder]\\nworkspaceFolderBasename: [workspaceFolderBasename]\\nfile: [file]\\nrelativeFile: [relativeFile]\\nfileBasename: [fileBasename]\\nfileBasenameNoExtension: [fileBasenameNoExtension]\\nfileDirname: [fileDirname]\\nfileExtname: [fileExtname]\\ncwd: [cwd]\\nlineNumber: [lineNumber]\""
    },
    {
      "name": "Only Single",
      "open": true,
      "onlySingle": true,
      "command": "echo \"I will not run with the others\""
    }
  ]
}




### One example of creating remote.txt for vs code remote terminal
Host xxtdev
  HostName 10.0.0.38
  IdentityFile C:\Users\xx\Downloads\ssh\.ssh\xx.pem
  User guptapoo  




### How to add Mobaxterm aliases
function git-quickcommit { git add -u ; git commit -m minorchange ; git push }
Set-Alias -Name gitm -Value git-quickcommit
$profile
function gitpush($a) { git add -u ; git commit -m $a ; git push}
function gitm { git add -u ; git commit -m minorchange ; git push }f
function sshr($a) {ssh-keygen -R $a}

### Easilty push code to all branches one by one
git branch merge
git checkout qa
git pull
git merge dev -m"merged dev to qa"
git push 
git checkout stage
git pull
git merge qa -m"merged qa to stage"
git push
git checkout prod
git pull
git merge stage -m"merged stage to prod"
git push
git checkout dev
git diff dev..qa
git diff qa..stage
git diff stage..prod








## VS Code Shortcuts
### Toggle sidebar
Ctrl + b 
### Command palette
Ctrl + Shift + p 
### Dearch files
Ctrl + p
### Move across open files
Ctrl + page up
### Copy paste line
Ctrl + c & v
### Select a word
Ctrl + d
### Multi line editing
Ctrl + D
### Highlighting lines
Ctri + L

### Some setting to setup in VS CODE
Goto Settings and Turn WordWrap on
Goto Settings and Exclude Node Modules from the directory. It will not show.
Goto Settings and Expand the cursor. Zooms in and Zooms out.

### Setup the below VS Code extensions
Prettier, Better Comments, Quokka.js (live scratchpad), Live Server, Bracket Pair Colorizer, impost cost, Auto Import, Markdown PDF, Setting Sync, Git Lens, Thunder Client.
Do “User Snippets”. Use repeated code.
 
### Command Pallette
In command pallete, use character # to find code, and character @ to find symbols
