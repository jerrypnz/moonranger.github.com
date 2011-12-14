.. include:: <s5defs.txt>

======================
可爱的reStructuredText
======================

----------------------------
实用主义者的文档解决方案
----------------------------

:Author: Jerry Peng <pr2jerry@gmail.com>


用什么写文档？
==============
* WYSIWYG字处理工具
    * M$ Word
    * OpenOffice Writer
* 纯文本的文档格式
    * XML类标记语言（Docbook, HTML）
    * LaTeX
    * 轻量级标记语言
* Embedded in Code


WYSIWYG字处理软件
=================
* What You See Is What You Get
    * Not always true
* 大量的鼠标点击
* 繁复的格式调整
* 二进制的文件格式
    * 无法diff，不利于作版本控制


WYSIWYG字处理软件
=================
* 花架子功能，影响心情（个人对此深恶痛绝）
    * 首字母自动大写
    * 自动识别为日期
    * 电脑软件是不应该“自作聪明”的
        * 用户知道自己要干什么，你一机器指手画脚干嘛！
* 总而言之，无法让人集中于主要问题上
    * 让人流畅地将idea变成文档才是最重要的


LaTeX
=====
* 学习曲线让人望而却步
    * 投入／回报不成比例
* 工具链复杂
    * 宏包
    * 中文问题

LaTeX
=====
* 适合产出印刷物，学术论文
* 不适合日常的工作文档，项目文档
    * 效率不高
* 没玩过LaTeX，所以轻拍…… ;-)
    * 期待TJLUG的LaTeX用户分享一下经验，让我入个门


XML/HTML
========
* 没人直接用HTML写文档吧？
    * 但HTML是常见的输出格式
* XML文档解决方案——Docbook
    * 一切都满足需求
    * 但它是坑爹的XML！
        * 标签要闭合
        * 源文件可读性不好


轻量级标记语言
==============
* Markdown
* Vimwiki
* reStructuredText
    * 今天的主角


代码中嵌入文档
==============
* 只适合API文档
* 方便和代码保持同步
* 通过工具生成


实用主义者的标准
================
* 必须是纯文本
    * 可以用最趁手的编辑器，比如：Vim
    * 轻松做版本控制
* 数据和表现分离
    * 文档源文件只包含结构化的数据
    * 以样式表、主题或者命令行选项的方式来控制字体、颜色等
    * 同样的源文件结合不同的样式得到不同的展现


实用主义者的标准
================
* 源文件的可读性要好
    * HTML/XML第一个被排除掉
* 可以输出到多种格式
    * HTML, pdf是必须的
    * S5——这样就可以做slides了
    * LaTeX——可以做进一步排版，方便打印或者输出高质量的pdf
* 易学易用，上手快，编辑效率高
    * 所以排除了LaTeX


主角登场：reStructuredText
==========================
* Powered by Python Technology
    * python-docutils
* 基于StructuredText和Setext标记语言强化而来
* 源文件可读性很好
* 保持简单的同时功能强大
* 可以输出为多种格式
    
    .. image:: rst2xxx.png


安装python-docutils
===================
* 通过发行版的包管理器直接安装::

    sudo apt-get install python-docutils
    sudo apt-get install rst2pdf

* 通过Python pip来安装::

    sudo pip install docutils
    sudo pip install rst2pdf

* 建议用pip + virtualenv来管理Python包


reStructuredText格式简介
========================
* 很多格式与Markdown等其他轻量标记语言类似
* 符合直觉，很容易记忆
* 这里简要介绍，详细的文档请Google之
    * reStructuredText官网 [1]_.
    * Quick reStructuredText [2]_.

.. [1] http://docutils.sourceforge.net/rst.html
.. [2] http://docutils.sourceforge.net/docs/user/rst/quickref.html


标题
====
* 标题的格式::

    ========
    文档标题
    ========

    ----------
    文档副标题
    ----------

* 文档标题和副标题通常用在封面页


标题
====
* 标题的格式::

    一级标题
    ========

    二级标题
    --------

    三级标题
    ````````

* 这些是文档各节（section）的标题
* 文档的目录根据这些标题生成


标题
====
* 可以使用字母数字以外的可打印ACSII字符，官方推荐的是以下字符::

    Recommended choices are 
    "``= - ` : ' " ~ ^ _ * + # < >``"

