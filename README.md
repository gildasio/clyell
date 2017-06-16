# Clyell

[https://gjuniioor.github.io/clyell](https://gjuniioor.github.io/clyell)

### About

It's just one more [jekyll](https://github.com/jekyll/jekyll) theme. Maybe it's has some appearance like a linux console. :)

[Bootstrap](http://getbootstrap.com/) was added to turn responsible. Thanks, [@magnunleno](https://github.com/magnunleno).

### Features

- [x] Google analytics
- [x] Disqus
- [x] Responsible
- [x] Highlights for code

### Characteristics

- [x] Customized (and nice :P) 404 page
- [x] Simple
- [x] Friendly to read

### Screenshots

![Screenshot]({{ site.baseurl }}images/screenshot/01.png)

![Screenshot]({{ site.baseurl }}images/screenshot/02.png)

### Config file example

~~~ yml
# Site settings
title: "gjuniioor"
bye_message: "Thx!"
baseurl: "/clyell/"
url: "https://gjuniioor.github.io"
disqus: gjuniioor

# Header settings
nick: "gjuniioor"
mail:
    domain: "protonmail"
    ext: "ch"
source_code:
    server: "github.com"
    nick: "gjuniioor"
blog:
    server: "wordpress.com"
    nick: "gjuniioor"
fingerprint_key: "5E12 9ABC C2A9 564B C048  2DF9 D327 0D10 BC71 CF75"

# Build settings
markdown: kramdown
permalink: /:categories/:title/
~~~
