---
title: python虚拟环境
date: 2024-01-17 22:00:16
tags: python
categories: python编程
---
# PyCharm 配置 Python 解释器

 前面几节我们把如何创建一个项目、以及可以为项目填充哪些元素为大家介绍完了。但还留了一个问题， 当我们在创建"Hello World" 项目时，当输完文件名后，需要选择解释器 ，当时只让大家选择了一个系统的解释器。那么这个解释器到底是什么呢？这节将详细介绍什么是解释器？有哪些类型？这些解释器又有什么不同？
## 1. 什么是解释器？
 解释器就是帮助我们将 Python 代码，也就是 .py 文件，交给机器可以执行的工具。
我们知道，计算机的 CPU 其实是很笨的，它只能读懂 0 和 1 这样的二进制编码文件。但是我们编写代码的时候肯定不能使用二进制，所以就诞生了像 Python 和 Java 这样的高级语言来辅助我们编程。但是代码写出来之后计算机理解不了又执行不了怎么办？这个时候就需要有一个东西将 Python 代码解释成计算机可以读懂并执行的内容，这个东西就是解释器。
## 2. 支持的解释器类型
 想要在 PyCharm 中使用 Python 代码，需要至少配置一个解释器。要配置的时候，需要指定系统中的 Python 可执行文件的路径。因此，在配置项目解释器之前，需要确保已下载 Python 并安装到系统中，并且知道其路径。我们可以基于不同的 Python 可执行文件创建项目解释器，也可以用同一个 Python 可执行文件创建项目解释器。
 
上图中的 Python.exe 就是 Python 的可执行文件，它存在于你的 Python 安装路径下面。
PyCharm 支持以下解释器类型：
* 标准的 Python 解释器（Python 2.7、Python 3.5-3.8)；
* 其他 Python 实现（IronPython、PyPy、Jython、CPython）；
* 虚拟环境：(Virtualenv, Pipenv, and Conda)；
* 远程 Python 解释器（SSH、Vagrant、WSL（仅适用于 Windows）；
* 基于 Docker 的解释器（Docker、Docker Compose）。

> Tips：后面两种类型，仅在 PyCharm Profession 版本中支持。

## 3. 新项目配置解释器
### 3.1 使用存在的解释器
当创建新项目时，我们需要选择解释器，这时我们可以选择已经存在的解释器。
￼
点击上面的详情按钮，根据不同的解释器类型，已经列出了对应存在的解释器。
￼
### 3.2 使用虚拟环境
基于存在的解释器，可以创建新的虚拟环境。目前 PyCharm 支持三种虚拟环境，分别是Pipenv、Virtualenv 与 Conda。
#### 3.2.1 使用 Pycharm 创建虚拟环境
PyCharm 自带 Virtualenv 不需要单独安装。 它是虚拟环境中最常见的工具，也有许多文档，可解决许多问题，所以非常适合初学者。缺点是由于其简单性，它没有很多功能。
￼
点击 “Create" 按钮，回到主界面 （Tool Windows --> Project --> Project)
￼
会看到项目文件夹下自动创建虚拟环境的目录 venv, 目录结构如下：
￼
更多的细节请参考 Virtualenv。针对其功能的单一性，工具 virtualenvWrapper 是其扩展，有兴趣的同学可以参考。
#### 3.2.2 Pipenv
Pipenv ，全称为 Python Development Workflow for Humans，目的是为开发项目自动创建和管理虚拟环境并管理 Python 包。它就是 virtualenv 和 pip 的集合体，通过创建指定 Python 版本的虚拟环境和安装依赖包，提供各个项目隔离的开发环境。
Pipenv 使用 Pipfile 文件来处理安装的所有包。 如果要在 PyCharm 里使用Pipenv 需要事先安装。更多安装及其它细节参考。
￼
点击 “Create" 按钮， 会在项目文件夹自动创建Pipfile, 目录结构如下：
￼
#### 3.2.3 Conda
在前面的章节我们提到过 Anaconda，它是一个开源的 Python 发行版本，其包含了 conda、Python 等 180 多个科学包及其依赖项。 conda 是包及其依赖项和环境的管理工具。通常只有当使用 Anaconda 时，Conda 才是合适的虚拟环境工具。在 PyCharm 里使用 Conda 需要提前安装。因为其比较大，通常会选择安装 miniconda。安装细节请参考。
￼
点击 “Create", 项目文件中不会创建额外的文件。
￼
#### 3.2.4 总结
在我们创建自己项目时，建议不要选择系统的解释器，而应创建项目自己的虚拟环境，保证各项目的环境独立性。作为初学者，可以优先选择 Virtualenv, 当对虚拟环境有更深了解以后，再选择Pipenv。毕竟Pipenv功能更为强大，在解决依赖性问题上做得更好。
## 4. 修改存在项目的解释器
有时候，我们可能需要修改存在项目的解释器，比如项目原来是基于 Virtualenv 虚拟环境的，后来项目越来越复杂，用 Pipenv 管理包与部署环境会更为合适；再比如项目之前是依托于 Python 2.7 的环境，想要升级为 Python3.0 的环境版本。
### 4.1 更新本地解释器路径
* step1：打开项目， 访问解释器页面，Mac 下依次点击：主PyCharm -> Preference -> Project:项目名 -> Python Intepreter，Windows 和 Linux 下依次点击：File -> Settings -> Project:项目名 ->Python Intepreter。然后点击右上角的齿轮按钮：
￼
* step2：在弹出列表中，单击"Show All…"，会弹出“Project Interpreters" 对话框 。（选择 Add 要求你创建新的解释器）选择 Show All 会先查看有哪些存在的解释器，然后再决定是否创建新的。
￼
* step3：可用的解释器出现在"Project Interpreters"对话框中，在对话框中选择期望的解释器。通过下面一排按钮为当前项目增删改解释器。

