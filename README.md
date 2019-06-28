# facyBox
fork from https://github.com/bitbonsai/facyBox,  Added mandatory modal window mode in the every link. support jQuery v1.x - lastest 3.4.1( now 2019-06-28)
# Usage
## 1. Javascript、Css Reference
```html
    <link href="js/plugins/facybox/facybox.css" rel="stylesheet" />
    <link href="js/plugins/facybox/facybox_urls.css" rel="stylesheet" />
    <script src="js/jquery.js" type="text/javascript"></script>
    <script src="js/plugins/facybox/facybox.js"></script>
```
## 2. Javascript
```javascript
<script type="text/javascript">
	jQuery(document).ready(function ($) {
		$('a[rel*=facybox]').facybox({
			noAutoload: true,
			modal: false,
			opacity: 0
		});
	});
</script>
```

## 3.1 Simple Sample ( default inherit global modal )
```html
<p>
    <a href="http://th05.deviantart.net/fs50/300W/f/2009/257/9/5/Alice_cards_by_Sugarock99.jpg" rel="facybox">
        View image 'Alice_cards_by_Sugarock99.jpg' with default modal in the facybox
    </a>
</p>
```
## 3.2 Simple Sample (forceModal="true")
```html
<p>
    <a href="http://th01.deviantart.net/fs50/300W/f/2009/257/7/f/Vintage_by_ValentinaKallias.jpg" rel="facybox" forceModal="true">
        View image 'Vintage_by_ValentinaKallias.jpg' with force-modal in the facybox
    </a>
</p>
```
## 3.3 Advanced Sample (programmatic forceModal="true")
```html
<p>
    <a href="javascript: openRemoteHtml();">
        View 'remote.html' with modal by programmatic in the facybox
    </a>
</p>
```
```javascript
<script type="text/javascript">
    function openRemoteHtml() {
        jQuery.facybox({ ajax: 'demo/remote.html', forceModal: true }, 'my-groovy-style');
    }
</script>
```
## 3.4 Advanced Sample (dynamically set whether the modal is inside the window by programmatic in the facybox)
### 3.4.1( index.html )
```html
<p>
    <a href="javascript: openRemoteModifyUserNameHtml();">
        View 'remote_modify_user_name.html' with non-modal,
        but dynamically set whether the modal is inside the window by programmatic in the facybox
    </a>
</p>
```
### 3.4.2( index.html )
```javascript
<script type="text/javascript">
    function openRemoteModifyUserNameHtml() {
        jQuery.facybox({ ajax: 'demo/remote_modify_user_name.html', forceModal: false }, 'my-groovy-style');
    }
</script>
```
### 3.4.3( remote_modify_user_name.html )
```html
<div>
    <p>
        I'm remote.html, a different file loaded with ajax.
    </p>
    <p>
        Please input your name：<input type="text" name="userName" id="userName" value="zhangsan" disabled="disabled" />
    </p>
    <p>
        <input type="button" value="edit" id="btnEdit" onclick="editInFacyBox();" />
        &nbsp;&nbsp;&nbsp;
        <input type="button" value="close" id="btnClose" onclick="closeFacyBox();" />
    </p>
</div>
```
### 3.4.4( index.html )
```javascript
<script type="text/javascript">
    jQuery(document).ready(function ($) {
        $('a[rel*=facybox]').facybox({
            noAutoload: true,
            modal: false,
            opacity: 0
        });
    });
    function closeFacyBox() {
        $.facybox.close();
    }
    function removeDisabledAttr(jObj) {
        if (typeof (jObj) == 'undefined') {
            return;
        }
        if (typeof (jObj.removeProp) != 'undefined') {
            jObj.removeProp("disabled");
        }
        if (typeof (jObj.removeAttr) != 'undefined') {
            jObj.removeAttr("disabled");
        }
    }
    function editInFacyBox() {
        var jUserName = $("#userName");
        if (jUserName.length == 0) {
            alert("The element 'userName' of page can not be found.");
            return;
        }
        removeDisabledAttr(jUserName);
        $.facybox.setToModalByDynamic(true); 
    }
</script>
```
