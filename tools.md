---
layout: default
---


# tools memo

## Terminal Recording(asciinema)
- <https://asciinema.org/~friendbear>
  - <https://asciinema.org/docs/how-it-works>

  ```sh
  brew install asciinema
  asciinema rec

  exit
  ```

## enhancd
cd command is one of the frequently used commands.

<https://github.com/b4b4r07/enhancd/blob/master/README.md>


## vi
```sh
curl -sLf https://spacevim.org/install.sh | bash
        /######                                     /##    /##/##
       /##__  ##                                   | ##   | #|__/
      | ##  \__/ /######  /######  /####### /######| ##   | ##/##/######/####
      |  ###### /##__  ##|____  ##/##_____//##__  #|  ## / ##| #| ##_  ##_  ##
       \____  #| ##  \ ## /######| ##     | ########\  ## ##/| #| ## \ ## \ ##
       /##  \ #| ##  | ##/##__  #| ##     | ##_____/ \  ###/ | #| ## | ## | ##
      |  ######| #######|  ######|  ######|  #######  \  #/  | #| ## | ## | ##
       \______/| ##____/ \_______/\_______/\_______/   \_/   |__|__/ |__/ |__/
               | ##
               | ##
               |__/
                      version : 1.1.0-dev       by : spacevim.org
```

### Metal-vim plugin

```
“ Configuration for vim-plug
Plug ‘derekwyatt/vim-scala’
Plug ‘natebosch/vim-lsc’

“ Configuration for vim-scala
au BufRead,BufNewFile *.sbt set filetype=scala

“ Configuration for vim-lsc
let g:lsc_enable_autocomplete = v:false
let g:lsc_server_commands = {
  \  ‘scala’: {
  \    ‘command’: ‘metals-vim’,
  \    ‘log_level’: ‘Log’
  \  }
  \}
let g:lsc_auto_map = {
  \  ‘GoToDefinition’: ‘gd’,
  \}
```