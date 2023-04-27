# 1. Найдите полный хеш и комментарий коммита, хеш которого начинается на aefea. 
```
user@epd3hictjchne13shf71:~/terraform$ git show aefea
commit aefead2207ef7e2aa5dc81a34aedf0cad4c32545
Author: Alisdair McDiarmid <alisdair@users.noreply.github.com>
Date:   Thu Jun 18 10:29:58 2020 -0400

    Update CHANGELOG.md
```
# 2. Какому тегу соответствует коммит 85024d3?
```
user@epd3hictjchne13shf71:~/terraform$ git show 85024d3
commit 85024d3100126de36331c6982bfaac02cdab9e76 (tag: v0.12.23)
```
# 3. Сколько родителей у коммита b8d720? Напишите их хеши.
```
user@epd3hictjchne13shf71:~/terraform$ git show b8d720^
commit 56cd7859e05c36c06b56d013b55a252d0bb7e158
Merge: 58dcac4b79 ffbcf55817
Author: Chris Griggs <cgriggs@hashicorp.com>
Date:   Mon Jan 13 13:19:09 2020 -0800

    Merge pull request #23857 from hashicorp/cgriggs01-stable

    [cherry-pick]add checkpoint links
```

или
```
user@epd3hictjchne13shf71:~/terraform$ git log --pretty=format:%P -n 1 "b8d720"
56cd7859e05c36c06b56d013b55a252d0bb7e158 
9ea88f22fc6269854151c571162c5bcf958bee2b
```
# 4.Перечислите хеши и комментарии всех коммитов которые были сделаны между тегами v0.12.23 и v0.12.24.
```
user@epd3hictjchne13shf71:~/terraform$ git log --oneline --left-right v0.12.23...v0.12.24
> 33ff1c03bb (tag: v0.12.24) v0.12.24
> b14b74c493 [Website] vmc provider links
> 3f235065b9 Update CHANGELOG.md
> 6ae64e247b registry: Fix panic when server is unreachable
> 5c619ca1ba website: Remove links to the getting started guide's old location
> 06275647e2 Update CHANGELOG.md
> d5f9411f51 command: Fix bug when using terraform login on Windows
> 4b6d06cc5d Update CHANGELOG.md
> dd01a35078 Update CHANGELOG.md
> 225466bc3e Cleanup after v0.12.23 release
```
# 5.Найдите коммит в котором была создана функция func providerSource, ее определение в коде выглядит так func providerSource(...) (вместо троеточего перечислены аргументы).
```
user@epd3hictjchne13shf71:~/terraform$ git log -S 'func providerSource' --oneline
5af1e6234a main: Honor explicit provider_installation CLI config when present
8c928e8358 main: Consult local directories as potential mirrors of providers
```
```
user@epd3hictjchne13shf71:~/terraform$ git show 8c928e8358 | grep providerSource
+       providerSrc := providerSource(services)
```
# 6.Найдите все коммиты в которых была изменена функция globalPluginDirs.
```
user@epd3hictjchne13shf71:~/terraform$ git grep --break --heading -n -e 'globalPluginDirs'
commands.go
88:             GlobalPluginDirs: globalPluginDirs(),
446:    helperPlugins := pluginDiscovery.FindPlugins("credentials", globalPluginDirs())
```
```
internal/command/cliconfig/config_unix.go
34:             // FIXME: homeDir gets called from globalPluginDirs during init, before

plugins.go
12:// globalPluginDirs returns directories that should be searched for
18:func globalPluginDirs() []string {
```
```
user@epd3hictjchne13shf71:~/terraform$ git log -L :globalPluginDirs:plugins.go | grep commit
commit 78b12205587fe839f10d946ea3fdc06719decb05
commit 52dbf94834cb970b510f2fba853a5b49ad9b1a46
commit 41ab0aef7a0fe030e84018973a64135b11abcd70
commit 66ebff90cdfaa6938f26f908c7ebad8d547fea17
commit 8364383c359a6b738a436d1b7745ccdce178df47
```
# 7.Кто автор функции synchronizedWriters?
```
user@epd3hictjchne13shf71:~/terraform$ git log -S 'func synchronizedWriters' --oneline
bdfea50cc8 remove unused
5ac311e2a9 main: synchronize writes to VT100-faker on Windows
```
```
user@epd3hictjchne13shf71:~/terraform$ git show 5ac311e2a9
commit 5ac311e2a91e381e2f52234668b49ba670aa0fe5
Author: Martin Atkins <mart@degeneration.co.uk>
```
