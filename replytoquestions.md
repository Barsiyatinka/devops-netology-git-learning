# Домашнее задание к занятию   
**"`Инструменты Git`"** - `Воскобойников Арсений Петрович`  

**Найдите полный хеш и комментарий коммита, хеш которого начинается на `aefea`.**
```
git show aefea  
aefead2207ef7e2aa5dc81a34aedf0cad4c32545    
```
**Ответьте на вопросы.**  
**Какому тегу соответствует коммит 85024d3?**  
```
git show 85024d3  
коммит 85024d3 соответствует тегу tag: v0.12.23  
```
**Сколько родителей у коммита b8d720? Напишите их хеши.**  
```
git show b8d720 смотри merge хэши для этого коммита  
56cd7859e05c36c06b56d013b55a252d0bb7e158  
9ea88f22fc6269854151c571162c5bcf958bee2b  
```
**Перечислите хеши и комментарии всех коммитов, которые были сделаны между тегами v0.12.23 и v0.12.24.**  
```
$ git log --oneline v0.12.23..v0.12.24  
33ff1c03bb (tag: v0.12.24) v0.12.24  
b14b74c493 [Website] vmc provider links  
3f235065b9 Update CHANGELOG.md  
6ae64e247b registry: Fix panic when server is unreachable  
5c619ca1ba website: Remove links to the getting started guide's old location  
06275647e2 Update CHANGELOG.md  
d5f9411f51 command: Fix bug when using terraform login on Windows  
4b6d06cc5d Update CHANGELOG.md  
dd01a35078 Update CHANGELOG.md  
225466bc3e Cleanup after v0.12.23 release  
```
**Найдите коммит, в котором была создана функция func providerSource, её определение в коде выглядит так: func providerSource(...)  (вместо троеточия перечислены аргументы).**  
```
Найдем коммиты где упоминается эта функция.
git log -L :providerSource:provider_source.go -p -s   
commit 5af1e6234ab6da412fb8637393c5a17a1b293663  
commit 92d6a30bb4e8fbad0968a9915c6d90435a4a08f6  
commit 8c928e83589d90a031f811fae52a81be7153e82f - имеет самую раннюю дату. значит в нём эта йункция была сосздана.

git show 8c928e83589d90a031f811fae52a81be7153e82f  
commit 8c928e83589d90a031f811fae52a81be7153e82f  

+// providerSource constructs a provider source based on a combination of the   
+// CLI configuration and some default search locations. This will be the   
+// provider source used for provider installation in the "terraform init"  
+// command, unless overridden by the special -plugin-dir option.  
+func providerSource(services *disco.Disco) getproviders.Source   

```
**Найдите все коммиты, в которых была изменена функция globalPluginDirs.**
```
$ git log -S "globalPluginDirs" --oneline
7c4aeac5f3 stacks: load credentials from config file on startup (#35952)
warning: unable to access 'internal/stacks/stackruntime/internal/stackeval/testdata/sourcebundle/validating/nested_module_diagnostics/invalid_child/.terraform/.gitattributes': Filename too long
warning: unable to access 'internal/stacks/stackruntime/internal/stackeval/testdata/sourcebundle/validating/nested_module_diagnostics/invalid_child/.terraform/modules/.gitattributes': Filename too long
65c4ba7363 Remove terraform binary
125eb51dc4 Remove accidentally-committed binary
22c121df86 Bump compatibility version to 1.3.0 for terraform core release (#30988)
7c7e5d8f0a Don't show data while input if sensitive
35a058fb3d main: configure credentials from the CLI config file
c0b1761096 prevent log output during init
8364383c35 Push plugin discovery down into command package
```
**Кто автор функции synchronizedWriters?**
```
Посмотрим историю коммитов:  
$ git log -S "synchronizedWriters" --oneline
warning: unable to access 'internal/stacks/stackruntime/internal/stackeval/testdata/sourcebundle/validating/nested_module_diagnostics/invalid_child/.terraform/.gitattributes': Filename too long
warning: unable to access 'internal/stacks/stackruntime/internal/stackeval/testdata/sourcebundle/validating/nested_module_diagnostics/invalid_child/.terraform/modules/.gitattributes': Filename too long
bdfea50cc8 remove unused
fd4f7eb0b9 remove prefixed io
5ac311e2a9 main: synchronize writes to VT100-faker on Windows

Смотрим первый коммит в которой есть упоминание функции synchronizedWriters  
$ git show 5ac311e2a9
commit 5ac311e2a91e381e2f52234668b49ba670aa0fe5
Автомр функции:
Author: Martin Atkins <mart@degeneration.co.uk>
```  