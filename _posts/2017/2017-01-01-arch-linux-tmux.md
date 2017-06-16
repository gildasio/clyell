---
layout: post
title:	"Arch Linux + Tmux = CLI++"
date:	2017-01-01 12:00:00
categories:
    - blog
tags:
    - archlinux
    - linux
    - screenshot
    - tmux
---

![Screenshot]({{ site.baseurl }}images/posts/2017/01.png)

> Caso queira ver o print maior, [clica aqui \[0\]][0].

Primeiro post do blog em 2017, logo no primeiro dia do ano, será que isso quer dizer alguma coisa? haha

Enfim, temos aqui um screenshot, algo que já queria postar há um tempo, mas enfim, está aqui agora. Nele tem aberto o filme "Lights Out" no Mplayer (\o/) e por trás o Tmux, com ZSH.

O Tmux é quase o padrão. No arquivo de configuração tem apenas o seguinte:

~~~
bind c new-window -c '#{pane_current_path}'
bind '"' split-window -c '#{pane_current_path}'
bind % split-window -h -c '#{pane_current_path}'
~~~

Contribuição do [Marino][marino], que serve para quando abrirmos um novo painel no Tmux, ele persistir o diretório do painel atual.

Já no ZSH eu utilizo o [Oh-My-ZSH \[1\]][1] com um tema bem simples que montei:

~~~
setopt promptsubst
PROMPT=$'%B${(r:$COLUMNS::¨:)}$(git_prompt_info)%{$fg[white]%}>> %b%{$reset_color%}'
RPROMPT='%B%*%b'

ZSH_THEME_GIT_PROMPT_PREFIX="%{$fg[white]%}"
ZSH_THEME_GIT_PROMPT_SUFFIX="%{$reset_color%} "
ZSH_THEME_GIT_PROMPT_DIRTY="%{$fg[red]%} *%{$reset_color%}"
ZSH_THEME_GIT_PROMPT_CLEAN=""
~~~

E lá ao fundo o wallpaper de gatênho! Aqui o link para ele: [Gatênho \[2\]][2].

Bom, tomara que começar o ano postando algo assim faça vir mais posts e coisas boas por aqui. Até a próxima, pessoal! o/

## Links

~~~
[0]: {{ site.url }}{{ site.baseurl }}images/posts/2017/01.png
[1]: http://ohmyz.sh/
[2]: {{ site.url }}{{ site.baseurl }}images/posts/2017/02.jpg
~~~

[0]: {{ site.baseurl }}images/posts/2017/01.png
[2]: {{ site.baseurl }}images/posts/2017/02.jpg
[1]: http://ohmyz.sh/
[marino]: https://github.com/marinofull
