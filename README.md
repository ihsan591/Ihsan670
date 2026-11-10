# Ihsan670
IHSAN AI - Your Personal Artificial Intelligence Assistant

<!DOCTYPE html>
<html lang="ps" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#080b12">
<title>IHSAN AI - Your Personal AI</title>

<style>
*{box-sizing:border-box;margin:0;padding:0}
body{
  font-family:Arial,sans-serif;
  background:#080b12;color:#f5f5f5;
  min-height:100vh;
}
header{
  display:flex;justify-content:space-between;
  align-items:center;padding:18px 6%;
  border-bottom:1px solid #242936;
  background:#0d111b;position:sticky;top:0;z-index:5;
}
.logo{font-size:25px;font-weight:bold;color:#e9bd58}
.logo span{color:white}
select,button,textarea{font:inherit}
select{
  background:#171e2b;color:white;
  border:1px solid #3a4353;padding:10px;
  border-radius:10px;
}
.hero{text-align:center;padding:65px 18px 35px}
.hero h1{font-size:clamp(32px,7vw,54px);margin-bottom:15px}
.gold{color:#e9bd58}
.hero p{color:#aeb6c5;line-height:1.9}
.panel{
  max-width:760px;margin:20px auto;
  padding:20px;background:#111722;
  border:1px solid #30394a;border-radius:20px;
}
.chat{
  height:310px;overflow-y:auto;padding:10px;
  display:flex;flex-direction:column;gap:12px;
}
.msg{
  padding:12px 15px;border-radius:14px;
  max-width:88%;line-height:1.8;white-space:pre-wrap;
}
.bot{background:#202a39;align-self:flex-start}
.user{background:#a77b25;color:#fff;align-self:flex-end}
.input-area{display:flex;gap:8px;margin-top:15px}
textarea{
  flex:1;resize:vertical;min-width:0;
  min-height:48px;max-height:130px;
  background:#080d16;color:white;
  border:1px solid #3a4353;border-radius:12px;
  padding:13px;outline:none;
}
button{
  border:0;border-radius:11px;
  padding:12px 17px;cursor:pointer;
  background:#d5a83e;color:#101010;
  font-weight:bold;
}
button:active{opacity:.8}
.upload{
  display:block;text-align:center;
  padding:18px;border:1px dashed #a77b25;
  border-radius:14px;margin-top:15px;
  color:#e9bd58;cursor:pointer;
}
.upload input{display:none}
#preview{
  max-width:100%;max-height:240px;
  display:none;margin:15px auto;border-radius:12px;
}
.features{
  max-width:900px;margin:35px auto;
  padding:0 15px;display:grid;
  grid-template-columns:repeat(auto-fit,minmax(200px,1fr));
  gap:15px;
}
.feature{
  background:#111722;border:1px solid #30394a;
  padding:22px;border-radius:15px;text-align:center;
}
.feature h3{color:#e9bd58;margin-bottom:10px}
.feature p{color:#aeb6c5;line-height:1.7}
footer{
  text-align:center;padding:30px;
  color:#8d96a5;border-top:1px solid #242936;
  margin-top:40px;
}
@media(max-width:500px){
  header{padding:14px 12px}
  .logo{font-size:20px}
  .panel{margin:15px 10px;padding:13px}
  .input-area{flex-wrap:wrap}
  .input-area button{flex:1}
}
</style>
</head>

<body>

<header>
  <div class="logo">IHSAN <span>AI</span></div>
  <select id="language" onchange="changeLanguage()">
    <option value="ps">پښتو</option>
    <option value="fa">دری</option>
    <option value="en">English</option>
  </select>
</header>

<section class="hero">
  <h1 id="heading">IHSAN <span class="gold">AI</span></h1>
  <p id="subtitle">
    ستا شخصي هوښیار مرستیال؛ پوښتنه وکړه او نوې نړۍ وپېژنه.
  </p>
</section>

<section class="panel">
  <h2 id="chatTitle" style="color:#e9bd58;margin-bottom:15px">
    له IHSAN AI سره خبرې وکړه
  </h2>

  <div class="chat" id="chat">
    <div class="msg bot" id="welcome">
      سلام! زه IHSAN AI یم. څنګه مرسته درسره وکړم؟
    </div>
  </div>

  <div class="input-area">
    <textarea id="question" placeholder="خپله پوښتنه دلته ولیکه..."></textarea>
    <button onclick="sendMessage()" id="send">لېږل</button>
  </div>

  <label class="upload">
    <span id="uploadText">📷 عکس انتخاب کړه</span>
    <input type="file" id="imageInput" accept="image/*">
  </label>

  <img id="preview" alt="Uploaded image preview">
</section>

<section class="features">
  <div class="feature">
    <h3 id="f1">🤖 هوښیار مرستیال</h3>
    <p id="d1">خپلې پوښتنې ولیکه او د AI له مرستې ګټه واخله.</p>
  </div>
  <div class="feature">
    <h3 id="f2">🌍 څو ژبې</h3>
    <p id="d2">پښتو، دري او انګلیسي ژبې.</p>
  </div>
  <div class="feature">
    <h3 id="f3">📷 د عکسونو برخه</h3>
    <p id="d3">خپل عکس انتخاب او مخکتنه یې وګوره.</p>
  </div>
</section>

<footer>
  <p>© 2026 IHSAN AI — All Rights Reserved</p>
  <p style="margin-top:8px">Created with ❤️ for the future</p>
</footer>

<script>
const translations = {
 ps:{
  dir:"rtl",heading:'IHSAN <span class="gold">AI</span>',
  subtitle:"ستا شخصي هوښیار مرستیال؛ پوښتنه وکړه او نوې نړۍ وپېژنه.",
  chatTitle:"له IHSAN AI سره خبرې وکړه",
  welcome:"سلام! زه IHSAN AI یم. څنګه مرسته درسره وکړم؟",
  placeholder:"خپله پوښتنه دلته ولیکه...",
  send:"لېږل",upload:"📷 عکس انتخاب کړه",
  f1:"🤖 هوښیار مرستیال",d1:"خپلې پوښتنې ولیکه او د AI له مرستې ګټه واخله.",
  f2:"🌍 څو ژبې",d2:"پښتو، دري او انګلیسي ژبې.",
  f3:"📷 د عکسونو برخه",d3:"خپل عکس انتخاب او مخکتنه یې وګوره.",
  empty:"مهرباني وکړه، لومړی خپله پوښتنه ولیکه.",
  demo:"ستا پیغام ترلاسه شو! دا د IHSAN AI لومړنۍ نسخه ده. د واقعي AI ځوابونو لپاره به خوندي AI سرور ورسره وصل کړو."
 },
 fa:{
  dir:"rtl",heading:'IHSAN <span class="gold">AI</span>',
  subtitle:"دستیار هوشمند شخصی شما؛ سوال بپرسید و دنیای جدید را کشف کنید.",
  chatTitle:"با IHSAN AI گفتگو کنید",
  welcome:"سلام! من IHSAN AI هستم. چطور کمک کنم؟",
  placeholder:"سوال خود را اینجا بنویسید...",
  send:"ارسال",upload:"📷 انتخاب عکس",
  f1:"🤖 دستیار هوشمند",d1:"سوال‌های خود را بنویسید.",
  f2:"🌍 چند زبانه",d2:"پشتو، دری و انگلیسی.",
  f3:"📷 بخش تصاویر",d3:"عکس خود را انتخاب و پیش‌نمایش کنید.",
  empty:"لطفاً سوال خود را بنویسید.",
  demo:"پیام شما دریافت شد! این نسخه اولیه IHSAN AI است. برای پاسخ‌های واقعی، سرور هوش مصنوعی را وصل می‌کنیم."
 },
 en:{
  dir:"ltr",heading:'IHSAN <span class="gold">AI</span>',
  subtitle:"Your personal intelligent assistant. Ask questions and explore.",
  chatTitle:"Chat with IHSAN AI",
  welcome:"Hello! I am IHSAN AI. How can I help you?",
  placeholder:"Type your question here...",
  send:"Send",upload:"📷 Choose an image",
  f1:"🤖 Smart Assistant",d1:"Write your questions and explore AI.",
  f2:"🌍 Multilingual",d2:"Pashto, Dari and English.",
  f3:"📷 Image Upload",d3:"Choose an image and preview it.",
  empty:"Please write a question first.",
  demo:"Message received! This is the first version of IHSAN AI. We will connect a secure AI server for real AI answers."
 }
};

function changeLanguage(){
 const lang=document.getElementById("language").value;
 const t=translations[lang];
 document.documentElement.lang=lang;
 document.documentElement.dir=t.dir;
 document.getElementById("heading").innerHTML=t.heading;
 document.getElementById("subtitle").textContent=t.subtitle;
 document.getElementById("chatTitle").textContent=t.chatTitle;
 document.getElementById("welcome").textContent=t.welcome;
 document.getElementById("question").placeholder=t.placeholder;
 document.getElementById("send").textContent=t.send;
 document.getElementById("uploadText").textContent=t.upload;
 ["f1","d1","f2","d2","f3","d3"].forEach(id=>{
  document.getElementById(id).textContent=t[id];
 });
}

function sendMessage(){
 const input=document.getElementById("question");
 const value=input.value.trim();
 const lang=document.getElementById("language").value;
 if(!value){
  alert(translations[lang].empty);
  return;
 }
 const chat=document.getElementById("chat");

 const user=document.createElement("div");
 user.className="msg user";
 user.textContent=value;
 chat.appendChild(user);

 const bot=document.createElement("div");
 bot.className="msg bot";
 bot.textContent=translations[lang].demo;
 chat.appendChild(bot);

 input.value="";
 chat.scrollTop=chat.scrollHeight;
}

document.getElementById("question").addEventListener("keydown",function(e){
 if(e.key==="Enter" && !e.shiftKey){
  e.preventDefault();
  sendMessage();
 }
});

document.getElementById("imageInput").addEventListener("change",function(){
 const file=this.files[0];
 if(!file)return;
 if(!file.type.startsWith("image/")){
  alert("Please choose an image file.");
  return;
 }
 const url=URL.createObjectURL(file);
 const preview=document.getElementById("preview");
 preview.src=url;
 preview.style.display="block";
});
</script>

</body>
</html>
