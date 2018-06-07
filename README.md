## Laboratory work II

Данная лабораторная работа посвещена изучению утилит для разработки проектов

## Tasks

- [ ] 1. Ознакомиться со ссылками учебного материала
- [ ] 2. Выполнить инструкцию учебного материала
- [ ] 3. Составить отчет и отправить ссылку личным сообщением в **Slack**
 
## Tutorial

```bash
$ export GITHUB_USERNAME=VladislavSchastnyi # присвоение переменной среды значение
$ export GIST_TOKEN=<сохраненный_токен> # присвоение переменной среды значение
$ alias edit=nano # создание псевдоним команды
```

```ShellSession
$ mkdir -p ${GITHUB_USERNAME}/workspace # создае каталога
$ cd ${GITHUB_USERNAME}/workspace # переход в каталог
$ pwd # вывод на экран путь в текущий каталог
/home/ubuntu/workspace/VladislavSchastnyi/workspace
$ cd .. # переход в "корневую" директорию
$ pwd
/home/ubuntu/workspace/VladislavSchastnyi
```

```ShellSession
$ mkdir -p workspace/tasks/ # создание каталога
$ mkdir -p workspace/projects/ # создание каталога
$ mkdir -p workspace/reports/ # создание каталога 
$ cd workspace # изменеие текущего каталога
```

```ShellSession
# Debian
$ wget https://nodejs.org/dist/v6.11.5/node-v6.11.5-linux-x64.tar.xz # загрузка архива
--2018-06-07 12:46:46--  https://nodejs.org/dist/v6.11.5/node-v6.11.5-linux-x64.tar.xz
Resolving nodejs.org (nodejs.org)... 104.20.22.46, 104.20.23.46, 2400:cb00:2048:1::6814:172e, ...
Connecting to nodejs.org (nodejs.org)|104.20.22.46|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9356460 (8.9M) [application/x-xz]
Saving to: ‘node-v6.11.5-linux-x64.tar.xz’

100%[======================================================================================================================================================>] 9,356,460   7.76MB/s   in 1.1s   

2018-06-07 12:46:48 (7.76 MB/s) - ‘node-v6.11.5-linux-x64.tar.xz’ saved [9356460/9356460]

$ tar -xf node-v6.11.5-linux-x64.tar.xz # разархивирование
$ rm -rf node-v6.11.5-linux-x64.tar.xz # удаление архива
$ mv node-v6.11.5-linux-x64 node # переименование файла
```

```ShellSession
$ ls node/bin # вывод на экран содержимого 
node*  npm@
$ echo ${PATH} # отображение содержимого переменной PATH
/home/ubuntu/.nvm/versions/node/v7.6.0/bin:/home/ubuntu/bin:/usr/local/rvm/gems/ruby-2.4.0/bin:/usr/local/rvm/gems/ruby-2.4.0@global/bin:/usr/local/rvm/rubies/ruby-2.4.0/bin:/home/ubuntu/bin:/opt/pyenv/shims:/opt/pyenv/bin:/home/ubuntu/.cs50/bin:/opt/cs50/bin:/mnt/shared/bin:/home/ubuntu/workspace/node_modules/.bin:/home/ubuntu/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/mnt/shared/sbin:/opt/gitl:/opt/go/bin:/mnt/shared/c9/app.nw/bin:/home/ubuntu/.local/bin:/usr/local/rvm/bin
$ export PATH=${PATH}:`pwd`/node/bin # присвоение переменной среды PATH новое значение 
$ echo ${PATH} # отображает содержимое переменной PATH
/home/ubuntu/.nvm/versions/node/v7.6.0/bin:/home/ubuntu/bin:/usr/local/rvm/gems/ruby-2.4.0/bin:/usr/local/rvm/gems/ruby-2.4.0@global/bin:/usr/local/rvm/rubies/ruby-2.4.0/bin:/home/ubuntu/bin:/opt/pyenv/shims:/opt/pyenv/bin:/home/ubuntu/.cs50/bin:/opt/cs50/bin:/mnt/shared/bin:/home/ubuntu/workspace/node_modules/.bin:/home/ubuntu/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/mnt/shared/sbin:/opt/gitl:/opt/go/bin:/mnt/shared/c9/app.nw/bin:/home/ubuntu/.local/bin:/usr/local/rvm/bin:/home/ubuntu/workspace/VladislavSchastnyi/workspace/node/bin
$ mkdir scripts
$ cat > scripts/activate<<EOF # копирование в файл содержимого переменной PATH c измененным значением
export PATH=\${PATH}:`pwd`/node/bin
EOF
$ source scripts/activate # чтение и выполнение команды из файла в текущей среде
```

