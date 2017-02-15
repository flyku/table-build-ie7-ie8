#README.md
#行列可选------可以根据行生成表格，也可以根据列生成表格。
#需要在table（cellLists,false）传入布尔值
#不传false，默认false以列生成表格，传入true时以行生成表格
###使用方法
#引入js
```
<script type="text/javascript" charset="utf-8" src="table.js"></script>
###或者amd cmd commonjs规范引入
```
###根据二维数组生成对应表格
```可以设置colspan rowspan```
```使用方法```

###配置二维数组
```ini
var cellLists = [
        cell(["1", "2", "3", "4", "5"].concat([{
            html: "加赛"
        }]), [{
            html: '局',
            rowSpan: 3
        }]),
        cell([1, 2, 3, 4, 5].concat([{
            html: 10,
            colSpan: 4
        }]), [{
            html: "flyku",
            colSpan: 5
        }].concat([{
            html: "环数",
            colSpan: 4
        }]).concat([{
            html: "第一箭"
        }])),

        cell([1, 2, 3, 4, 5], [{
            html: '第二箭'
        }]),
        cell([1, 2, 3, 4, 5], [{
            html: '第三箭'
        }]),
        cell([1, 2, 3, 4, 5], [{
            html: '总计'
        }]),
        cell([1, 2, 3, 4, 5].concat([{
            html: "加赛"
        }]), [{
            html: '得分',
            rowSpan: 2
        }]),

        cell([1, 2, 3, 4, 5].concat([{
            html: 222
        }]), [{
            html: '比分',
            rowSpan: 3
        }]),

        cell([1, 2, 3, 4, 5].concat([{
            html: 1
        }]), [{
            html: "flyku",
            colSpan: 5
        }].concat([{
            html: "得分",
            rowSpan: 2
        }])),
        cell([1, 2, 3, 4, 5].concat([{
            html: 10,
            colSpan: 4
        }]), [{
            html: '环数',
            colSpan: 4
        }].concat([{
            html: "第一箭"
        }])),
        cell([1, 2, 3, 4, 5], [{
            html: '第二箭'
        }]),
        cell([1, 2, 3, 4, 5], [{
            html: '第三箭'
        }]),
        cell([1, 2, 3, 4, 5], [{
            html: '总计'
        }])
    ];
```
###生成table
```ini
var data = table(cellLists,false);
#默认false以列生成表格，true时以行生成表格
```
###插入html（使用模板插入，underscore模板等等！）
```ini
var str = '<table padding="0" cellspacing="0" border="0">
    <thead></thead>
    <tbody>
        <% for(var i=0;i<data.rows.length;i++){%>
            <tr>
                <% for(var j=0;j<data.rows[i].length;j++){%>
                    <td rowspan="<%= data.rows[i][j].rowSpan || 1 %>" colspan="<%= data.rows[i][j].colSpan || 1 %>" data-id="<%= data.rows[i][j].uniqId %>">
                        <%= data.rows[i][j].html %>
                    </td>
                <% }; %>
            </tr>
        <% }; %>
    </tbody>
</table>';
    var template = _.template(str);
    document.getElementById("table").innerHTML = template(data);
```

###效果预览collook.jpg
![image](https://raw.githubusercontent.com/flyku/table-build-ie7-ie8/master/look.jpg)


###生成table
```ini
var data = table(cellLists,true);
#默认false以列生成表格，true时以行生成表格
```
###插入html（使用模板插入，underscore模板等等！）
```ini
var str = '<table padding="0" cellspacing="0" border="0">
    <thead></thead>
    <tbody>
        <% for(var i=0;i<data.rows.length;i++){%>
            <tr>
                <% for(var j=0;j<data.rows[i].length;j++){%>
                    <td rowspan="<%= data.rows[i][j].rowSpan || 1 %>" colspan="<%= data.rows[i][j].colSpan || 1 %>" data-id="<%= data.rows[i][j].uniqId %>">
                        <%= data.rows[i][j].html %>
                    </td>
                <% }; %>
            </tr>
        <% }; %>
    </tbody>
</table>';
    var template = _.template(str);
    document.getElementById("table").innerHTML = template(data);
```

###效果预览rowlook.jpg
![image](https://raw.githubusercontent.com/flyku/table-build-ie7-ie8/master/rowlook.jpg)
