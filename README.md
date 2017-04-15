# config-vim
~/.vimrc文件是vim的配置文件。
## 安装步骤：
### 1. 安装Vundle

[Vundle在GitHub上的URL](https://github.com/VundleVim/Vundle.vim)

`git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim`

### 2. 修改~/.vimrc

```vim
set encoding=utf-8 fileencodings=ucs-bom,utf-8,gbk,cp936

set nocompatible              " be iMproved, required
filetype off                  " required

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/some/path/here')

" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'
Plugin 'The-NERD-tree'
Plugin 'majutsushi/tagbar'
Plugin 'vim-airline/vim-airline'
Plugin 'vim-airline/vim-airline-themes'
Plugin 'scrooloose/syntastic'
Plugin 'tComment'
Plugin 'hynek/vim-python-pep8-indent'
Plugin 'Yggdroot/indentLine'

" All of your Plugins must be added before the following line
call vundle#end()            " required
filetype plugin indent on    " required
" To ignore plugin indent changes, instead use:
"filetype plugin on
"
" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just:PluginUpdate
" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
"
" see :h vundle for more details or wiki for FAQ
" Put your non-Plugin stuff after this line

nmap <F2> :NERDTreeToggle<CR>
let g:NERDTreeDirArrows = 0

nmap <F3> :TagbarToggle<CR>

set t_Co=256
set laststatus=2
let g:airline#extensions#whitespace#enabled = 0
let g:airline#extensions#whitespace#symbol = '!'
let g:airline_powerline_fonts = 1
if !exists('g:airline_symbols')
	let g:airline_symbols = {}
endif
" old vim-powerline symbols
let g:airline_left_sep = '⮀'
let g:airline_left_alt_sep = '⮁'
let g:airline_right_sep = '⮂'
let g:airline_right_alt_sep = '⮃'
let g:airline_symbols.branch = '⭠'
let g:airline_symbols.readonly = '⭤'
let g:airline_symbols.linenr = '⭡'
let g:airline_symbols.maxlinenr = '⭡'
let g:airline#extensions#tabline#enabled = 1
nnoremap <C-N> :bn<CR>
nnoremap <C-P> :bp<CR>

set statusline+=%#warningmsg#
set statusline+=%{SyntasticStatuslineFlag()}
set statusline+=%*

let g:syntastic_always_populate_loc_list = 1
let g:syntastic_auto_loc_list = 1
let g:syntastic_check_on_open = 1
let g:syntastic_check_on_wq = 0

set backspace=indent,eol,start
set list lcs=tab:\|\ 
syntax on
set smartindent
set showcmd
set tags=tags;
set autochdir
autocmd FileType python,php,html,css,javascript setlocal et sta sw=4 sts=4
```
### 3. 开始安装插件

进入VIM然后:PluginInstall

airline需要安装字体：[airline字体](https://github.com/powerline/fonts)，git clone下来sh安装脚本就行。

airline配置看这个：[airline配置](http://note.youdao.com/noteshare?id=23a98148642a7b994ae53e22b515019c&sub=465EE16A802E45F9B0B6D6CA79CE37EC)。

注意，Yggdroot/indentLine这个插件需要vim7.3以上版本。我是先把自带vim卸了然后编译安装的vim8.0。