```ShellSession
$ npm install -g gistup # установка gistup
/home/ubuntu/.nvm/versions/node/v7.6.0/bin/gistup -> /home/ubuntu/.nvm/versions/node/v7.6.0/lib/node_modules/gistup/bin/gistup
/home/ubuntu/.nvm/versions/node/v7.6.0/bin/gistup-open -> /home/ubuntu/.nvm/versions/node/v7.6.0/lib/node_modules/gistup/bin/gistup-open
/home/ubuntu/.nvm/versions/node/v7.6.0/bin/gistup-rename -> /home/ubuntu/.nvm/versions/node/v7.6.0/lib/node_modules/gistup/bin/gistup-rename
/home/ubuntu/.nvm/versions/node/v7.6.0/lib
└─┬ gistup@0.1.3 
  ├─┬ optimist@0.3.7 
  │ └── wordwrap@0.0.3 
  └── queue-async@1.2.1 

$ ls node/bin # вывод на экран содержимого
node*  npm@
```

```ShellSession
$ cat > ~/.gistup.json <<EOF # запись в файл токен
{
  "token": "${GIST_TOKEN}"
}
EOF
```

## Report

```ShellSession
$ export LAB_NUMBER=02 # присвоение переменной среды значение
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER} # копируем репозиторий в директорию
Cloning into 'tasks/lab02'...
remote: Counting objects: 37, done.
remote: Total 37 (delta 0), reused 0 (delta 0), pack-reused 37
Unpacking objects: 100% (37/37), done.
$ mkdir reports/lab${LAB_NUMBER} # создание директории
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md # копируем содержимое файла
$ cd reports/lab${LAB_NUMBER} # изменяем текущую директорию
$ edit REPORT.md # открываем файл на редактирование
$ gistup -m "lab${LAB_NUMBER}" # enter: yes↵ # загружаем отредактированный файл на GitHub
Reinitialized existing Git repository in /home/ubuntu/workspace/VladislavSchastnyi/workspace/reports/lab02/.git/
[master 75301d2] Initial gistup commit.
/home/ubuntu/.nvm/versions/node/v7.6.0/lib/node_modules/gistup/lib/gistup/unless.js:11

## Links

### Unix commands

- [ar](https://en.wikipedia.org/wiki/Ar_(Unix))
- [cat](https://en.wikipedia.org/wiki/Cat_(Unix))
- [cd](https://en.wikipedia.org/wiki/Cd_(command))
- [cp](https://en.wikipedia.org/wiki/Cp_(Unix))
- [cut](https://en.wikipedia.org/wiki/Cut_(Unix))
- [echo](https://en.wikipedia.org/wiki/Echo_(command))
- [env](https://en.wikipedia.org/wiki/Env_(shell))
- [ex](https://en.wikipedia.org/wiki/Ex_(editor))
- [file](https://en.wikipedia.org/wiki/File_(command))
- [find](https://en.wikipedia.org/wiki/Find)
- [ls](https://en.wikipedia.org/wiki/Ls)
- [man](https://en.wikipedia.org/wiki/Man_page)
- [mkdir](https://en.wikipedia.org/wiki/Mkdir)
- [mv](https://en.wikipedia.org/wiki/Mv)
- [nm](https://en.wikipedia.org/wiki/Nm_(Unix))
- [ps](https://en.wikipedia.org/wiki/Ps_(Unix))
- [pwd](https://en.wikipedia.org/wiki/Pwd)
- [rm](https://en.wikipedia.org/wiki/Rm_(Unix))
- [sed](https://en.wikipedia.org/wiki/Sed)
- [touch](https://en.wikipedia.org/wiki/Touch_(Unix))

### Package Managers

- [apt](http://help.ubuntu.ru/wiki/apt) | [dnf](https://en.wikipedia.org/wiki/DNF_(software)) | [yum](https://fedoraproject.org/wiki/Yum/ru)
- [brew](https://brew.sh) | [linuxbrew](http://linuxbrew.sh)
- [npm](https://docs.npmjs.com)

### Software

- [curl](https://www.gitbook.com/book/bagder/everything-curl/details)
- [wget](https://www.gnu.org/software/wget/manual/wget.pdf)
- [clang](https://clang.llvm.org)
- [g++](https://gcc.gnu.org/onlinedocs/gcc-4.0.2/gcc/G_002b_002b-and-GCC.html)
- [make](https://en.wikipedia.org/wiki/Make_(software))
- [open](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/open.1.html)
- [openssl](https://www.openssl.org)
- [nano](https://www.nano-editor.org)
- [tree](https://linux.die.net/man/1/tree)
- [vim](http://www.vim.org)

```
Copyright (c) 2017 Братья Вершинины
```
