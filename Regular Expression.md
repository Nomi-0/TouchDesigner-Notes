# Regular Expression

### 网站
[在线正则测试](https://tool.oschina.net/regex/)
[表达式全集](https://tool.oschina.net/uploads/apidocs/jquery/regexp.html)

处理以下css文件
    #myXDToTD {
        position: absolute;
        width: 1080px;
        height: 1080px;
        background-color: rgba(255,255,255,1);
        overflow: hidden;
        --web-view-name: myXDToTD;
        --web-view-id: myXDToTD;
        --web-scale-on-resize: true;
        --web-enable-deep-linking: true;
      }
    #myButton2 {
        position: absolute;
        width: 469px;
        height: 214px;
        left: 172px;
        top: 257px;
        overflow: visible;
      }

#### 找到所有my开头的id
    p1 = re.compile(r"#my(.*?)[ {]", re.S)
    ops = re.findall(p1, string)
    >> ['XDToTD', 'Button2', 'Button']

#### 找到所有my开头id对应的样式
    p1 = re.compile(r"#my(.*?)[}]", re.S) #最小匹配
    styles = re.findall(p1, string)
    >>['XDToTD {\n\t\tposition: absolute;\n\t\twidth: 1080px;\n\t\theight: 1080px;\n\t\tbackground-color: rgba(255,255,255,1);\n\t\toverflow: hidden;\n\t\t--web-view-name: myXDToTD;\n\t\t--web-view-id: myXDToTD;\n\t\t--web-scale-on-resize: true;\n\t\t--web-enable-deep-linking: true;\n\t', 
      'Button2 {\n\t\tposition: absolute;\n\t\twidth: 469px;\n\t\theight: 214px;\n\t\tleft: 172px;\n\t\ttop: 257px;\n\t\toverflow: visible;\n\t', 
      'Button {\n\t\tposition: absolute;\n\t\twidth: 469px;\n\t\theight: 214px;\n\t\tleft: 172px;\n\t\ttop: 581px;\n\t\toverflow: visible;\n\t']

#### 截取特定字符串后面的内容,包括换行符
    for i in range(len(ops)):
      print('--------------------------------------')
      text = styles[i]
      myop = ops[i]
      p0 = re.compile(r'(?<='+myop+' {)[\s\S]*', re.S)
      cont = re.findall(p0, text)
    >>--------------------------------------
      ['\n\t\tposition: absolute;\n\t\twidth: 1080px;\n\t\theight: 1080px;\n\t\tbackground-color: rgba(255,255,255,1);\n\t\toverflow: hidden;\n\t\t--web-view-name: myXDToTD;\n\t\t--web-view-id: myXDToTD;\n\t\t--web-scale-on-resize: true;\n\t\t--web-enable-deep-linking: true;\n\t']
      --------------------------------------
      ['\n\t\tposition: absolute;\n\t\twidth: 469px;\n\t\theight: 214px;\n\t\tleft: 172px;\n\t\ttop: 257px;\n\t\toverflow: visible;\n\t']
      --------------------------------------
      ['\n\t\tposition: absolute;\n\t\twidth: 469px;\n\t\theight: 214px;\n\t\tleft: 172px;\n\t\ttop: 581px;\n\t\toverflow: visible;\n\t']
