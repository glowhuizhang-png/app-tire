<!DOCTYPE html>
<html lang="zh">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>轮胎扫码系统 Pro</title>

<script src="https://unpkg.com/html5-qrcode"></script>
<script src="https://cdn.sheetjs.com/xlsx-0.20.0/package/dist/xlsx.full.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.10.1/jszip.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/FileSaver.js/2.0.5/FileSaver.min.js"></script>

<style>
body{font-family:Arial;background:#f2f2f2;padding:15px;}
.card{background:#fff;padding:15px;border-radius:12px;margin-bottom:15px;}
button{width:100%;padding:15px;margin-top:10px;font-size:18px;border:none;border-radius:10px;}
.primary{background:#007aff;color:#fff;}
.success{background:#34c759;color:#fff;}
.danger{background:#ff3b30;color:#fff;}
#reader{width:100%;}
img{width:100%;border-radius:10px;margin-top:10px;}
.count{font-size:22px;font-weight:bold;}
.small{font-size:12px;color:#666;}
</style>
</head>

<body>

<div class="card">
<h2>轮胎扫码系统 Pro</h2>

<div>今日数量：<span class="count" id="count">0</span></div>

<button class="primary" onclick="startScanner()">开始扫描</button>

<div id="reader"></div>

<h3>当前条码</h3>
<div id="barcode">未扫描</div>

<input type="file" accept="image/*" capture="environment" id="cameraInput" style="display:none">

<button class="success" onclick="takePhoto()">拍照</button>

< img id="preview">

<button class="primary" onclick="saveData()">保存</button>
</div>

<div class="card">
<button onclick="exportExcel()">导出 Excel</button>
<button onclick="exportZip()">导出 ZIP</button>
<button class="danger" onclick="clearAll()">清空数据</button>
</div>

<div class="card">
<h3>历史记录</h3>
<div id="history"></div>
</div>

<script>

let scanner = null;
let currentBarcode = "";
let currentImage = "";
let records = JSON.parse(localStorage.getItem("tire") || "[]");

// ===== 扫码 =====
function startScanner(){
    scanner = new Html5Qrcode("reader");

    Html5Qrcode.getCameras().then(() => {
        scanner.start(
            { facingMode: "environment" },
            { fps: 10, qrbox: 250 },
            (text) => {
                currentBarcode = text;
                document.getElementById("barcode").innerText = text;
                scanner.stop();
                navigator.vibrate?.(150);
            }
        );
    });
}

// ===== 拍照 =====
function takePhoto(){
    document.getElementById("cameraInput").click();
}

document.getElementById("cameraInput").addEventListener("change", e=>{
    const file = e.target.files[0];
    if(!file) return;

    const reader = new FileReader();
    reader.onload = e=>{
        currentImage = e.target.result;
        document.getElementById("preview").src = currentImage;
    };
    reader.readAsDataURL(file);
});

// ===== 保存 =====
function saveData(){

    if(!currentBarcode){
        alert("请先扫码");
        return;
    }

    if(!currentImage){
        alert("请先拍照");
        return;
    }

    if(records.find(r => r.barcode === currentBarcode)){
        alert("条码已存在");
        return;
    }

    records.push({
        barcode: currentBarcode,
        image: currentImage,
        time: new Date().toLocaleString()
    });

    localStorage.setItem("tire", JSON.stringify(records));

    currentBarcode = "";
    currentImage = "";

    document.getElementById("barcode").innerText = "未扫描";
    document.getElementById("preview").src = "";

    load();
}

// ===== 加载 =====
function load(){
    document.getElementById("count").innerText = records.length;

    let html = "";

    records.forEach((r,i)=>{
        html += `
        <div class="card">
            <b>${r.barcode}</b><br>
            <span class="small">${r.time}</span>
            < img src="${r.image}">
        </div>`;
    });

    document.getElementById("history").innerHTML = html;
}

load();

// ===== Excel =====
function exportExcel(){

    let data = records.map(r => ({
        条码:r.barcode,
        时间:r.time
    }));

    const ws = XLSX.utils.json_to_sheet(data);
    const wb = XLSX.utils.book_new();
    XLSX.utils.book_append_sheet(wb, ws, "数据");

    XLSX.writeFile(wb, "轮胎数据.xlsx");
}

// ===== ZIP =====
function exportZip(){

    const zip = new JSZip();

    records.forEach(r=>{
        zip.file(r.barcode + ".jpg", r.image.split(",")[1], {base64:true});
    });

    zip.generateAsync({type:"blob"}).then(content=>{
        saveAs(content, "轮胎照片.zip");
    });
}

// ===== 清空 =====
function clearAll(){
    if(confirm("确定清空？")){
        localStorage.removeItem("tire");
        records = [];
        load();
    }
}

</script>

</body>
</html>