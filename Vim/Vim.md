# Vim

## Links

- [7 Tips](https://www.freecodecamp.org/news/7-vim-tips-that-changed-my-life/)
- [Python](https://www.vimfromscratch.com/articles/vim-for-python/)
- [IPython](https://pythonawesome.com/seamlessly-run-python-code-from-vim-in-ipython/#installation)

## Getting search in between <div>


```vim
::/\(hidden;">\)\@<=.\{-}\(\<div\)\@=
```
## Remember

`33G` - Going to the line number needed
`Ctrl+]` - to go to specific seciont of vim help

 - `:s/pattern/replace/g` - find and replace in current line
 - `:%s///replace/g` - replace last search in entire e
 - `%` - serch in entire e
 - `:help :substitute`

## Plugins


### vim-plug

`~\.vimrc` - file to edit
`:source ~/.vimrc` - To reload source
`:PlugInstall` - to Install new plugins
`:PlugUpdate` - in case of update
`:PlugClean` - remove unlisted plugins

## Extensions

- See the file hirarchy
- Intellisens
- Documentation
- Vim MarkDown syntaxis formated

### Tabular

[Github link](https://github.com/godlygeek/tabular)

Text aligning tools

## Vimtutor

vim C:\tools\vim\vim82\tutor\tutor

## NERDTree

[Github link](https://github.com/preservim/nerdtree)

```vim

nnoremap <leader>n :NERDTreeFocus<CR>
nnoremap <C-n> :NERDTree<CR>
nnoremap <C-t> :NERDTreeToggle<CR>
nnoremap <C-f> :NERDTreeFind<CR>

```
## Questions

- Top plugins
- Vim multiple tabs
- Tree view 
- Intelisense

## Command line syntaxis
 
 - `:!` - execute in command line
 - `%` - current file name
 - `:pu=strftime('%c')` gives date 08/01/2022 8:36:40 pm

## Set
 - `:set  number` - turn on numbers
 - `:set  nonumber` - turn off line numbers
 - `:set hlsearch` - turn on highlight on search
 - `:noh` - turn off highlight on search

## Search

 - `/`  search for something
 - `//` previous search
 - `?`  backward search
 - `:set hlsearch` - turn on highlight on search
 - `:noh` - turn off highlight on search

## Substitue

 - `:1,4s/^/#` - Add # on begining of each line from 1 to 4
 - `:s/pattern/replace/g` - find and replace in current line
 - `:%s///replace/g` - replace last search in entire file
 - `%` - serch in entire file
 - `:help :substitute`

### Vimgrep

Super awesome vim search in multiple files

## Concept 

 I think it might be a great idea to completly switch to vim
 I have couple of blind spots with vim. But the general concpt of working full in `Vim` is sort of Idea that I like I mean it is cool.

## Copy pase MS Widnows buffer

<kbd>"</kbd>+<kbd>\*</kbd>+<kbd>y</kbd> - copy

<kbd>"</kbd>+<kbd>\*</kbd>+<kbd>p</kbd> - paste 

<kbd>Ctrl</kbd>+<kbd>Q</kbd> - Visual block mode 

<kbd>Shift</kbd>+<kbd>I</kbd> -  Insert changes in visual block mode

## Navigation

<kbd>Ctrl</kbd>+<kbd>]</kbd> - Move to tag in vim help
<kbd>Ctrl</kbd>+<kbd>O</kbd> - Get to begining
<kbd>Ctrl</kbd>+<kbd>T</kbd> - Get to previous location
## Scrolling

<kbd>Ctrl</kbd>+<kbd>U</kbd> - Scroll up 
<kbd>Ctrl</kbd>+<kbd>D</kbd> - Scroll Down
<kbd>Ctrl</kbd>+<kbd>Y</kbd> - Scroll One Line up 
<kbd>Ctrl</kbd>+<kbd>E</kbd> - Scroll One Line Down

`zz` - Scroll to the screen center
`zt` - Scroll to the Top
`zb` - Scroll to the Bottom



## Old vimrc file   


```vim
set nocompatible              " required
filetype on                  " required
syntax on
set shortmess=a

let g:pymode_python = 'python3'
let g:slime_target = "vimterminal"
let g:pymode_lint_write = 0       "turn off running pylint on file save
let g:pymode_lint_write = 0       "turn off running pylint on file save
let mapleader = ","
nnoremap <leader>p :PyLint<cr>    "pressing ,p will run plyint on current buffer

call plug#begin('~/.vim/plugged')

" Shorthand notation; fetches https://github.com/junegunn/vim-easy-align
" Plug 'junegunn/vim-easy-align'

Plug 'scrooloose/nerdtree'
Plug 'github/copilot.vim'
Plug 'tpope/vim-commentary' 
Plug 'junegunn/fzf.vim'
Plug 'iamcco/markdown-preview.vim'
Plug 'aklt/plantuml-syntax'
Plug 'tyru/open-browser.vim'
Plug 'weirongxu/plantuml-previewer.vim'
" 
Plug 'godlygeek/tabular'
Plug 'preservim/vim-markdown'

" is the best for the syntax highlighting
Plug 'numirias/semshi'
Plug 'google/yapf' 

" Plug 'jpalardy/vim-slime', { 'for': 'python' }
" Plug 'hanschen/vim-ipython-cell', { 'for': 'python' }
"
" Intellisense code completion

call plug#end()
" for proper indenting
"Plug 'Vimjas/vim-python-pep8-indent 
" puis an asynchronous linter plugin. Use it with flake8 and pylint;
"Plug 'dense-analysis/ale' 
"  formatter.
"Plug 'neoclide/coc.nvim'
"Plug 'neoclide/coc-python' 

"NERDTree settings
let mapleader = "," " map leader to comma
nnoremap <leader>n :NERDTreeFocus<CR>
noremap <C-t> :NERDTreeToggle<CR>
nnoremap <C-f> :NERDTreeFind<CR>
```
