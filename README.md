# AutoSave

## Description

AutoSave - automatically save changes to disk without having to use `:w` (or any binding to it) every time a buffer has been modified.

Inspired by the same feature in RubyMine text editor.

## Installation and Usage

Use [vundle](https://github.com/gmarik/vundle) or
download [packaged version](http://www.vim.org/scripts/script.php?script_id=4521) from vim.org.

AutoSave is disabled by default, run `:AutoSaveToggle` to enable/disable it.  
If you want plugin to be always enabled it can be done with `g:auto_save` option:

```VimL
" .vimrc
let g:auto_save = 1  " enable AutoSave on Vim startup

```

AutoSave relies on `CursorHold` event and sets the `updatetime` option to 200 so that modifications are saved almost instantly.  
But sometimes changing the `updatetime` option may affect other plugins and break things.  
You can prevent AutoSave from changing the `updatetime` with `g:auto_save_no_updatetime` option:

```VimL
" .vimrc
let g:auto_save_no_updatetime = 1  " do not change the 'updatetime' option

```

You can disable AutoSave in insert mode with the `g:auto_save_in_insert_mode` option:

```VimL
" .vimrc
let g:auto_save_in_insert_mode = 0  " do not save while in insert mode

```

AutoSave will display on the status line on each auto-save by default.

```
(AutoSaved at 08:40:55)
```

You can silence the display with the `g:auto_save_silent` option:

```VimL
" .vimrc
let g:auto_save_silent = 1  " do not display the auto-save notification

```

If you need an autosave hook (such as generating tags post-save) then use `g:auto_save_postsave_hook` option:

```VimL
" .vimrc
let g:auto_save_postsave_hook = 'TagsGenerate'  " this will run :TagsGenerate after each save
```

The events on which AutoSave will perform a save can also be adjusted using the `g:auto_save_events` option.
Using `InsertLeave` and `TextChanged` only, for example, will save on every change in normal mode.

```.VimL
let g:auto_save_events = ["InsertLeave", "TextChanged"]
```

This options default value is 1. It fixes the [selecting your pasted
text](http://vim.wikia.com/wiki/Selecting_your_pasted_text) mapping. Without
it, the mapping will select the whole buffer, because a write operation sets
the `'[` and `']` marks respectively to the start and end of the buffer. If you
want vims default behavior, set the options value to 0:

```VimL
let g:auto_save_keep_marks = 0 " Don't keep the '[ and '] marks. It will break
                               " the selecting your pasted text mapping:
                               " http://vim.wikia.com/wiki/Selecting_your_pasted_text
```

## Contribution

Development is made in [907th/vim-auto-save](https://github.com/907th/vim-auto-save) repo.  
Feel free to contribute!

## License

Distributed under the MIT License (see LICENSE.txt).

Copyright (c) 2013-2015 Alexey Chernenkov
