Date: 2025-12-06
Tags: [[Tools in Linux]]

# Vim
Vim = It is a modal text editor.
It is different from normal editors because typing does not always insert texts.
it has modes to switch between, to do different tasks.
### Modes

| Mode             | Purpose              | Keys to Enter       | How to Exit     |
| ---------------- | -------------------- | ------------------- | --------------- |
| **Normal**       | Navigation, commands | Press `Esc` anytime | Already default |
| **Insert**       | Type/insert text     | `i`, `a`, `o`, etc. | `Esc`           |
| **Visual**       | Select text          | `v`                 | `Esc`           |
| **Command-line** | Save, quit, configs  | `:`                 | Enter or `Esc`  |

---
## Moving Inside a File (Normal Mode)

Basic movement:

- `h` = left
    
- `j` = down
    
- `k` = up
    
- `l` = right
    

Fast navigation:

- `w` = next word
    
- `b` = previous word
    
- `0` = start of line
    
- `$` = end of line
    
- `gg` = go to top of file
    
- `G` = go to bottom

---
## Entering Text (Insert Mode)

|Action|Key|
|---|---|
|Insert before cursor|`i`|
|Insert after cursor|`a`|
|New line below|`o`|
|New line above|`O`

---
## Editing / Deleting Text

Vim uses **verbs** + **objects**  
Example:

- `d` = delete
    
- `y` = copy
    
- `c` = change (delete + go to insert)
    

Combine like:

- `dw` → delete word
    
- `dd` → delete line
    
- `d$` → delete till end of line
    

Undo/redo:

- `u` → undo
    
- `Ctrl+r` → redo

---
## Visual Mode (Select Like Mouse)

- `v` → select characters
    
- `V` → select whole line
    
- `Ctrl+v` → block select (useful in config files)
    

After selecting:

- `d` → delete
    
- `y` → copy
    
- `p` → paste
---
## Copy & Paste

- `yy` → copy line
    
- `yw` → copy word
    
- `p` → paste below/after cursor
    
- `P` → paste above/before cursor
---
##  Searching & Replacing

Search:

- `/text` → search forward
    
- `?text` → backward
    
- `n` / `N` → next / previous match
    

Replace:

- `:s/old/new` → replace once in line
    
- `:%s/old/new/g` → replace all in file

---
##  Save & Quit (Command Mode `:`)

- `:w` → save
    
- `:q` → quit
    
- `:wq` → save & quit
    
- `:q!` → quit without saving

---
##  Your First Mini Practice Routine (2 mins/day)

Repeat this until comfortable:

1. Move around using `h j k l`
    
2. Insert with `i`, `a`, `o`
    
3. Delete `dw`, `dd`, `d$`
    
4. Copy/paste `yy`, `p`
    
5. Search `/word` + `n`
    
6. Save/quit `:wq`

---
# References
Learn How to use vi / vim editor in Linux with examples in Hindi | MPrashant
ChatGPT

---
# Summary
