文档头部描述了文档的基本属性和信息
## <title>
>描述了文档的标题
## <meat> 中的属性：

#### charset
`<meat charset = "utf-8">`
>定义文档的字符编码为utf-8
注：需写在第一行，位于在<title>前 

#### keywords
`<meat name= "keywords" content= "关键字..." >`
>描述文档基本信息。keywords（关键字）属性可理解为content的名字。content里面的内容主要是给搜索引擎用的；描述网页中的关键字。

#### description
`<meat name= "description" content= "主要内容...">`
>描述文档信息。description（描述）属性可理解为content的名字；content里面的内容主要是给搜索引擎用的。描述网页的主要内容。

#### author
`<meat name= "author" content= "作者信息...">`
>>描述文档信息。author（名字）属性可理解为content的名字；content里面的内容主要是给搜索引擎用的。描述网页作者的。

#### robots
`<meta name="robots" contect= "all|none|index|noindex|follow|nofollow">`
- all：文件将被检索，且页面上的链接可以被查询；
- none：文件将不被检索，且页面上的链接不可以被查询；
- index：文件将被检索；
- follow：页面上的链接可以被查询；
- noindex：文件将不被检索，但页面上的链接可以被查询；
- nofollow：文件将不被检索，页面上的链接可以被查询。

#### viewport
`<meat name= "viewport" content="width= device-width, initial-scale=1, maximum-scale=1">`
>设定移动端视口的宽高、缩放等。
- width：控制 viewport 的大小，可以指定的一个值，如果 600，或者特殊的值，如 device-width 为设备的宽度（单位为缩放为 100% 时的 CSS 的像素）。
- initial-scale：初始缩放比例，也即是当页面第一次 load 的时候缩放比例。
- maximum-scale：允许用户缩放到的最大比例。
- minimum-scale：允许用户缩放到的最小比例。
- user-scalable：用户是否可以手动缩放
--- 
## link
>定义文档和外部资源的关系，最常见的用法是链接样式表。
- href 规定被链接文档的位置（url）。
- media：规定被链接文档将被显示在什么设备上。
- rel:规定当前文档与被链接文档之间的关系。	值：alternate、author、help、icon、
、licence、next、pingback、prefetch、prev
、search、sidebar、stylesheet、tag

- type： 规定被链接文档的 MIME 类型