---
layout: post
title:	"Redimensionar partições LVM"
date:	2017-04-11 03:00:00
categories:
    - blog
tags:
    - linux
    - lvm
---

Em um post passado, mostrando como fazer a [instalação do Arch Linux \[0\]][0], utilizei do LVM para gerenciar os discos. Lá falei um pouco mais da teoria por trás dele e tal. Aqui vou me ater mesmo a repassar o passo a passo utilizado para isso.

Uma questão a ser dita é que o LVM nos dá a possibilidade de poder redimensionar nossas partições sem desligar o sistema. Acontece que a depender de sua aplicação, mesmo que não dê um shutdown no sistema, as consequências podem ser as mesmas. Explico: para aumentar o tamanho da partição é moleza, dá para fazer sem mais nem menos. Agora para diminuir o volume de uma partição tem de desmontá-la e tudo mais. E isso para alguns pode ser um grande problema.

Mas enfim, vamos lá...

## Reduzir o tamanho

Digamos que uma partição sua está sendo menos utilizada que outra e que você quer tirar um pouco de espaço dessa determinada partição e colocar na outra. Pois bem, não esqueça de adaptar os endereços aqui para seu cenário, uma breve explicação:

* `/particao`: endereço no qual a partição que você está usando está montada
* `VolumeGroup`: acredito que o nome já é autoexplicativo
* `LogicalVolume01` e `LogicalVolume02`: os nomes também já se explicam, mas a numeração se refere a que o 01 é o volume lógico que irá diminuir de tamanho, enquanto o 02 o que irá aumentar
* `XXG`: nova quantidade de gigas da partição que teve espaço diminuído

Primeiro, desmonte a partição:

~~~
# umount /particao
~~~

Então, repare o sistema de arquivos:

~~~
# fsck -f /dev/VolumeGroup/LogicalVolume01
~~~

Agora de fato redimensione:

~~~
# resize2fs /dev/VolumeGroup/LogicalVolume01 XXG
~~~

E então, reduza o tamanho do volume lógico para seu novo espaço:

~~~
# lvreduce -L XXG /dev/VolumeGroup/LogicalVolume01
~~~

Agora monte sua partição numa boa:

~~~
# mount /particao
~~~

## Aumentar tamanho

Depois que passei por alguns apertos passei a deixar alguns gigas "sobrando" quando ia pensar no esquemas de partições, justamente por essa facilidade da adição em relação à redução. Pois bem, tendo em vista que já se tem o espaço sobrando, como o procedimento acima mostra como fazer, basta seguir:

~~~
# lvextend -L +10G /dev/mapper/main-root
# resize2fs /dev/mapper/main-root
~~~

E pronto. Agora cheque o tamanho dos discos com `df -h` e seja feliz! :)

Até!

## Links

~~~
[0]: {{ site.url }}{{ site.baseurl }}blog/archlinux-lvm-luks/
~~~

[0]: {{ site.baseurl }}blog/archlinux-lvm-luks/
