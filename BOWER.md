# **Bower** #

*A package manager for the web*

---
* [Install Bower](#markdown-header-install-bower)
* [Install packages](#markdown-header-install-packages)
* [Cache](#markdown-header-cache)
* [Help](#markdown-header-help)
* [Home](#markdown-header-home)
* [Info](#markdown-header-info)
* [Init](#markdown-header-init)
* [Link](#markdown-header-link)
* [List](#markdown-header-list)
* [Lookup](#markdown-header-lookup)
* [Prune](#markdown-header-prune)
* [Register](#markdown-header-register)
* [Search](#markdown-header-search)
* [Update](#markdown-header-update)
* [Uninstall](#markdown-header-uninstall)
* [Version](#markdown-header-version)

---
## Install Bower

```bash
$ npm install -g bower    #instalacja bowera
```
## Install packages
```bash
$ bower install <package>               #instalacja pakietu
$ bower install <package>#<version>     #instalacja pakietu w odpowiedniej wersji
$ bower install jquery                  #instalacja zarejestrowanego pakietu
$ bower install user/package            #instalacja skrócona z github
$ bower install git://github.com/user/package.git   #instalacja ostatniej wersji z gałęzi master
$ bower install http://example.com/script.js        #instalacja z url

$ bower install <name>=<package>#<version>
$ bower install my/local/folder/                                #instalacja z folderu lokalnego
$ bower install svn+http://package.googlecode.com/svn/          #instalacja z publicznych Subversion
$ bower install svn+ssh://package.googlecode.com/svn/           #instalacja z prywatnych Subversion
$ bower install svn+https://package.googlecode.com/svn/         #jw.
$ bower install http://example.com/package.tar                  #instalcja z archiwum (rozpakowuje)

$ bower install pakiet#1.2.3                        #wersja 1.2.3
$ bower install pakiet#~1.2.3                       #zakresy wersji
$ bower install pakiet#^1.2.3                       #jw.
$ bower install pakiet#>=1.2.3 <2.0           #jw.

$ bower install pakiet#<tag>                  #Git tag
$ bower install pakiet#<sha>                  #Git commit SHA
$ bower install pakiet#<branch>               #Git branch
$ bower install pakiet#<revision>             #Subversion revision
```
#### *Options*

* `-F`, `--force-latest` : Force latest version on conflict
* `-p`, `--production` : Do not install project devDependencies
* `-S`, `--save` : Save installed packages into the project’s bower.json dependencies
* `-D`, `--save-dev` : Save installed packages into the project’s bower.json devDependencies

## Cache
```bash
$ bower cache <command> [<args>]      #zarządzenie pamięcią podręczną (cache)

$ bower cache clean                   #czyszczenie pamięci podręcznej pakietów
$ bower cache clean <name> [<name> ...]
$ bower cache clean <name>#<version> [<name>#<version> ..]      

$ bower cache list                    #lista pamięci podręcznej pakietów
$ bower cache list <name> [<name> ...]
```
## Help
```bash
$ bower help <command>      #pomoc
```
## Home
```bash
$ bower home      #otwiera stronę pakietu w ulubionej przeglądarce
$ bower home <package>
$ bower home <package>#<version>
```
## Info
```bash
$ bower info <package>          #wyświetla ogólne informacje o pakiecie
$ bower info <package> [<property>]
$ bower info <package>#<version> [<property>]         #wyświetla ogólne informacje o pakiecie w określonej wersji
```
## Init
```bash
$ bower init      #tworzy plik bower.json
```
## Link
```bash
$ bower link
$ bower link <name> [<local name>]      #dowiązanie symboliczne do pakietu
```
## List
```bash
$ bower list [<options>]        #lista lokalnych pakietów i ewentualne aktualizacje
$ bower list --json             #lista lokalnych pakietów i ewentualne aktualizacje w formacie JSON 
```
#### *Options*

* `-p`, `--paths` : Generates a simple JSON source mapping
* `-r`, `--relative` : Make paths relative to the directory config property, which defaults to bower_components

## Lookup
```bash
$ bower lookup <name>       #wyświetla adres url pakietu
```
## Prune
```bash
$ bower prune     #odinstalowanie lokalnych pakietów obcych (extraneous)
```
## Register
```bash
$ bower register <name> <url>         #rejestracja pakietu
```
## Search
```bash
$ bower search
$ bower search <name>     #wyszukiwanie pakietu
```
## Update
```bash
$ bower update <name> [<name> ..] [<options>]       #aktualizacje zainstalowanych pakietów do ich najnowszych wersji według bower.json
```
#### *Options*

* `-F`, `--force-latest` : Force latest version on conflict
* `-p`, `--production` : Do not install project devDependencies

## Uninstall
```bash
$ bower uninstall <name> [<name> ..] [<options>]      #odinstalowuje pakiet lokalny z katalogu bower_components
```
#### *Options*

* `-S`, `--save` : Remove uninstalled packages from the project’s bower.json dependencies
* `-D`, `--save-dev` : Remove uninstalled packages from the project’s bower.json devDependencies

## Version
```bash
$ bower version [<newversion> | major | minor | patch]
$ bower version patch -m "Upgrade to %s for reasons"
```
#### *Options*

- `-m`, `--message` : Custom git commit and tag message

---
## Options

* `-f`, `--force` : Makes various commands more forceful
* `-j`, `--json` : Output consumable JSON
* `-l`, `--log-level` : What level of logs to report
* `-o`, `--offline` : Do not use network connection
* `-q`, `--quiet` : Only output important information
* `-s`, `--silent` : Do not output anything, besides errors
* `-v`, `--verbose` : Makes output more verbose
* `--allow-root` : Allows running commands as root. Bower is a user command, there is no need to execute it with superuser permissions. However, if you still want to run commands with sudo, use --allow-root option