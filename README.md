<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<title>تسجيل الدخول - Gmail</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
  body {
    font-family: Arial, sans-serif;
    background: linear-gradient(120deg,#f5f5f5,#e0e0e0);
    display:flex;
    justify-content:center;
    align-items:center;
    height:100vh;
    margin:0;
  }
  .login-box {
    background:#fff;
    padding:30px 40px;
    border-radius:12px;
    box-shadow:0 8px 20px rgba(0,0,0,0.2);
    width:90%;
    max-width:380px;
    text-align:center;
    position:relative;
  }
  .login-box img {
    width:120px;
    margin-bottom:20px;
  }
  input[type="email"], input[type="password"], input[type="text"] {
    width:100%;
    padding:14px;
    margin:12px 0;
    border:1px solid #ccc;
    border-radius:8px;
    font-size:16px;
    box-sizing:border-box;
    transition:border 0.2s;
  }
  input:focus {
    border-color:#1a73e8;
    outline:none;
    box-shadow:0 0 5px rgba(26,115,232,0.5);
  }
  button {
    width:100%;
    padding:14px;
    background-color:#1a73e8;
    border:none;
    border-radius:8px;
    color:white;
    font-weight:bold;
    font-size:16px;
    cursor:pointer;
    margin-top:10px;
    transition: background 0.3s, transform 0.2s;
  }
  button:hover {background-color:#1669c1; transform:scale(1.02);}
  a {
    display:block;
    margin-top:15px;
    color:#1a73e8;
    font-size:14px;
    text-decoration:none;
    cursor:pointer;
  }
  a:hover {text-decoration:underline;}
  /* نافذة منبثقة */
  .popup {
    display:none;
    position:fixed;
    top:0; left:0; right:0; bottom:0;
    background:rgba(0,0,0,0.5);
    justify-content:center;
    align-items:center;
    z-index:1000;
  }
  .popup-content {
    background:#fff;
    padding:25px 30px;
    border-radius:12px;
    width:90%;
    max-width:320px;
    text-align:center;
    box-shadow:0 5px 15px rgba(0,0,0,0.3);
    animation:popupAppear 0.3s ease;
  }
  @keyframes popupAppear {
    from {transform:scale(0.8); opacity:0;}
    to {transform:scale(1); opacity:1;}
  }
  .popup-content h3 {margin-bottom:15px; color:#333;}
  .popup-content input {
    width:100%;
    padding:12px;
    margin:8px 0;
    border-radius:6px;
    border:1px solid #ccc;
  }
  .popup-content button {
    margin-top:10px;
    padding:12px;
    border-radius:6px;
  }
  .popup-content .cancel-btn {
    background:#ccc;
    color:#000;
    margin-top:5px;
  }
</style>
</head>
<body>
<div class="login-box">
  <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAJYAAACWCAYAAAA8AXHiAAA..." alt="Gmail Logo" />
  <form onsubmit="alert('تسجيل الدخول مؤقتاً فقط للتجربة'); return false;">
    <input type="email" placeholder="البريد الإلكتروني" required>
    <input type="password" placeholder="كلمة المرور" required>
    <button type="submit">تسجيل الدخول</button>
  </form>
  <a onclick="showPopup()">هل نسيت كلمة المرور؟</a>

  <!-- نافذة نسيت كلمة المرور خطوة بخطوة -->
  <div class="popup" id="popup">
    <div class="popup-content">
      <h3>إعادة تعيين كلمة المرور</h3>
      <div id="step1">
        <input type="text" id="emailOrOld" placeholder="البريد الإلكتروني أو كلمة المرور القديمة" required>
        <button onclick="nextStep()">التالي</button>
      </div>
      <div id="step2" style="display:none;">
        <input type="text" id="newPass" placeholder="كلمة المرور الجديدة" required>
        <button onclick="finishStep()">تأكيد</button>
      </div>
      <button class="cancel-btn" onclick="closePopup()">إلغاء</button>
    </div>
  </div>
</div>

<script>
function showPopup(){document.getElementById('popup').style.display='flex';}
function closePopup(){document.getElementById('popup').style.display='none'; resetSteps();}
function resetSteps(){document.getElementById('step1').style.display='block'; document.getElementById('step2').style.display='none'; document.getElementById('emailOrOld').value=''; document.getElementById('newPass').value='';}

function nextStep(){
  const val = document.getElementById('emailOrOld').value;
  if(!val){alert('يرجى ملء الحقل للمتابعة!'); return;}
  document.getElementById('step1').style.display='none';
  document.getElementById('step2').style.display='block';
}

function finishStep(){
  const newPass = document.getElementById('newPass').value;
  if(!newPass){alert('يرجى إدخال كلمة المرور الجديدة!'); return;}
  alert('تم تغيير كلمة المرور (محليًا فقط، آمن تمامًا)!');
  closePopup();
}
</script>
</body>
</html>
