

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bon SecureX Web</title>
<style>
body { font-family: Arial; background: #f3f3f3; margin:0; padding:20px; }
.container { max-width:700px; margin:auto; background:white; padding:20px; border-radius:15px; }
h1 { text-align:center; color:#c62828; }
.status { text-align:center; font-size:22px; font-weight:bold; margin-top:15px; }
.safe { color:green; }
.unsafe { color:red; }
.flash { animation: flash 0.5s infinite alternate; }
@keyframes flash { from {background:#ffebee;} to {background:#ffcdd2;} }
button { width:100%; padding:12px; font-size:16px; margin-top:10px; }
video { width:100%; margin-top:10px; display:none; border-radius:10px; }
a.downloadLink { display:block; text-align:center; margin-top:10px; font-weight:bold; color:#c62828; }
</style>
</head>
<body>
<div class="container" id="page">
<h1>🚨 SheGuardian Web</h1>

<div class="status" id="statusText">Tap the button or double-tap screen in emergency</div>
<div id="aiInfo" class="status"></div>
<div id="locationInfo" class="status"></div>

<video id="videoPreview" autoplay muted></video>
<a id="downloadLink" class="downloadLink" style="display:none;">⬇ Download Emergency Video</a>

<p id="shareText"></p>
<button id="emergencyBtn">🚨 Activate Emergency</button>
<button id="shareBtn" style="display:none;" onclick="shareEmergency()">📤 Share Video & Location</button>
</div>

<script>
let chunks = [];
let recorder;

// Ultrasonic Alarm
function playUltrasonicAlarm(duration = 10000) {
  try {
    const context = new (window.AudioContext || window.webkitAudioContext)();
    const osc1 = context.createOscillator();
    const osc2 = context.createOscillator();
    const gainNode = context.createGain();

    osc1.frequency.value = 17000;
    osc2.frequency.value = 18000;
    osc1.type = 'sine';
    osc2.type = 'sine';

    osc1.connect(gainNode);
    osc2.connect(gainNode);
    gainNode.connect(context.destination);
    gainNode.gain.setValueAtTime(1, context.currentTime);

    osc1.start(); osc2.start();
    setTimeout(()=>{ osc1.stop(); osc2.stop(); }, duration);
  } catch(e) { console.log("Ultrasonic alarm not supported:", e); }
}

// Voice Guidance
function speak(text){
  const tts = new SpeechSynthesisUtterance(text);
  window.speechSynthesis.speak(tts);
}

// Activate Emergency
function activateEmergency() {
  document.getElementById("page").classList.add("flash");
  document.getElementById("statusText").innerText = "🚨 EMERGENCY MODE ACTIVE";
  playUltrasonicAlarm(15000);
  speak("Emergency activated. Recording video and tracking location.");
  getLocation();
  startRecording();
}

// GPS + safety
function getLocation() {
  if(!navigator.geolocation){ alert("GPS not supported"); return; }
  navigator.geolocation.getCurrentPosition(pos=>{
    const lat = pos.coords.latitude;
    const lon = pos.coords.longitude;
    const hour = new Date().getHours();
    let unsafe = (hour>=19 || hour<=5);

    const status = document.getElementById("statusText");
    status.innerText = unsafe ? "🔴 UNSAFE / ISOLATED STREET" : "🟢 STREET APPEARS SAFE";
    status.className = unsafe ? "status unsafe" : "status safe";

    document.getElementById("aiInfo").innerHTML = "🤖 Suggestion: "+ (unsafe ? "Move to crowded area or police station." : "Area seems active. Stay alert.");
    
    const msg = `🚨 EMERGENCY ALERT\nMy location: https://maps.google.com?q=${lat},${lon}\n🎥 Emergency video recorded`;
    document.getElementById("shareText").innerText = msg;
    document.getElementById("shareBtn").style.display = "block";

    document.getElementById("locationInfo").innerHTML = `Latitude: ${lat}<br>Longitude: ${lon}`;
  });
}

// Video recording - must be called on user gesture
function startRecording() {
  navigator.mediaDevices.getUserMedia({video:true,audio:true})
  .then(stream=>{
    const video = document.getElementById("videoPreview");
    video.srcObject = stream;
    video.style.display = "block";

    recorder = new MediaRecorder(stream);
    recorder.ondataavailable = e => chunks.push(e.data);
    recorder.onstop = () => {
      const blob = new Blob(chunks, {type:"video/webm"});
      const url = URL.createObjectURL(blob);
      const link = document.getElementById("downloadLink");
      link.href = url;
      link.download = "EmergencyVideo.webm";
      link.style.display = "block";
      link.click();
      speak("Video recorded and saved to device.");
    };
    recorder.start();
    setTimeout(()=>{
      recorder.stop();
      stream.getTracks().forEach(track => track.stop());
    },15000);
  }).catch(err=>alert("Camera/microphone access denied: "+err));
}

// Share emergency
function shareEmergency(){
  const msg = encodeURIComponent(document.getElementById("shareText").innerText);
  const contacts = ["+911234567890","+919876543210"];
  contacts.forEach(number=>{
    const url = `https://api.whatsapp.com/send?phone=${number}&text=${msg}`;
    window.open(url,"_blank");
  });
}

// Button & double-tap triggers
document.getElementById("emergencyBtn").addEventListener("click", activateEmergency);
document.body.addEventListener("dblclick", activateEmergency);
</script>
</body>
</html>
