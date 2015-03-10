### 弹出带两个按钮提示框的js代码

```
/**
 * Created by 
 */
$(document).ready(
    function(){
        $(window).scroll(
            function()
            {
                $('#remmindBox').css('top',($(window).scrollTop()+$(window).height()/6) + 'px')
            }
        );
    }
);
$('#boxClose').live('click',function(){boxClose();});
function getRemindBox(boxName)
{
    $('body').append('<div id="reLockbg"></div>');//页面元素锁定
    $('body').append('<div id="remmindBox"></div>');
    $('#remmindBox').append('<div id="boxTop"><span id="boxName">'+boxName+'</span><a title="关闭" href="javascript:void()" id="boxClose">X</a></div>');
    $('#remmindBox').append('<div id="boxData"></div>');
    setCss();//初始化样式
}
//初始化样式
function setCss()
{
    //锁定背景样式
    $('#reLockbg').css({'background-color':'#666','width':'100%','left':'0','top':'0','filter':'alpha(opacity=50)','opacity':'0.5','z-index':'1','position':'fixed!important','position':'absolute','height':$(document).height()+'px'});
    //提示框样式
    $('#remmindBox').css({'width':'30%','height':'200px','border':'none','left':'35%','background':'#fff','position':'absolute','z-index':'101','text-align':'left','top':$(window).height()/6 + 'px'});
    //顶部导航样式
    $('#boxTop').css({'height':'30px','background':'#eee'});
    //跳框标题样式
    $('#boxName').css({'float':'left','font-size':'14px','font-weight':'800','line-height':'30px','color':'#333','margin-left':'10px'});
    //关闭按键样式
    $('#boxClose').css({'float':'right','line-height':'30px','color':'#333','text-decoration':'none','padding':'0 10px'})
    //数据框样式
    $('#boxData').css({'font-size':'14px','margin':'40px'});
}
//关闭按钮鼠标事件
$('#boxClose').live('mouseover',function(){$(this).css('color','red')});
$('#boxClose').live('mouseout',function(){$(this).css('color','#333')});

function boxClose()
{
    $('#reLockbg').remove();
    $('#remmindBox').remove();
}

$('#btn').live('click',function(){window.location.href="https://google.com";});


function divShow()
{
    getRemindBox('提示信息');
    var str="";
    str='<p>需要提示的信息内容</p>';
    str+='<p></p>';
    str+='<p align="center" style="margin:40px;" ><input type="button" style="height:30px;width:80px;" id="btn" value="跳转按钮"><input style="margin-left:50px;height:30px;width:80px;" type="button" value="返 回" onclick="javascript:history.back()" style="margin-left:100px"></p>';
    $('#boxData').html(str);
}
```