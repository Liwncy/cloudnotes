# onenotes
笔记
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8"/>
    <title>Marked in the browser</title>
    <link rel="stylesheet" href="https://cdn.bootcss.com/github-markdown-css/2.10.0/github-markdown.min.css" media="all" />
</head>
<body>
<div id="content" class="markdown-body"></div>
<script src="https://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
<script>
    var url = "https://cdn.jsdelivr.net/gh/liwncy/onenotes/java/Stream.md";
    $.get(url,function(data,status){
        console.log("数据: " + data + "\n状态: " + status);
        document.getElementById('content').innerHTML = marked(data);
    });
</script>
</body>
</html>
```
