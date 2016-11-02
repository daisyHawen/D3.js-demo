#说明
此专题是关于D3.js学习的专题
#入门
##基本语法
demo2
｀｀｀
d3.select(".container").append("h1")
    .text("Hello, world!")
    .style("text-align", "center")
    .style("line-height", "320px")
    .style("font-size", "100px")
    .style("transform", "rotate(-180deg) scale(0.001, 0.001)")
  .transition()
    .duration(1500)
    .style("transform", null);
｀｀｀
d3.delect 选择一个元素
d3.append 在选择的元素后面插入一个新的h1元素
  .text   添加h1的text 
  .style  添加h1的style
  。可以添加transform属性，旋转属性，以及缩放
  .duration 持续时间

##进阶
demo1
与jquery的对比
d3很重要的enter属性
详细说明见demo1的注释

##更多例子
demo4、demo5参照《D3入门指南》中的demo
演示了如何设置了bar；
以及如何在bar上方添加数据；
以及如何如何画圆；

demo演示了，如何随机生成一个圆，以及拖动一个圆。

＃D3高级进阶
##实现拖动
```
d3.behavior.drag() 来定义 drag 行为
```
除了 drag 事件之外，还有 dragstart 和 dragend 事件，
```
svg.selectAll("circle")
    .data(circles)
    .enter().append("circle")
    .attr("cx", function(d) {
        return d.x;
    })
    .attr("cy", function(d) {
        return d.y;
    })
    .attr("r", radius)
    .style("fill", function(d, i) {
        return color(i);
    })
    .call(d3.drag()
        .on("start", dragstarted)
        .on("drag", dragged)
        .on("end", dragended));

function dragstarted(d) {
    d3.select(this).raise().classed("active", true);
}

function dragged(d) {
    d3.select(this).attr("cx", d.x = d3.event.x).attr("cy", d.y = d3.event.y);
}

function dragended(d) {
    d3.select(this).classed("active", false);
}
```
例如上面的代码就为drag实现了三个阶段
```
    .call(d3.drag()
        .on("start", dragstarted) //拖动开始
        .on("drag", dragged)      //拖动过程
        .on("end", dragended));   //拖动释放
```
说明：在本案例中的d3版本不支持 d3.behavior.drag() 来定义 drag 行为

