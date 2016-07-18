##appmodelTree
使用封装好的appmodeltree

前提本模块只适用于appmodel下面的tree

 

1. 首先在需要使用的模块下添加pom引用

    ```
    <dependency>
        <groupId>com.gaoxin</groupId>
        <artifactId>appmodel-tree</artifactId>
        <version>1.0.0</version>
    </dependency>
    ```

2. 之后在index下添加js引用,同时之前必须引用过jstree的相关js和css

 ```javascript
    <script src="assets/global/scripts/appmodel-tree.js" type="text/javascript"></script>
 ```

3. 使用方法
   使用本js首先要设置路径

   可以在你的jsp页面下
    ```javascript
    appModelTree.setPath('<%= request.getContextPath()%>');
    ```
  也可以在你的js内部
    ```javascript
     appModelTree.setPath(configMap.path);
    ```
 上面是前提, 本js有两种方式生成tree
 1. 简单的使用
     ```javascript
     //设置路径
     appModelTree.setPath(configMap.ContextPath);
     //生成tree
        appModelTree.Tree( $tree,'realline_tree',true,false);
    ```
    appModelTree.Tree()是一个可以直接生成tree的函数
    4个参数
     > `$tree` 需要生成tree的jQuery对象，一个div 
     > syscode 系统参数的编码，来供查询是什么应用模型的tree
     > withtag 查询出来的tree是否带有指标，ture 或 false
     > ischeckbox 是否带有复选框，这里是简单的复选框，复杂的用法请使用`$.appmodeltree`这个函数
 
 2. 扩展jstree ,和之前jstree使用方式一样
     ```javascript
     jqueryMap.$tree_index.appmodeltree({
          withtag: true,
          syscode: 'realline_tree',
          'core': {
            'themes': {
              'responsive': false
            },
            'check_callback': true,
            'data': function(obj, callback) {
              return callModelTreeData(obj, callback);
            }
          },
          'types': {
            'node': {
              'icon': 'fa fa-folder icon-state-warning icon-lg'
            },
            'index': {
              'icon': 'fa fa-line-chart icon-state-success icon-lg'
            }
          },
          'plugins': ['wholerow', 'types']
    });
     ```
     多了两个自定的属性
   >  withtag 系统参数的编码，来供查询是什么应用模型的tree
     syscode 查询出来的tree是否带有指标，ture 或 false
     
jstree的api
https://www.jstree.com/api/
    
比如点击节点的时候的event
```
jqueryMap.$tree_index.on('select_node.jstree', function(event, node) {
      console.log(node);
      }
    });
```