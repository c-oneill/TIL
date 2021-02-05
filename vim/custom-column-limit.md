#### Custom column limit

Date: 02/05/2021

I wanted to add some customization to my editor so text is highlighted after 80 characters.

I created a new `.vimrc` file in my home directory `~` based off the advice [here](https://stackoverflow.com/questions/25273075/editing-my-vimrc-file-on-a-mac).

I appended this code:
```
highlight OverLength ctermbg=darkred ctermfg=white guibg=#FFD9D9
match OverLength /\%>80v.\+/
```
This snippet is pulled verbatim from a stack overflow answer [here](https://stackoverflow.com/questions/235439/vim-80-column-layout-concerns).

Resources:
* https://stackoverflow.com/questions/235439/vim-80-column-layout-concerns
* https://stackoverflow.com/questions/25273075/editing-my-vimrc-file-on-a-mac

