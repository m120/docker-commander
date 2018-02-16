# docker-commander
Docker Commander

## Desc
dockerで良く使うコマンドを [go-task](https://github.com/go-task/task) でまとめました。

dockerコマンドで何かするとき、コンテナIDやイメージ名をいちいち調べるのが面倒なので、その悩みを解決してみました。
* 例えば
  * BuildしてRun
  * Stop
  * コンテナにShellで入る
  * コンテナにコマンド実行

## Usage
### Preparation
- go-task install
  - [go-task:Installation](https://github.com/go-task/task#installation)

- Taskvars.yml に必要な情報を記載します。

### Usage
#### Task List
* タスク一覧を表示。詳細は `taskfile.yml` を参照

```
 $ task -l
  * build:        Docker Build
  * build-run:    Build and Run.
  * default:      Docker Controler
  * ps:           Dokcer ps for {{.DOCKER_IMAGE}}
  * rmi:          Delete Dokcer image
  * run:          Dokcer run
  * shell:        Get into a container
  * stop:         Dokcer stop
```

例えばBuildしたい場合は、
```
 $ task build
```

#### 少し便利な使いかた
* BuildしてRun
```
 $ task build-run
```

* コンテナのシェルに入りたい
 * コンテナにBashがinstallされている必要があります

 ```
  $ task shell
 ```

* コンテナに対してコマンドを実行(ex: date)
```
 $ task shell command=date
 Sat Dec 13 06:33:30 JST 1980
```