* 标题前后的符号数目必须大于等于标题文本的长度


段落
====
* 段落的格式::

    段落不需要特殊标记，用空行来分割，
    段落内的换行是被忽略的，因此源文件
    可以很好地控制一行的长度。

    这是一段。

    这是第二段。

        段落可以缩进，通常用来表达引用的文字。


行内标记
========
* 用来实现斜体、粗体、引用、脚注、引用等等::

    *斜体*, **粗体**, hyperlink_, 脚注 [3]_

    .. [3] 脚注的正文
    .. _hyperlink:  http://jerrypeng.me

* 下面是实际的效果

    *斜体*, **粗体**, hyperlink_, 脚注 [3]_

* 还有更多其他标记，请参考文档

.. [3] 脚注的正文
.. _hyperlink:  http://jerrypeng.me


项目编号
========
* 项目符号的格式::

    前面的段落，下面需要一个空行。

    - 项目一
    - 项目二
    - 项目符号后必须跟一个空格
    - 一组项目的前后要加上空行
    - 可以用*, -, +来作为bullet，如果有多行，
      必须和上一行的文字对其，像你看到的这样。

    后面的段落，上面需要一个空行。


数字编号
========
* 数字编号的格式::
    
    规则和项目编号一样，只不过用数字来替代项目符号

    1. 第一项
    2. 第二项
    3. 格式是数字后面跟一个'.'，再跟一个空格
    #. 用#替代数字来自动编号


表格
====
* 表格的格式::

    +------------+------------+-----------+ 
    | Header 1   | Header 2   | Header 3  | 
    +============+============+===========+ 
    | body row 1 | column 2   | column 3  | 
    +------------+------------+-----------+ 
    | body row 2 | Cells may span columns.| 
    +------------+------------+-----------+ 
    | body row 3 | Cells may  | - Cells   | 
    +------------+ span rows. | - contain | 
    | body row 4 |            | - blocks. | 
    +------------+------------+-----------+


表格
====
* 看起来是这样的:

    +------------+------------+-----------+ 
    | Header 1   | Header 2   | Header 3  | 
    +============+============+===========+ 
    | body row 1 | column 2   | column 3  | 
    +------------+------------+-----------+ 
    | body row 2 | Cells may span columns.| 
    +------------+------------+-----------+ 
    | body row 3 | Cells may  | - Cells   | 
    +------------+ span rows. | - contain | 
    | body row 4 |            | - blocks. | 
    +------------+------------+-----------+


简单表格
========
* 简单表格的格式::

    =====  =====  ====== 
       Inputs     Output 
    ------------  ------ 
      A      B    A or B 
    =====  =====  ====== 
    False  False  False 
    True   False  True 
    False  True   True 
    True   True   True 
    =====  =====  ======


简单表格
========
* 看起来是这样的:

    =====  =====  ====== 
       Inputs     Output 
    ------------  ------ 
      A      B    A or B 
    =====  =====  ====== 
    False  False  False 
    True   False  True 
    False  True   True 
    True   True   True 
    =====  =====  ======


指令（Directives）
==================
* 指令是基本的标记之外的扩展机制
* 有一组标准的指令
    * 目录
    * 图片，内嵌代码
    * 公式
    * 标准指令大全 [4]_
* 不同的工具可以实现自己独特的指令以实现高级功能

.. [4] http://docutils.sourceforge.net/docs/ref/rst/directives.html


指令的格式
==========
* 指令的格式如下::

    .. directive_type :: directive
       block


指令示例: 嵌入图片
==================
* 嵌入图片::

    .. image:: funny.gif
       :height: 100px
       :width: 100px
       :alt: funny cat picture
       :align: center

.. image:: funny.gif
   :height: 100px
   :width: 100px
   :alt: funny cat picture
   :align: center


指令实例: 嵌入代码
==================
* 嵌入代码::

    .. code:: python

        def say_hello():
            print 'Hello, reStructuredText'

        if __name__ == '__main__':
            say_hello()


* docutils-0.9才开始支持，无法给演示了……


Enough for Now
==============
* 先介绍这么多
* 使用时现查手册就足够了
* 很容易记忆


reStructuredText工具链
======================
* TBD

