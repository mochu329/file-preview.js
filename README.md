# file-preview.js

加入檔案
````html
<script src="jquery-3.1.1.min.js"></script>
<script src="src/jquery.file-preview.js"></script>
````
<br>
接著你需要有類似這樣的結構
````html
<form class="form1">
    <input type="file" name="upload[]" class="upload" multiple>    
</form>
````
<br>
如果只是顯示預覽圖片，jQuery 的部分可以這麼寫
````javascript
$().filePreview({
    parent: ".form1",
    selector: ".upload",
    success: function (key, obj){
        console.log(obj)
    }
})
````
<br>
可以透過 FileReader 取得圖片或檔案的 Base64 編碼，例如打算使用 Base64 作為上傳，可以這麼用
````javascript
$().filePreview({
    parent: ".form1",
    selector: ".upload",
    isReader: true,
    progress: function (key, percent){
        console.log(percent)
    },
    success: function (key, obj){
        console.log(obj)
    }
})
````
<br>
注意，這會犧牲瀏覽器的記憶體效能，檔案過大則會容易造成記憶體不足。通常這用在上傳圖檔時很適合。<br><br>
## file-preview 參數
- parent 綁定的父元素
- selector 綁定的元素
- isReader 是否啟用 FileReader
- progress(key, percent) 若啟用 FileReader 可顯示讀取進度
- success(key, obj) 單一檔案讀取成功所觸發

## Success 可取得的物件
- file 檔案原始資訊
- nameExtension 附檔名
- nameMaster 主檔名
- preview 預覽網址
- size 檔案大小
- type 檔案類型
