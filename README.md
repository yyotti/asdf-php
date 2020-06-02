<div>
PHP5.6がビルドできない問題を何とか解決しようと努力してみました。一応、PHP5.6.36以上であればビルドできるようになったと思います。

**何か不都合があっても全て自己責任でお願いします。**

**動作確認はLinux Mint 19.3でしかやってません。**

## オリジナルからの変更点
* どうやらPHP5.6はOpenSSL-1.0でないとビルドできないようなので、OpenSSL-1.1に対応させるパッチを当てる処理を追加しました。
  - [参考(http://www.nsl.tuis.ac.jp/xoops/modules/xpwiki/?PHP)](http://www.nsl.tuis.ac.jp/xoops/modules/xpwiki/?PHP)

## Prerequirements
**オリジナルの方も要確認。**

事前にインクルードパスを調整しておく必要があります。私の場合はLinuxbrewで`curl`を入れていてそちらを参照したいので下記のようにします。
```sh
sudo ln -s "$(brew --prefix curl)/include/curl" /usr/local/include/curl
```

普通に`apt`で入れた場合はどうなるのか確認していませんが、どこかで下記のようにすると見た記憶があります。
```sh
sudo ln -s /usr/lib/x86_64-linux-gnu/curl /usr/local/include/curl
```

## インストール時
5.6系の場合は環境変数`CPPFLAGS`をセットしてやらないとエラーになると思います。
```sh
CPPFLAGS="$CPPFLAGS -DU_USING_ICU_NAMESPACE=1 " asdf install php [version]

# or

export CPPFLAGS="$CPPFLAGS -DU_USING_ICU_NAMESPACE=1 "
asdf install php [version]
```

</div>
<hr />
<div align="center">
<h1>asdf-php</h1>
<span><a href="https://www.php.net">PHP</a> plugin for asdf version manager</span>
</div>
<hr />

[![GitHub Workflow Status](https://img.shields.io/github/workflow/status/asdf-community/asdf-php/Main%20workflow?style=flat-square)](https://github.com/asdf-community/asdf-php/actions)
[![All Contributors](https://img.shields.io/badge/all_contributors-15-orange.svg?style=flat-square)](#contributors-)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)
[![License](https://img.shields.io/github/license/asdf-community/asdf-php?style=flat-square&color=brightgreen)](https://github.com/asdf-community/asdf-php/blob/master/LICENSE)

_Original version of this plugin created by
[@Stratus3D](https://github.com/Stratus3D)_

## Prerequirements

Check the [.github/workflows/workflow.yml](.github/workflows/workflow.yml) for
dependencies, paths, and environment variables needed to install the latest PHP
version. To be honest, supporting a major version other than the latest without
any extra work from the user is an endless endeavor that won't ever really work
too well. It's not that we don't support them at all, but it's almost impossible
for us to support them.

## Installation

```bash
asdf plugin-add php https://github.com/asdf-community/asdf-php.git
```

#### Note: PHP-PEAR

PHP PEAR is down without ETA for when the server will be back. To install PHP
without PEAR you can specify a `PHP_WITHOUT_PEAR` variable with any value
(except no), eg:

```bash
PHP_WITHOUT_PEAR=yes asdf install php <version>
```

## Usage

Check [asdf](https://github.com/asdf-vm/asdf) readme for instructions on how to
install & manage versions.

## Contributors ✨

Thanks goes to these wonderful people
([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="https://stratus3d.com/"><img src="https://avatars1.githubusercontent.com/u/1520926?v=4" width="100px;" alt=""/><br /><sub><b>Trevor Brown</b></sub></a><br /><a href="https://github.com/asdf-community/asdf-php/commits?author=Stratus3D" title="Code">💻</a></td>
    <td align="center"><a href="https://oscardearriba.com"><img src="https://avatars3.githubusercontent.com/u/563391?v=4" width="100px;" alt=""/><br /><sub><b>Óscar de Arriba</b></sub></a><br /><a href="https://github.com/asdf-community/asdf-php/commits?author=odarriba" title="Documentation">📖</a> <a href="#maintenance-odarriba" title="Maintenance">🚧</a> <a href="#infra-odarriba" title="Infrastructure (Hosting, Build-Tools, etc)">🚇</a></td>
    <td align="center"><a href="https://bsky.moe"><img src="https://avatars3.githubusercontent.com/u/38746192?v=4" width="100px;" alt=""/><br /><sub><b>BSKY</b></sub></a><br /><a href="https://github.com/asdf-community/asdf-php/commits?author=imbsky" title="Code">💻</a> <a href="https://github.com/asdf-community/asdf-php/commits?author=imbsky" title="Documentation">📖</a> <a href="#maintenance-imbsky" title="Maintenance">🚧</a> <a href="#infra-imbsky" title="Infrastructure (Hosting, Build-Tools, etc)">🚇</a></td>
    <td align="center"><a href="https://www.bixels.nl"><img src="https://avatars1.githubusercontent.com/u/334814?v=4" width="100px;" alt=""/><br /><sub><b>Choong Wei Tjeng</b></sub></a><br /><a href="https://github.com/asdf-community/asdf-php/commits?author=bixelsnl" title="Documentation">📖</a> <a href="#infra-bixelsnl" title="Infrastructure (Hosting, Build-Tools, etc)">🚇</a></td>
    <td align="center"><a href="http://eher.com.br"><img src="https://avatars0.githubusercontent.com/u/398034?v=4" width="100px;" alt=""/><br /><sub><b>Alexandre Eher</b></sub></a><br /><a href="https://github.com/asdf-community/asdf-php/commits?author=EHER" title="Code">💻</a> <a href="https://github.com/asdf-community/asdf-php/commits?author=EHER" title="Documentation">📖</a> <a href="#infra-EHER" title="Infrastructure (Hosting, Build-Tools, etc)">🚇</a></td>
    <td align="center"><a href="http://salzsee.info"><img src="https://avatars0.githubusercontent.com/u/99911?v=4" width="100px;" alt=""/><br /><sub><b>Ben Rexin</b></sub></a><br /><a href="https://github.com/asdf-community/asdf-php/commits?author=salzig" title="Code">💻</a> <a href="https://github.com/asdf-community/asdf-php/commits?author=salzig" title="Documentation">📖</a></td>
    <td align="center"><a href="https://turnintocoders.it"><img src="https://avatars3.githubusercontent.com/u/65402?v=4" width="100px;" alt=""/><br /><sub><b>Matteo Giaccone</b></sub></a><br /><a href="https://github.com/asdf-community/asdf-php/commits?author=matjack1" title="Documentation">📖</a> <a href="#infra-matjack1" title="Infrastructure (Hosting, Build-Tools, etc)">🚇</a></td>
  </tr>
  <tr>
    <td align="center"><a href="http://caleb.fm"><img src="https://avatars1.githubusercontent.com/u/4692?v=4" width="100px;" alt=""/><br /><sub><b>Caleb Land</b></sub></a><br /><a href="https://github.com/asdf-community/asdf-php/commits?author=caleb" title="Code">💻</a> <a href="https://github.com/asdf-community/asdf-php/commits?author=caleb" title="Documentation">📖</a></td>
    <td align="center"><a href="https://medium.com/@belaustegui"><img src="https://avatars3.githubusercontent.com/u/2965623?v=4" width="100px;" alt=""/><br /><sub><b>Cristian Álvarez Belaustegui</b></sub></a><br /><a href="https://github.com/asdf-community/asdf-php/commits?author=crbelaus" title="Code">💻</a></td>
    <td align="center"><a href="https://www.mokhan.ca"><img src="https://avatars1.githubusercontent.com/u/80475?v=4" width="100px;" alt=""/><br /><sub><b>mo khan</b></sub></a><br /><a href="https://github.com/asdf-community/asdf-php/commits?author=mokhan" title="Code">💻</a></td>
    <td align="center"><a href="http://christopherjones.us"><img src="https://avatars0.githubusercontent.com/u/115515?v=4" width="100px;" alt=""/><br /><sub><b>Chris Jones</b></sub></a><br /><a href="https://github.com/asdf-community/asdf-php/commits?author=magikid" title="Documentation">📖</a></td>
    <td align="center"><a href="https://me.baldarn.com/"><img src="https://avatars0.githubusercontent.com/u/2814802?v=4" width="100px;" alt=""/><br /><sub><b>lorenzo farnararo</b></sub></a><br /><a href="https://github.com/asdf-community/asdf-php/commits?author=baldarn" title="Code">💻</a></td>
    <td align="center"><a href="https://github.com/j-dexx"><img src="https://avatars3.githubusercontent.com/u/6691543?v=4" width="100px;" alt=""/><br /><sub><b>James</b></sub></a><br /><a href="https://github.com/asdf-community/asdf-php/commits?author=j-dexx" title="Code">💻</a></td>
    <td align="center"><a href="https://trevorsuarez.com/"><img src="https://avatars3.githubusercontent.com/u/742384?v=4" width="100px;" alt=""/><br /><sub><b>Trevor N. Suarez</b></sub></a><br /><a href="https://github.com/asdf-community/asdf-php/commits?author=Rican7" title="Code">💻</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://github.com/triptec"><img src="https://avatars0.githubusercontent.com/u/240159?v=4" width="100px;" alt=""/><br /><sub><b>Andreas Franzén</b></sub></a><br /><a href="https://github.com/asdf-community/asdf-php/commits?author=triptec" title="Code">💻</a> <a href="#infra-triptec" title="Infrastructure (Hosting, Build-Tools, etc)">🚇</a></td>
  </tr>
</table>

<!-- markdownlint-enable -->
<!-- prettier-ignore-end -->
<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the
[all-contributors](https://github.com/all-contributors/all-contributors)
specification. Contributions of any kind welcome!

## License

Licensed under the
[Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0).
