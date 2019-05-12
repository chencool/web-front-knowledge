title与h1的区别、b与strong的区别、i与em的区别？

title 是浏览器窗口网页标题

h1 是文本标签 默认与word的h1相似为最大的标题显示

b 为文本加粗标签 与word的加粗功能相似

strong 为强调语气， 也是为文本加粗 与b标签是有不同

i 标签为斜体 常用于阿里图标 和图片

em 标签为 斜体 用于文本斜体较多

title 是浏览器窗口网页标题

table的作用和优缺点是什么呢？

优点：写表格方便快捷，样式统一，居中对齐，减少使用div，seo较好
缺点：需要写的内容较多。

html5中的form怎么关闭自动完成？

设置form的autocomplete属性为off。

如何实现浏览器内多个标签页之间的通信？

第一种——调用localStorage

在一个标签页里面使用 localStorage.setItem(key,value)添加（修改、删除）内容； 

在另一个标签页里面监听 storage 事件。 

即可得到 localstorge 存储的值，实现不同标签页之间的通信。

标签页1：

<input id="name"> 

<input type="button" id="btn" value="提交">  

<script type="text/javascript">
  
    $(function(){    
    
        $("#btn").click(function(){    
        
            var name=$("#name").val();
            
            localStorage.setItem("name", name);  
            
        }); 
        
    }); 
    
</script>  

标签页2：

<script type="text/javascript"> 
	
    $(function(){   
		
        window.addEventListener("storage", function(event){ 
				
            console.log(event.key + "=" + event.newValue);  
						
        }); 
				
    });  
		
</script> 

第二种——调用cookie+setInterval()

将要传递的信息存储在cookie中，每隔一定时间读取cookie信息，即可随时获取要传递的信息。

页面1：

<input id="name">  
<input type="button" id="btn" value="提交">  
<script type="text/javascript">  
    $(function(){    
        $("#btn").click(function(){    
            var name=$("#name").val();    
            document.cookie="name="+name;    
        });    
    });    
</script>  
页面2：

<script type="text/javascript">  
    $(function(){   
        function getCookie(key) {    
            return JSON.parse("{\"" + document.cookie.replace(/;\s+/gim,"\",\"").replace(/=/gim, "\":\"") + "\"}")[key];    
        }     
        setInterval(function(){    
            console.log("name=" + getCookie("name"));    
        }, 10000);    
    });  
</script>  
