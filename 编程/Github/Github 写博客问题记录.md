# Github 写博客问题记录

在 Github 上使用 markdown 文件写博客以后，碰到了一些使用问题，记录在这里：

## 图片路径不允许空格

如果你在 markdown 文件中插入图片：`![image](relative path/image.png)`，这在 Typora 和 VS Code 中或许能正常显示，但是在 Github 上只会显示原 markdown 代码。因为 Github 路径是不允许空格的，必须使用百分比编码转义：`![image](relative%20path/image.png)`。

## 网址文本必须使用 <> 封闭

如果你在 markdown 文件中输入一个网址，在 Github 上可能会将后续文本全部判定为网址的一部分，比如 https://example.com/test，即使使用中文逗号分隔，后面的文本依然可能会被当做网址的一部分。
因此必须使用尖括号来封闭包裹网址 <https://example.com/test>，这样才能正常显示。