￼
**红框中的按钮从上到下分别是：**

1. 增加新的解释器；
2. 删除选中的解释器；
3. 编辑选中的解释器；
4. 与其他项目相关联的环境将不显示；
5. 选中解释器的现有路径将显示在解释器路径对话框中。
点击上图按钮 4， 会显示下图：
￼
点击上图按钮 5， 会显示下图：
￼
### 4.2 Vagrant （仅专业版支持）
PyCharm 支持远程调试，对于已存在的项目可以增加远程环境进行调试。Vagrant 是一款基于 Ruby 用于构建及配置虚拟开发环境的软件，主要以命令行的方式运行。

使用 Oracle 的开源 VirtualBox 虚拟化系统，与 Chef，Salt，Puppet 等环境配置管理软件搭配使用， 可以实行快速虚拟开发环境的构建。PyCharm 可以通过 Vagrant 直接访问VirtualBox 虚拟机，所以需要提前安装 Vagrant 与 VirtualBox， 以及 Vagrant plugin。

PyCharm 已经默认安装了 Vagrant plugin。对于 VirtualBox 与 Vagrant, 根据自己的操作系统，从官网下载VirtualBox 与 Vagrant安装包，然后运行安装包，与其它软件安装是一样的，根据提示点击下一步，就能顺利安装成功。

* step1：执行下面的命令， 启动要使用的虚拟机。（Vagrant命令参考 ）
 > 本地已经准备好了相应BOX文件，也可直接从网上下载，但速度慢。
 1. vagrant box add centos /Users/xuxh/Downloads/Vagrant-CentOS-7.box
 2. vagrant init centos
 3. vagrant up

* step2：打开项目， 访问解释器页面，然后点击齿轮按钮，点击“add"。
￼
* step3：选择左侧面板“vagrant”, 指定虚拟机目录及解释器路径。
￼
### 4.3 Docker (仅专业版支持）
PyCharm 集成了 Docker，允许在 Docker 容器中部署的各种配置开发环境中运行应用程序。当然前提也是需要安装 Docker 与 Docker plugin（PyCharm 已经预装）。
> Tips：关于 Docker 的使用，可以参考这里。

* step1：启动要用的 Docker 容器：
docker run python:latest mytest

* step2：打开项目， 访问解释器页面，然后点击齿轮按钮，点击“add"。（参考前面步骤）
  
* step3：左侧面板点击 Docker，配置 server：

* step4：显示连接成功后，会自动显示对应 docker 服务包含的所有镜像。
* step5：选择在步骤1运行的镜像文件，点击 OK：
￼
## 小结
本节主要针对 Python 解释器做了详细的阐述， 该节的重点及难点是创建虚拟环境解释器。涉及的 Virtualenv、Pipenv 及 Conda 三种虚拟环境，除了要学习本节内容，建议去各自的官网了解更详细的知识。在创建项目时，要优先选择虚拟环境解释器，这样保证系统解释器整洁性，也保证各个项目环境的独立性，在项目移值与部署上都会非常方便。除此以外，本节也涉及到一些专业版才有的功能：Docker 与 Vagrant，应用与理解这些功能需要的背景知识非常多，建议感兴趣的同学先阅读文中给出的文档链接。
￼