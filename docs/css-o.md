# CSS代码逻辑组织
将CSS代码逻辑拆分为5类组织

### 1. 重置
填补各个浏览器中默认样式的不一致，比如YUI的reset 和 font 样式文件

### 2. 布局
页面元素布局样式，比如 header footer  article aside nav 等页面布局元素。或者YUI的grid通用布局方法
可以考虑使用`lay-`前缀

### 3. 模块
将布局内的UI元素拆分成若干个小模块，模块是页面信息展现方式的抽象，比如头、内容、尾部的信息块，导航信息块，列表信息块，表格信息块。

  <div class="mod">
    <div class="hd"></div>
    <div class="bd"></div>
    <div class="ft"></div>
  </div>

  .mod {}
  .mod .hd {}
  .mod .bd {}
  .mod .ft {}

可以考虑使用 `mod-` 前缀声明模块。比如 歌曲列表`mod-songlist` 电影列表`mod-moivelist` 图片列表`mod-piclist` 评论表单`mod-frm-common` 等等

### 4. 主题
主题类表达页面的视觉风格样式，比如颜色，背景图片，按钮样式等，可以考虑使用`them-`前缀
一个模块可以搭配不同的主题风格，就像Windows窗体的GUI可以多种皮肤。

### 5. 状态
视觉元素中有很多动态的展现，比如展开，选中，激活，不可用，高亮等。这类样式就是状态。

建议表示状态
  
  .on, .active, .selected, .hili, .hide, .disabled

综合实例

    <div id="doc">
      <div class="hd">
        header
      </div>
      <div class="bd lay-g1">
        <article class="lay-i-1">
          <div class="mod-pics them-1">
            <div class="hd">
              <h3>title</h3>
            </div>
            <div class="bd">
              <ul class="list">
                <li><a href="#"><img src="/pic.jpg" alt="pic name"></a></li>
                <li><a href="#"><img src="/pic.jpg" alt="pic name"></a></li>
                <li><a href="#"><img src="/pic.jpg" alt="pic name"></a></li>
              </ul>
            </div>
            <div class="ft">
              <a href="#">more</a>
            </div>
          </div>
        </article>
        <aside class="lay-i-2">
          aside
        </aside>
      </div>
      <div class="ft">
      footer
      </div>
    </div>


