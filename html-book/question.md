
### doctype 的意义是什么


<details>
<summary>查看答案</summary>


- 让浏览器以标准模式渲染

- 让浏览器知道元素的合法性

</details>

### HTML、XHTML、HTML5的区别


<details>
<summary>查看答案</summary>


- HTML 属于 SGML

- XHTML 属于 XML，是 HTML 进行 XML 严格化的结果

- HTML5 不属于SGML，也不属于 XML（HTML5有自己独立的一套规范），比 XHTML 宽松。

</details>

### HTML5 有什么新的变化

<details>
<summary>查看答案</summary>


- 新的语义化元素

- 表单增强

- 新的API：离线、音视频、图形、实时通信、本地存储、设备能力等。

</details>

### em 和 i 的区别

<details>
<summary>查看答案</summary>


共同点：二者都是表示斜体。

区别：

- em 是语义化的标签，表示强调。

- i 是纯样式的标签，表示斜体。HTML5 中不推荐使用。

</details>

### 语义化的意义是什么

<details>
<summary>查看答案</summary>


- 开发者容易理解，便于维护。

- 机器（搜索引擎、读屏软件等）容易理解结构

- 有助于 SEO

</details>

### 哪些元素可以自闭合

<details>
<summary>查看答案</summary>


> 自闭合的元素中不能再嵌入别的元素。且 HTML5 中要求加斜杠。

- 表单元素 input

- 图片 img

- br、hr

- meta、link

</details>

### form 表单的作用

<details>
<summary>查看答案</summary>


- 直接提交表单

- 使用 submit / reset 按钮

- 便于浏览器保存表单

- 第三方库（比如 jQuery）可以整体获取值

- 第三方库可以进行表单验证

所以，如果我们是通过 Ajax 提交表单数据，也建议加上 form。

</details>
