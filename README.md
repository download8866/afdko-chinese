[![PyPI](https://img.shields.io/pypi/v/afdko.svg)](https://pypi.org/project/afdko)

[![Travis](https://travis-ci.org/adobe-type-tools/afdko.svg?branch=develop)](https://travis-ci.org/adobe-type-tools/afdko)
[![Appveyor](https://ci.appveyor.com/api/projects/status/qurx2si4x54b97mt/branch/develop?svg=true)](https://ci.appveyor.com/project/adobe-type-tools/afdko/branch/develop)
[![CircleCI](https://circleci.com/gh/adobe-type-tools/afdko/tree/develop.svg?style=svg)](https://circleci.com/gh/adobe-type-tools/afdko/tree/develop)
[![Azure Pipelines](https://dev.azure.com/adobe-type-tools/afdko/_apis/build/status/adobe-type-tools.afdko?branchName=develop)](https://dev.azure.com/adobe-type-tools/afdko/_build/latest?definitionId=1&branchName=develop)

[![Coverage](https://codecov.io/gh/adobe-type-tools/afdko/branch/develop/graph/badge.svg)](https://codecov.io/gh/adobe-type-tools/afdko/branch/develop)

[![Language grade: C/C++](https://img.shields.io/lgtm/grade/cpp/g/adobe-type-tools/afdko.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/adobe-type-tools/afdko/context:cpp)
[![Language grade: Python](https://img.shields.io/lgtm/grade/python/g/adobe-type-tools/afdko.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/adobe-type-tools/afdko/context:python)
[![Total alerts](https://img.shields.io/lgtm/alerts/g/adobe-type-tools/afdko.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/adobe-type-tools/afdko/alerts/)

Adobe Font Development Kit for OpenType (AFDKO)
===============================================

AFDKO是一组用于从 PostScript 和 TrueType 字体数据中设计OpenType字体文件的工具。

This repository contains the data files, Python scripts, and sources for
the command line programs that comprise the AFDKO. The project uses the
[Apache 2.0 OpenSource license](LICENSE.md).

Please refer to the
[AFDKO Overview](https://adobe-type-tools.github.io/afdko/AFDKO-Overview.html)
for a more detailed description of what is included in the package.

Please see the
[wiki](https://github.com/adobe-type-tools/afdko/wiki)
for additional information, such as links to reference materials and related
projects.

安装设置
------------

The AFDKO requires [Python](http://www.python.org/download) 3.6
or later.

Releases are available on the [Python Package
Index](https://pypi.python.org/pypi/afdko) (PyPI) and can be installed
with [pip](https://pip.pypa.io).

### 安装

**选项 1 (推荐)**

- 创建虚拟环境:

        python3 -m venv afdko_env

- Activate the virtual environment:

    - macOS & Linux

            source afdko_env/bin/activate

    - Windows

            afdko_env\Scripts\activate.bat

- Install [afdko](https://pypi.python.org/pypi/afdko):

        pip install afdko

Installing the **afdko** inside a virtual environment prevents conflicts
between its dependencies and other modules installed globally.

**Option 2**

Install [afdko](https://pypi.python.org/pypi/afdko) globally:

    pip install --user afdko

### 更新

Use the `-U` (or `--upgrade`) option to update the afdko (and its
dependencies) to the newest stable release:

    pip install -U afdko

To get pre-release and in-development versions, use the `--pre` flag:

    pip install -U afdko --pre

### 卸载

To remove the afdko package use the command:

    pip uninstall afdko

从源文件中编译
-----------------

首先，您必须为您的平台安装了开发工具。

在MacOS环境中，你需要在终端中执行以下命令:

    xcode-select --install

在Linux (Ubuntu 17.10 LTS or later)环境中, 你需要在终端中执行以下命令:

    apt-get -y install python3.6
    apt-get -y install python-pip
    apt-get -y install python-dev

在Windows环境中, 你需要用到 Visual Studio 2017 软件.

To build the **afdko** from source, clone the [afdko GitHub
repository](https://github.com/adobe-type-tools/afdko), ensure the `wheel`
module is installed (`pip install wheel`), then `cd` to the top-level
directory of the afdko, and run:

    pip install .

**注意**

It's not possible to install the afdko in editable/develop mode using
`pip install -e .` ; this is because the toolkit includes binary C executables
which setup.py tries to install in the bin/ (or Scripts/) folder, however
this process was only meant to be used with text-based scripts (either
written in Python or a shell scripting language). To work around this problem
(which really only impacts the few core afdko developers who need to get live
feedback as they modify the source files) you can use alternative methods like
exporting a PYTHONPATH, using a .pth file or similar hacks.
For further details read [this comment](https://github.com/adobe-type-tools/afdko/pull/677#issuecomment-436747212).

版本2.5.x的主要更改
--------------------------------

* The AFDKO has been restructured so that it can be installed as a Python
package. It now depends on the user's Python interpreter, and no longer
contains its own Python interpreter.

* Two programs, **IS** and **checkoutlines** were dropped because their source
code could not be open-sourced. These tools are available in [release version
2.5.65322 and older](https://github.com/adobe-type-tools/afdko/releases?after=2.6.22).

**注意**

If you install the old AFDKO as well as the new PyPI afdko package, the tools from
the newer version will take precedence over the older. This happens because pip
adds the afdko's package path at the beginning of the system's PATH environment
variable, whereas the old installer adds it at the end; this modification to PATH
is not undone by the uninstaller. If you want to completely remove the path to the
newer version, you will have to edit the PATH. On the Mac, this means editing the
line in your login file that sets the PATH variable. On Windows, this means editing
the PATH environment variable in the system's Control Panel.
