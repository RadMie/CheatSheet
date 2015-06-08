# **GIT** #

*Version control system*

---
* [$ git init](#markdown-header-git-init)
* [$ git clone](#markdown-header-git-clone)
* [gitignore](#markdown-header-gitignore)
* [$ git diff](#markdown-header-git-diff)
* [$ git remote](#markdown-header-git-remote)
* [$ git log](#markdown-header-git-log)
* [$ git commit](#markdown-header-git-commit)
* [$ git tag](#markdown-header-git-tag)
* [$ git stash](#markdown-header-git-stash)
* [$ git add](#markdown-header-git-add)
* [$ git show](#markdown-header-git-show)
* [$ git rebase](#markdown-header-git-rebase)
* [$ git reflog](#markdown-header-git-reflog)
* [$ git branch](#markdown-header-git-branch)
* [$ git checkout](#markdown-header-git-checkout)
* [$ git push](#markdown-header-git-push)
* [$ git pull](#markdown-header-git-pull)
* [$ git fetch](#markdown-header-git-fetch)
* [$ git merge](#markdown-header-git-merge)
* [$ git rm](#markdown-header-git-rm)
* [$ git mv](#markdown-header-git-mv)
* [$ git reset](#markdown-header-git-reset)
* [$ git apply](#markdown-header-git-apply)
* [$ git am](#markdown-header-git-am)
* [$ git request-pull](#markdown-header-git-request-pull)
* [$ git cherry-pick](#markdown-header-git-cherry-pick)
* [$ git describe](#markdown-header-git-describe)
* [$ git format-patch](#markdown-header-git-format-patch)
* [$ git rev-parse](#markdown-header-git-rev-parse)
* [Tools](#markdown-header-tools)
* [Help](#markdown-header-help)

---
## $ git config

```bash
$ git config --global user.name "Jan Nowak"             #zmiana danych globalnie
$ git config --global user.email jannowak@example.com   #zmiana danych globalnie

$ git config user.name "Jan Nowak"              #zmiana danych lokalnie
$ git config user.email jannowak@example.com    #zmiana danych lokalnie

$ git config --global core.editor emacs     #zmiana domyslnego edytora textu
$ git config --global merge.tool vimdiff    #zmiana narzędzia obsługi różnic

$ git config --list                         #wyświetla liste konfiguracji

$ git config user.name                      #sprawdzenie konkretnej zmiennej

$ git config --global alias.ci commit       #dodanie aliasów
$ git config --global alias.visual "!gitzk" #alias do zewnętrznego polecenia
```

## $ git init
```bash
$ git init      #rozpoczyna śledzenie zmian w plikach
```
## $ git clone
```bash
$ git clone git://github.com/schacon/grit.git       #klonowanie repozytorium
```
## gitignore
```bash
*.[oa]
*~          #ignorowanie plików z rozszerzeniem .o , .a i konczące sie tyldą
!lib.a      #uwzglednij lib.a mimi ignorowania .a w linijce wyzej
/plik       #ignoruj plik w kat głównym
folder/     #ignoruj wszyst. pliki w katalogu folder
doc/*.txt   #ignoruj doc/notatki.txt, ale nie doc/server/arch.txt
#komentarz
```
## $ git diff
```bash
$ git diff              #Aby zobaczyć, co zmieniłeś ale nie wysłałeś do poczekalni (porównuje roboczy z poczekalną)
$ git diff --cached     #lub     
$ git diff --staged     #zobaczyć zawartość poczekalni, która trafi do repo. z najbliższym zatwierdzeniem
$ git diff --check      #sprawdzenie czy są jakieś spacje
$ git diff master...contrib     #możesz wstawić trzy kropki po nazwie gałęzi z którą chcesz porównać, aby otrzymać różnice z ostatniej zmiany z gałęzi na której się znajdujesz a wspólnym przodkiem tej drugiej
```
## $ git remote
```bash
$ git remote             #wyświetlenie zdalnych repozytoriów
$ git remote -v          #wyświetlenie przypisanego do skrótu, pełnego, zapamiętanego przez Gita, adresu URL
$ git remote add pb git://github.com/paulboone/ticgit.git   #Dodawanie zdalnych repozytoriów
$ git remote show [nazwa-zdalnego-repo]         #inspekcja zdalnych zmian
$ git remote rename pb paul                     #Usuwanie i zmiana nazwy zdalnych repozytoriów
$ git remote rm paul                            #uwuwanie odnośnika do zdalnego repo
```
## $ git log
```bash
$ git log               #listuje zmiany zatwierdzone w tym repozytorium w odwrotnej kolejności chronologicznej
$ git log -p -2         #Pokazuje ona różnice wprowadzone z każdą rewizj, ograniczyć zbiór do dwóch ostatnich wpisów
$ git log --stat        #skrócone statystyki każdej z zatwierdzonych zmian
$ git log --pretty=oneline      #każdą zatwierdzoną zmianę w pojedynczej linii(short,full,fuller)
$ git log --pretty=format:"%h - %an, %ar : %s"          #określić własny wygląd i format informacji
$ git log --pretty=format:"%h %s" --graph               #graf ASCII pokazujący historię gałęzi oraz scaleń
$ git log --after=od --before=do    #od daty do daty
$ git log --since=od --until=do     #jw
$ git log --author                  #Pokazuje rewizje, których wpis autora pasuje do podanego.
$ git log --committer               #Pokazuje jedynie te rewizje w których osoba zatwierdzająca zmiany pasuje do podanej
$ git log --no-merges origin/remote ^local  #zmiany miedzy zdalnym a lokalnym
$ git log --abbrev-commit --pretty=oneline  #odnaleźć unikalne występowania wartości SHA-1
$ git log -g master         #aby zobaczyć wynik reflog-a w formacie podobnym do wyniku git log
$ git log master..galaz     #co znajduje się w Twojej gałęzi "galaz" nie zostało jeszcze włączone do gałęzi "master"

$ git log origin/master..HEAD   #Ta komenda pokaże wszystkie zmiany z Twojej obecnej gałęzi, których nie ma w zdalnej gałęzi master w repozytorium 

$ git log refA..refB            #zmiany które są dostępne z refA, ale nie z refB
$ git log ^refA refB            #jw
$ git log refB --not refA       #jw

$ git log refA refB ^refC       #zmiany które są dostępne z refA lub refB, ale nie z refC
$ git log refA refB --not refC  #jw

$ git log master...experiment   #zmiany które są dostępne z jednej z dwóch referencji, ale nie z obu

$ git log --left-right master...experiment  #jw + po której stronie każda zmiana występuje
```
## $ git commit
```bash
$ git commit -m "Nazwa commita"   #zatwierdzanie zmian z poczekalni
$ git commit -a         #zatwierdzenie zmian bez poczekalni
$ git commit --amend    #poprawka ostatniej rewizji/migawki, poprawia tylko pliki które są w przechowalni

#UWAGA!! Musisz być ostrożny z tymi zmianami, ponieważ wykonywanie komendy "ammend", zmienia sumę SHA-1 dla commitu. Działa to podobnie do bardzo małej zmiany bazy (and. rebase) - nie wykonuj komendy "amend" na ostatnim commicie, jeżeli zdążyłeś go już udostępnić innym.
```
## $ git tag
```bash
$ git tag                   #listowanie etykiet
$ git tag -l 'v1.4.2.*'     #wyszukiwać etykiety za pomocą wzorca
$ git tag -a nazwa_etykiety -m 'notatka etykiety'   #dodanie etykiety opisanej (dodanie -s zamiast -a dołacza podpis GPG)
$ git tag nazwa_etykiey                             #dodanie etykiet lekkiej
$ git tag -v nazwa_etykiety         #weryfikacja etykiety GPG
$ git tag -a nazwa_etykiet sha1     #weryfikowanie histori , sha1 commita
```
## $ git stash
```bash
$ git stash       #SCHOWEK - Podczas dodawania do schowka, pobrane zostaną zmiany które są w obecnym katalogu - czyli pliki które są śledzone i zostały zmodyfikowane oraz dodane do przechowalni - i zapisane zostaną w nim, tak aby mogły być ponownie użyte w dowolnym momencie
$ git stash list    #list zapisanych zmian w przechowalni
$ git stash apply   #nakładnie zmian z przechowalni
$ git stash apply stash@{2}     #jw starszych zmian
$ git stash drop nazwa          #usuwanie zmiany o nazie nazwa
$ git stash apply -- index      #dodawanie plików który był w przechowalni a teraz nie jest
$ git stash pop                 #nałożyć ostatnio zapisane zmiany ze schowka, a następnie usunąć je z listy zmian
$ git stash show -p stash@{0} | git apply -R    #Może się zdarzyć sytuacja, w której nałożysz zmiany ze schowka, wprowadzisz jakieś inne zmiany, aby potem zechcesz cofnąć zmiany które zostały wprowadzone ze schowka. 
#Git nie udostępnia komendy git unapply, ale można to osiągnąć poprzez pobranie wprowadzonych zmian i nałożenie ich w od tyłu
$ git stash show -p | git apply -R              #jw - Ponownie, jeżeli nie wskażesz schowka, Git założy najnowszy
$ git stash branch galaz                        #tworzenie gałezi ze schowka - stworzy nową gałąź, pobierze ostatnią wersję plików, nałoży zmiany ze schowka, oraz usunie zapisany schowek jeżeli wszystko odbędzie się bez problemów
```
## $ git add
```bash
$ git add -i        #tryb interaktywny gita (lub -interactive)
$ git add -p        #szybkie dodanie części plików do przechowalni
$ git add --patch   #jw
```
## $ git show
```bash
$ git show HEAD@{5}                 #zobacz HEAD sprzed 5 zmian
$ git show master@{yesterday}       #zobaczyć gdzie była gałąź master wczoraj
$ git show HEAD^   #zobaczyć poprzednią zmianę, poprzez użycie HEAD^, co oznacza "rodzic HEAD-a" lub HEAD~
#HEAD~2 - pierwszy rodzic pierwszego rodzica "dziadek", HEAD^^^ - pierwszego rodzica, pierwszego rodzica, pierwszego rodzica, HEAD~3^2 - dostać drugiego rodzica HEAD^^^
$ git show sha1^2   #jw , drugi rodzic sha1
$ git show nazwa_etykiety           #wyswietlenie etykiety po nazwie
$ git show sha1                     #wyswietlanie po sha1
```
## $ git rebase
```bash
$ git rebase master       #zmiana bazy mastera wzięta z galezi w której aktualnie jestem
$ git rebase --onto master server client        #przełącz się do gałęzi klienta, określ zmiany wprowadzone od wspólnego przodka gałęzi client i server, a następnie nanieś te zmiany na gałąź główną master
$ git rebase gałąź_bazowa gałąź_tematyczna      #zmiany z gałęzi tematycznej zostaną zaaplikowane do gałęzi bazowej, bez konieczności przełączania się do gałęzi tematycznej
$ git rebase -i jaki_commit         #rebase w trybie interaktywnym , zmiana kilku commitów
$ git rebase -i HEAD~3              #jw - zmienić ostatnie trzy commity (zakres HEAD~3..HEAD); ale zwróć uwagę na to, że tak naprawdę określiłeś cztery ostatnie commity, rodzica ostatniej zmiany którą chcesz zmienić
#odwrotna kolejność niż w przydaki git log ($ git log --pretty=format:"%h %s" HEAD~3..HEAD) - przy każdym się zatrzymi i trzeba wykonać ręcznie $ git commit --amend i $ git rebase --continue
#UWAGA !! Nie zmieniaj commitów które zdążyłeś już wgrać na centralny serwer
#UWAGA !! Nie zmieniaj bazy rewizji, które wypchnąłeś już do publicznego repozytorium
```
## $ git reflog
```bash
$ git reflog          #zobacz odwołania HEAD-a i innych gałęzi

#UWAGA!! Należy zaznaczyć, że informacje z reflog-a są wyłącznie lokalne - jest to zapis zmian które wprowadzałeś w swoim repozytorium. Referencje nie będą takie same na kopii repozytorium u kogoś innego; a od razu po pierwszym sklonowaniu repozytorium, będziesz miał pusty reflog, ze względu na to, że żadna aktywność nie została wykonana
```
## $ git branch
```bash
$ git branch                #listę istniejących gałęzi
$ git branch -v             #ostatni zatwierdzony zestaw zmian na każdej z gałęzi
$ git branch --merged       #wyświetlenia gałęzi, które już zostały scalone do aktywnej gałęzi
$ git branch --no-merged    #wyświetlenia gałęzi, które nie zostały scalone do aktywnej gałęzi
$ git branch nazwa_galezi           #tworzenie galezi bez przejscia do niej
$ git branch -d nazwa_galezi        #usuwanie galezi
```
## $ git checkout
```bash
$ git checkout -- benchmarks.rb     #cofanie zmian w zmodyfikowanym pliku - wszelkie zmiany jakie wykonałeś w pliku przepadają
$ git checkout nazwa_galezi         #przełacznie sie na gałąź
$ git checkout -b nazwa_galezi      #tworzenie gałezi z przelaczeniem na nią
$ git checkout -b galaz origin/master       #towrzenie i przejscie do nowej gałęzi z gałęzią źródłową master na serwerze
```
## $ git push
```bash
$ git push [nazwa-zdalnego-repo] [nazwa-gałęzi]     #wypchnięcie do serwera
$ git push nazwa_zdal_repo nazwa_etykiety           #wypchniecie na serwer etykiety
$ git push nazwa_zdal_repo --tags                   #wypchnięcie wszystkich etykiet
$ git push origin serverfix:innanazwagałęzi
$ git push origin local:remote                      #wypchniecie lokalnej gałęzi local pod zdalną remote
$ git push nazwa_zdalnego_repo :galaz               #usunąć zdalną gałąź
$ git push -f galaz galaz1                          #Z powodu zmiany bazy ("rebase") na gałęzi, musisz użyć przełącznika -f do komendy push, tak abyś mógł nadpisać gałąź galaz1 na serwerze, commitem który nie jest jej potomkiem. Alternatywą może być wysłanie tych zmian do nowej gałęzi na serwerze (np. nazwanej galaz2)
```
## $ git pull
```bash
$ git pull nazwa-zdaln-repo       #fetch+merge
```
## $ git fetch
```bash
$ git fetch nazwa-zdaln-repo      #pobiera wszystko co jest na zdalnym a nie ma u mnie
```
## $ git merge
```bash
$ git merge origin/serverfix                    #scalić pobraną pracę z bieżącą gałęzią roboczą
$ git merge --no-commit --squash featureB       #pobiera wszytstkie zmiany z gałęzi oraz łaczy je w jedną nie włączoną na gałezi na której obecnie jesteś , brak zapisu info o commit (można zrobić zmiane bez comita)
$ git merge nazwa_galezi                        #scalenie galezi nazwa_galezi na galezia na której jestem aktualnie
```
## $ git rm
```bash
$ git rm plik               #dodaje do poczekalni operacje usunięcia
$ git rm --cached plik      #przeniesienie z poczekalni do roboczego
$ git rm log/\*.log         #usuwa wszystkie pliki z rozszerzeniem .log, znajdujące się w katalogu log/
$ git rm \*~                #Usuwa ona wszystkie pliki, które kończą się tyldą ~
```
## $ git mv
```bash
$ git mv file_from file_to        #zmiany nazwy pliku w repozytorium
```
## $ git reset
```bash
$ git reset HEAD plik.rb          #usuwanie z poczekalni
```
## $ git apply
```bash
$ git apply /tmp/patch-ruby-client.patch      #akceptacja zmian przysłanych maile, nie tworzy commita (zaakceptuj lub odrzuć wszystko)
$ git apply --check łata.patch                #zobaczyć, czy łata nałoży się czysto zanim ją zaaplikujesz
```
## $ git am
```bash
$ git am       #akceptacja wszystkich z mboxa
```
## $ git request-pull
```bash
$ git request-pull origin/master galaz        #generuje podsumowanie zmian miedzy galezia lokalna galaz a repo master
```
## $ git cherry-pick
```bash
$ git cherry-pick sha1       #To pobierze tylko zmiany z jednego commita sha1, ale otrzyma nową sumę SHA-1, ze względu na nową datę nałożenia
```
## $ git describe
```bash
$ git describe master        #generowanie numeru kompilacji
```
## $ git format-patch
```bash
$ git format-patch -M origin/master       #towrzenie łatek do wysłania do opiekuna
```
## $ git rev-parse
```bash
$ git rev-parse galaz        #jeżeli chciałbyś zobaczyć, na jaką sumę SHA-1 wskazuje dana gałąź, lub jeżeli chcesz zobaczyć na jaką sumę SHA-1 każdy z tych przykładów się rozwiązuje
```
## Tools
```bash
$ gitk                #program z interfejsem graficznym-historia rewizji
$ git mergetool       #narzędzie do rozwiązywania konflików scalania

#UWAGA!! Przeniesienie do poczekalni oznacza w Gicie rozwiązanie konfliktu>
```
## Help
```bash
$ git help <polecenie>        #pomoc
$ git <polecenie> --help      #pomoc
$ man git-<polecenie>         #pomoc
```