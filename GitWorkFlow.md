# NoSqlEpt DB Work Flow

### 说明

- 开发环境基于 C++,协作模式为 Gitflow 工作流模式.

### 工作方式

` Gitflow ` 工作流使用 `Github` 上的仓库作为所有开发成员的交互中心,开发者在本地工作并 `push` 分支到远程仓库.

#### 历史分支

`Gitflow` 工作流使用两个分支来记录项目的历史. `master` 分支为主分支,存放对外发布的历史,任何时候在该分支下拉取的项目都是稳定的版本. `develop` 分支为开发分支,用于日常开发,存放最新的开发版本.

#### 功能分支

新功能的开发是基于 `develop` 分支的,每次开发者新增功能的时候,使用 `develop` 分支作为父分支创建新的 `featurer` 分支,在 `feature` 分支中实现目标功能.完成功能开发后,开发者向 `develop` 分支发送 `pull request` 请求,接受其他开发者审核通过后,合并到 `develop` 分支,并删除当前的 `feature` 分支.

```
$ git checkout develop 				  	//切换到 develop 分支
$ git pull 							  	//更新本地 develop 分支到最新状态
$ git flow feature start some-feature 	//创建新分支 some-feature
$ git branch							//切换到新分支进行开发
$ git push								//发布新分支,在 github 上切换到 develop 分支
										//进行 pull request
$ git checkout develop 					//切换到本地 develop
$ git pull 								//更新本地 develop 到最新状态
$ git branch -d some-feature			//删除功能分支
```

#### 发布分支

当 `develop`  分支上有了足够多的功能,就可以从 `develop` 分支上 `checkout`  一个新的发布分支 `relesse`. 发布分支上不允许添加新的功能, 只允许做 `Bug` 修复/文档生成和其他面向发布任务. 直到完成发布工作,将发布分支合并到 `master` 分支并分配一个版本号打好 `Tag` , 另外,新建发布分支后对发布分支做的修改都需要合并回 `develop` 分支. (发布分支的意义在于, 开发团队在完善当前发布版本的同时, 可以继续开发下个版本的功能).

```
$ git checkout develop 					//切换到 develop 分支
$ git pull //更新
$ git flow release start '1.0.0' 		//创建发布分支
$ git flow release finish '1.0.0' 		//结束发布分支
```

#### 维护分支

当 `release` 分支发现 bug , 而 `develop` 分支正在开发新功能, 无法发布时, 需要创建维护分支 `hotfix`.  

*具体操作请潇哥补充* 