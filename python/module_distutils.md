# distutil 模块详解

## 概要
用来发布你的Python模块
> using the Distutils to distribute your Python modules, concentrating on the role of developer/distributor

## 1.3. General Python terminology (Python中基本术语的区分)
package ：包，存在__init__.py文件的文件夹

root package : sys.path中的路径

> If you’re reading this document, you probably have a good idea of what modules, extensions, and so forth are. Nevertheless, just to be sure that everyone is operating from a common starting point, we offer the following glossary of common Python terms:
module
the basic unit of code reusability in Python: a block of code imported by some other code. Three types of modules concern us here: pure Python modules, extension modules, and packages.
pure Python module
a module written in Python and contained in a single .py file (and possibly associated .pyc and/or .pyo files). Sometimes referred to as a “pure module.”
extension module
a module written in the low-level language of the Python implementation: C/C++ for Python, Java for Jython. Typically contained in a single dynamically loadable pre-compiled file, e.g. a shared object (.so) file for Python extensions on Unix, a DLL (given the .pyd extension) for Python extensions on Windows, or a Java class file for Jython extensions. (Note that currently, the Distutils only handles C/C++ extensions for Python.)
package
a module that contains other modules; typically contained in a directory in the filesystem and distinguished from other directories by the presence of a file __init__.py.
root package
the root of the hierarchy of packages. (This isn’t really a package, since it doesn’t have an __init__.py file. But we have to call it something.) The vast majority of the standard library is in the root package, as are many small, standalone third-party modules that don’t belong to a larger module collection. Unlike regular packages, modules in the root package can be found in many directories: in fact, every directory listed in sys.path contributes modules to the root package.


## 1.4. Distutils-specific terminology （发布时所使用的术语）

module distribution：a collection of Python modules distributed together as a single downloadable resource and meant to be installed en masse.a single module distribution may contain zero, one, or many Python packages.
distribution root : 其实就是setpu.py文件所在的目录



## 参考
* https://www.zhihu.com/question/59209129
* https://docs.python.org/2/distutils/index.html