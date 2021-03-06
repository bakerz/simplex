---
title: 最简图片裁剪-预览-上传
category: 技术
tags: [JavaScript, Canvas, HTML]
monthLast: true
---

```
'use strict';

require('bootstrap');
require('../plugins/jquery.form/jquery.form');

var loading = require('../modules/loading');

var btn = $('form .upload-img');
var file = $('#upload-modal [type=file]');
var modal = $('#upload-modal');

var canvas = document.getElementById('canvas');
var con = canvas.getContext('2d');

$(btn).on('click', function() {
    modal.modal('show');
});

$('#file').change(function(){
    var file = this.files[0];
    
    var reader = new FileReader();
    reader.onload = function(){
        var url = reader.result;
        setImageURL(url);
    };
    reader.readAsDataURL(file);
});

var image = new Image();
function setImageURL(url) {
    image.src = url;
    
    loading.show();
    imgLoad(image, function() {
        
        if(image.naturalWidth) {
            var nw = image.naturalWidth;
            var nh = image.naturalHeight;
        } else {
            var img = new Image();
            img.src = image.src;
            var nw = img.width;
            var nh = img.height;
        }
        
        var size = (nw < nh) ? nw : nh;
        var clip = (nw < nh) ? 'height' : 'width';
        
        if(clip == 'width') {
            con.drawImage(image, (nw - size)/2, 0, size, size, 0, 0, 100, 100);
        } else {
            con.drawImage(image, 0, (nh - size)/2, size, size, 0, 0, 100, 100);
        }
        
        var base64_src = canvas.toDataURL();
        $('.modal input[name=image]').attr('value', base64_src);
        submitImg(base64_src);
        loading.hide();
    });
}

function submitImg(src) {
    $('.modal form').on('submit', function() {
        loading.show();
        
        $('.user-avatar').html('<img src="'+ src +'">');
        
        $(this).ajaxSubmit({
            success: function(data) {
                modal.modal('hide');
                
                if (data.success === true) {
                    $('[name=Avatar]', $(btn).parents('form')).val(data.path);
                } else {
                    console.log(data);
                }
                
                loading.hide();
            }
        });
        
        return false;
    });
}

// 检测图片加载完成
function imgLoad(img, callback) {
    var timer = setInterval(function() {
        if(img.complete) {
            callback(img);
            clearInterval(timer);
        }
    }, 50);
}
```