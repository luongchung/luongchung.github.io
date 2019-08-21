---
layout: post
title:  "Hiệu ứng 3D CSS"
date:   2017-09-17 13:50:29
categories: android
---
<html>
    <head>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
  <link rel="stylesheet" href="/css/style.css" type="text/css" media="screen" />
  <script type="text/javascript" charset="utf-8">
    function hasClassName(inElement, inClassName)
    {
        var regExp = new RegExp('(?:^|\\s+)' + inClassName + '(?:\\s+|$)');
        return regExp.test(inElement.className);
    }

    function addClassName(inElement, inClassName)
    {
        if (!hasClassName(inElement, inClassName))
            inElement.className = [inElement.className, inClassName].join(' ');
    }

    function removeClassName(inElement, inClassName)
    {
        if (hasClassName(inElement, inClassName)) {
            var regExp = new RegExp('(?:^|\\s+)' + inClassName + '(?:\\s+|$)', 'g');
            var curClasses = inElement.className;
            inElement.className = curClasses.replace(regExp, ' ');
        }
    }

    function toggleClassName(inElement, inClassName)
    {
        if (hasClassName(inElement, inClassName))
            removeClassName(inElement, inClassName);
        else
            addClassName(inElement, inClassName);
    }

    function toggleShape()
    {
      var shape = document.getElementById('shape');
      if (hasClassName(shape, 'ring')) {
        removeClassName(shape, 'ring');
        addClassName(shape, 'cube');
      } else {
        removeClassName(shape, 'cube');
        addClassName(shape, 'ring');
      }
      
      var stage = document.getElementById('stage');
      if (hasClassName(shape, 'ring'))
        stage.style.webkitTransform = 'translateZ(-200px)';
      else
        stage.style.webkitTransform = '';
    }
    function downloadLink()
    {
      location.href = 'http://luongchung.github.io/zip/3d-css.zip';
    }
  </script>
</head>
    <body>

  <div style="text-align: right;padding: 15px;"><button onclick="toggleShape()">Đổi kiểu</button>&nbsp;<button onclick="downloadLink()">Download code</button></div>
  
  <div id="container">
    <div id="stage">
      <div id="shape" class="cube backfaces">
        <div class="plane one"></div>
        <div class="plane two"></div>
        <div class="plane three"></div>
        <div class="plane four"></div>
        <div class="plane five"></div>
        <div class="plane six"></div>
        <div class="plane seven"></div>
        <div class="plane eight"></div>
        <div class="plane nine"></div>
        <div class="plane ten"></div>
        <div class="plane eleven"></div>
        <div class="plane twelve"></div>
      </div>
    </div>
  </div>
  <div style="position: absolute;top: 15px;left: 15px;height: 30px;width: 300px;" id="playAudio">
    <audio controls autoplay loop><source src="/music/Girls_Like_You.mp3" type="audio/mpeg"></audio>
  </div>
  <!--script>
    var isChrome = /Chrome/.test(navigator.userAgent) && /Google Inc/.test(navigator.vendor);
    if(isChrome) {
        document.getElementById('playAudio').remove();
        document.write('<iframe src="/music/Girls_Like_You.mp3" allow="autoplay loop" style="display:none"></iframe>');
    }
  </script-->
</body>
</html>