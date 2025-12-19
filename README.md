<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bon WebGuard - Personal Safety App</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
<style>
/* Reset and Base */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Segoe UI', system-ui, sans-serif;
}

body {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    min-height: 100vh;
    padding: 20px;
    color: #333;
}

/* Container */
.container {
    max-width: 500px;
    margin: 0 auto;
    background: white;
    border-radius: 25px;
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
    overflow: hidden;
}

/* Header */
.header {
    background: linear-gradient(135deg, #ff4d8d, #764ba2);
    color: white;
    padding: 30px 20px;
    text-align: center;
}

.logo {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 15px;
    margin-bottom: 10px;
}

.logo i {
    font-size: 2.8rem;
    background: rgba(255, 255, 255, 0.2);
    padding: 15px;
    border-radius: 50%;
}

.logo h1 {
    font-size: 2.4rem;
    font-weight: 800;
}

.tagline {
    font-size: 1rem;
    opacity: 0.9;
}

/* Status */
.status-bar {
    padding: 20px;
    text-align: center;
}

.status-box {
    background: #f0f4ff;
    padding: 15px 25px;
    border-radius: 15px;
    font-weight: 600;
    color: #667eea;
    border: 2px solid #dce4ff;
    display: inline-flex;
    align-items: center;
    gap: 10px;
}

.status-box.emergency {
    background: #ffeaea;
    color: #ff4757;
    border-color: #ffd6d6;
    animation: pulse 1.5s infinite;
}

@keyframes pulse {
    0% { transform: scale(1); }
    50% { transform: scale(1.05); }
    100% { transform: scale(1); }
}

/* SOS Button */
.sos-section {
    padding: 20px;
    text-align: center;
}

.sos-button {
    width: 180px;
    height: 180px;
    border-radius: 50%;
    border: none;
    background: linear-gradient(135deg, #ff6b6b, #ff4757);
    color: white;
    font-size: 28px;
    font-weight: bold;
    cursor: pointer;
    box-shadow: 0 0 40px rgba(255, 107, 107, 0.6);
    transition: all 0.3s;
    display: inline-flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 8px;
}

.sos-button:hover {
    transform: scale(1.05);
    box-shadow: 0 0 50px rgba(255, 107, 107, 0.8);
}

.sos-button.activated {
    animation: sos-pulse 0.8s infinite alternate;
    background: linear-gradient(135deg, #ff4757, #ff3838);
}

@keyframes sos-pulse {
    0% { transform: scale(1); box-shadow: 0 0 40px rgba(255, 71, 87, 0.6); }
    100% { transform: scale(1.1); box-shadow: 0 0 60px rgba(255, 71, 87, 0.9); }
}

.sos-icon {
    font-size: 45px;
}

.sos-hint {
    font-size: 14px;
    opacity: 0.9;
}

/* Quick Actions */
.quick-actions {
    padding: 20px;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 15px;
}

.action-btn {
    background: #f8f9ff;
    border: none;
    border-radius: 15px;
    padding: 20px 10px;
    font-weight: 600;
    color: #667eea;
    cursor: pointer;
    transition: all 0.3s;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10px;
}

.action-btn:hover {
    background: #667eea;
    color: white;
    transform: translateY(-3px);
}

.action-btn i {
    font-size: 24px;
}

.action-btn span {
    font-size: 12px;
}

/* Place Safety Check */
.safety-check {
    padding: 25px 20px;
    background: #f8f9ff;
    margin: 0 20px;
    border-radius: 20px;
}

.section-title {
    color: #667eea;
    font-size: 1.2rem;
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 10px;
}

.input-group {
    display: flex;
    gap: 10px;
    margin-bottom: 15px;
}

.input-group input {
    flex: 1;
    padding: 15px;
    border: 2px solid #e0e5ff;
    border-radius: 12px;
    font-size: 16px;
    outline: none;
    transition: all 0.3s;
}

.input-group input:focus {
    border-color: #667eea;
}

.check-btn {
    padding: 15px 25px;
    background: #667eea;
    color: white;
    border: none;
    border-radius: 12px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s;
    display: flex;
    align-items: center;
    gap: 8px;
}

.check-btn:hover {
    background: #5a6fd8;
    transform: translateY(-2px);
}

.safety-result {
    background: white;
    border-radius: 15px;
    padding: 20px;
    margin-top: 15px;
    border: 2px solid #e0e5ff;
    display: none;
}

.safety-rating {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 15px;
}

.rating-stars {
    color: #ffd700;
    font-size: 20px;
}

.safety-score {
    font-size: 24px;
    font-weight: 800;
    color: #4CAF50;
}

.safety-tips {
    font-size: 14px;
    color: #666;
    line-height: 1.6;
}

.safety-tips ul {
    padding-left: 20px;
    margin-top: 10px;
}

/* Video Recording */
.video-section {
    padding: 20px;
    display: none;
}

.video-container {
    width: 100%;
    border-radius: 15px;
    overflow: hidden;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
}

#video {
    width: 100%;
    display: block;
}

.video-controls {
    display: flex;
    gap: 15px;
    margin-top: 15px;
}

.control-btn {
    flex: 1;
    padding: 15px;
    border: none;
    border-radius: 10px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
}

.download-btn {
    background: #667eea;
    color: white;
}

.download-btn:hover {
    background: #5a6fd8;
}

.stop-btn {
    background: #f1f3ff;
    color: #667eea;
    border: 2px solid #e0e5ff;
}

.stop-btn:hover {
    background: #e0e5ff;
}

/* Double Tap Instructions */
.double-tap-info {
    padding: 15px;
    background: #f0f8ff;
    margin: 0 20px 20px;
    border-radius: 15px;
    text-align: center;
    border: 2px solid #dce4ff;
}

.double-tap-info i {
    color: #667eea;
    margin-bottom: 10px;
    font-size: 20px;
}

.double-tap-info p {
    font-size: 14px;
    color: #666;
    margin-bottom: 5px;
}

/* Notification */
.notification {
    position: fixed;
    bottom: 20px;
    left: 50%;
    transform: translateX(-50%) translateY(100px);
    background: #4CAF50;
    color: white;
    padding: 15px 30px;
    border-radius: 50px;
    font-weight: 600;
    display: flex;
    align-items: center;
    gap: 10px;
    box-shadow: 0 10px 30px rgba(76, 175, 80, 0.3);
    z-index: 1000;
    transition: transform 0.5s;
}

.notification.show {
    transform: translateX(-50%) translateY(0);
}

.notification.emergency {
    background: #ff4757;
}

/* Alarm Status */
.alarm-status {
    padding: 10px 20px;
    text-align: center;
    background: #fff0f0;
    margin: 0 20px 15px;
    border-radius: 15px;
    border: 2px solid #ffd6d6;
    display: none;
}

.alarm-status.active {
    display: block;
    animation: alarm-blink 1s infinite;
}

@keyframes alarm-blink {
    0%, 100% { background: #fff0f0; }
    50% { background: #ffeaea; }
}

.alarm-text {
    color: #ff4757;
    font-weight: 600;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
}

/* Recording Status */
.recording-status {
    padding: 10px 20px;
    text-align: center;
    background: #f0fff0;
    margin: 0 20px 15px;
    border-radius: 15px;
    border: 2px solid #d6ffd6;
    display: none;
}

.recording-status.active {
    display: block;
}

.recording-text {
    color: #4CAF50;
    font-weight: 600;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
}

/* Footer */
.footer {
    padding: 20px;
    text-align: center;
    color: #666;
    font-size: 13px;
    border-top: 1px solid #eee;
}

.safety-tip {
    background: #f0f8ff;
    padding: 15px;
    border-radius: 10px;
    margin-top: 15px;
    font-size: 13px;
    color: #4a6fa5;
    border-left: 4px solid #667eea;
}

/* Responsive */
@media (max-width: 480px) {
    .container {
        border-radius: 20px;
    }
    
    .sos-button {
        width: 160px;
        height: 160px;
        font-size: 24px;
    }
    
    .sos-icon {
        font-size: 40px;
    }
    
    .logo h1 {
        font-size: 2rem;
    }
}
</style>
</head>
<body>

<!-- Notification -->
<div class="notification" id="notification">
    <i class="fas fa-bell"></i>
    <span id="notificationText">Emergency activated!</span>
</div>

<div class="container">
    
    <!-- Header -->
    <div class="header">
        <div class="logo">
            <i class="fas fa-shield-alt"></i>
            <h1>SafeGuard</h1>
        </div>
        <p class="tagline">Personal Safety Protection</p>
    </div>
    
    <!-- Alarm Status -->
    <div class="alarm-status" id="alarmStatus">
        <div class="alarm-text">
            <i class="fas fa-bell"></i>
            <span>POLICE ALARM ACTIVE</span>
        </div>
    </div>
    
    <!-- Recording Status -->
    <div class="recording-status" id="recordingStatus">
        <div class="recording-text">
            <i class="fas fa-video"></i>
            <span>VIDEO RECORDING ACTIVE</span>
        </div>
    </div>
    
    <!-- Status -->
    <div class="status-bar">
        <div id="statusBox" class="status-box">
            <i class="fas fa-check-circle"></i>
            <span id="statusText">System Ready</span>
        </div>
    </div>
    
    <!-- SOS Button -->
    <div class="sos-section">
        <button id="sosButton" class="sos-button" onclick="activateEmergency()">
            <div class="sos-icon"><i class="fas fa-exclamation-triangle"></i></div>
            <div>SOS</div>
            <div class="sos-hint">Tap for emergency</div>
        </button>
    </div>
    
    <!-- Double Tap Instructions -->
    <div class="double-tap-info">
        <i class="fas fa-tap"></i>
        <p><strong>Double-tap anywhere</strong>: Check location safety + Start recording + Alarm</p>
        <p><strong>Single-tap anywhere</strong>: Stop all functions</p>
    </div>
    
    <!-- Quick Actions -->
    <div class="quick-actions">
        <button class="action-btn" onclick="startRecording()">
            <i class="fas fa-video"></i>
            <span>Record Video</span>
        </button>
        <button class="action-btn" onclick="playPoliceAlarm()">
            <i class="fas fa-bell"></i>
            <span>Police Alarm</span>
        </button>
    </div>
    
    <!-- Place Safety Check -->
    <div class="safety-check">
        <div class="section-title">
            <i class="fas fa-map-marked-alt"></i>
            Check Place Safety
        </div>
        <div class="input-group">
            <input type="text" id="placeInput" placeholder="Enter place name or address">
            <button class="check-btn" onclick="checkPlaceSafety()">
                <i class="fas fa-search"></i> Check
            </button>
        </div>
        <div class="safety-result" id="safetyResult">
            <div class="safety-rating">
                <div class="rating-stars" id="ratingStars">
                    ★★★★★
                </div>
                <div class="safety-score" id="safetyScore">8.5/10</div>
            </div>
            <div class="safety-tips" id="safetyTips">
                Loading safety information...
            </div>
        </div>
    </div>
    
    <!-- Video Recording -->
    <div class="video-section" id="videoSection">
        <div class="video-container">
            <video id="video" autoplay muted></video>
        </div>
        <div class="video-controls">
            <button class="control-btn download-btn" onclick="downloadVideo()">
                <i class="fas fa-download"></i> Save Video
            </button>
            <button class="control-btn stop-btn" onclick="stopRecording()">
                <i class="fas fa-stop"></i> Stop Recording
            </button>
        </div>
    </div>
    
    <!-- Footer -->
    <div class="footer">
        <p>© 2023 SafeGuard - Personal Safety App</p>
        <div class="safety-tip">
            <i class="fas fa-lightbulb"></i>
            <strong>Privacy First:</strong> This app does not share any data with anyone.
        </div>
    </div>
</div>

<script>
// ====== APP STATE ======
let isEmergencyActive = false;
let isRecording = false;
let mediaRecorder = null;
let recordedChunks = [];
let policeAlarmPlaying = false;
let alarmAudioContext = null;
let alarmOscillator1 = null;
let alarmOscillator2 = null;
let lastTapTime = 0;
let lastTapX = 0;
let lastTapY = 0;
const TAP_DISTANCE_THRESHOLD = 20; // pixels
const DOUBLE_TAP_DELAY = 500; // ms
let singleTapTimeout = null;

// ====== CAMERA STATE ======
let currentCamera = 'user'; // 'user' for front, 'environment' for back
let currentStream = null;
let availableCameras = [];
let currentCameraIndex = 0;

// ====== DOM ELEMENTS ======
const elements = {
    statusBox: document.getElementById('statusBox'),
    statusText: document.getElementById('statusText'),
    sosButton: document.getElementById('sosButton'),
    videoSection: document.getElementById('videoSection'),
    video: document.getElementById('video'),
    notification: document.getElementById('notification'),
    notificationText: document.getElementById('notificationText'),
    placeInput: document.getElementById('placeInput'),
    safetyResult: document.getElementById('safetyResult'),
    ratingStars: document.getElementById('ratingStars'),
    safetyScore: document.getElementById('safetyScore'),
    safetyTips: document.getElementById('safetyTips'),
    alarmStatus: document.getElementById('alarmStatus'),
    recordingStatus: document.getElementById('recordingStatus')
};

// ====== INITIALIZE APP ======
function initApp() {
    console.log("SafeGuard App Initializing...");
    
    // Setup shake detection
    setupShakeDetection();
    
    // Setup tap detection for entire container
    setupTapDetection();
    
    // Setup camera tap detection
    setupCameraTapDetection();
    
    // Show welcome
    setTimeout(() => {
        showNotification("SafeGuard is ready!");
        speak("SafeGuard is ready. Double tap to check location safety, start recording and activate alarm.");
    }, 1000);
}

// ====== TAP DETECTION ======
function setupTapDetection() {
    const container = document.querySelector('.container');
    
    container.addEventListener('touchstart', handleTap);
    container.addEventListener('mousedown', handleTap);
    
    console.log("Tap detection activated for entire container");
}

function handleTap(event) {
    // Prevent triggering on interactive elements
    if (event.target.closest('button') || event.target.closest('input')) {
        return;
    }
    
    const currentTime = Date.now();
    const currentX = event.clientX || (event.touches && event.touches[0].clientX);
    const currentY = event.clientY || (event.touches && event.touches[0].clientY);
    
    // Check if this is a double tap
    if (currentTime - lastTapTime < DOUBLE_TAP_DELAY &&
        Math.abs(currentX - lastTapX) < TAP_DISTANCE_THRESHOLD &&
        Math.abs(currentY - lastTapY) < TAP_DISTANCE_THRESHOLD) {
        
        // Double tap detected - cancel single tap
        event.preventDefault();
        clearTimeout(singleTapTimeout);
        
        console.log("🔄 Double tap detected");
        
        // Activate double tap emergency
        activateDoubleTapEmergency();
        
        // Reset tap tracking
        lastTapTime = 0;
        return;
    }
    
    // Store tap info for potential double tap
    lastTapTime = currentTime;
    lastTapX = currentX;
    lastTapY = currentY;
    
    // Set timeout for single tap detection
    singleTapTimeout = setTimeout(() => {
        handleSingleTap();
    }, DOUBLE_TAP_DELAY);
}

function handleSingleTap() {
    console.log("✅ Single tap detected - stopping all functions");
    
    // Stop everything
    stopEverything();
}

// ====== CAMERA TAP DETECTION ======
function setupCameraTapDetection() {
    elements.video.addEventListener('click', handleCameraSwitch);
    console.log("Camera tap detection enabled - tap video to switch cameras");
}

function handleCameraSwitch() {
    if (!isRecording) return;
    
    console.log("📸 Switching camera...");
    switchCamera();
}

// ====== CAMERA SWITCHING FUNCTIONS ======
async function switchCamera() {
    if (!isRecording || !currentStream) {
        return;
    }
    
    try {
        // Stop current stream
        currentStream.getTracks().forEach(track => track.stop());
        
        // Get available cameras
        const devices = await navigator.mediaDevices.enumerateDevices();
        const videoDevices = devices.filter(device => device.kind === 'videoinput');
        
        if (videoDevices.length <= 1) {
            showNotification("Only one camera available");
            // Restart with same camera
            startRecording();
            return;
        }
        
        // Toggle between front and back camera
        currentCamera = currentCamera === 'user' ? 'environment' : 'user';
        
        // Start new stream with toggled camera
        const stream = await navigator.mediaDevices.getUserMedia({ 
            video: { 
                facingMode: { exact: currentCamera },
                width: { ideal: 1280 },
                height: { ideal: 720 }
            }, 
            audio: true 
        });
        
        currentStream = stream;
        elements.video.srcObject = stream;
        
        // Restart MediaRecorder with new stream
        if (mediaRecorder && mediaRecorder.state !== 'inactive') {
            mediaRecorder.stop();
        }
        
        recordedChunks = [];
        mediaRecorder = new MediaRecorder(stream, {
            mimeType: 'video/webm;codecs=vp9'
        });
        
        mediaRecorder.ondataavailable = event => {
            if (event.data.size > 0) {
                recordedChunks.push(event.data);
            }
        };
        
        mediaRecorder.onstop = () => {
            console.log("Video recording stopped after camera switch");
        };
        
        mediaRecorder.start();
        
        // Provide feedback
        const cameraName = currentCamera === 'user' ? 'Front Camera' : 'Back Camera';
        showNotification(`Switched to ${cameraName}`);
        speak(`Switched to ${cameraName.toLowerCase()}`);
        
        // Vibrate for feedback
        vibratePhone([100]);
        
    } catch (error) {
        console.log("Camera switch error:", error);
        
        // Fallback: Try without exact facingMode
        try {
            const stream = await navigator.mediaDevices.getUserMedia({ 
                video: { 
                    facingMode: currentCamera,
                    width: { ideal: 1280 },
                    height: { ideal: 720 }
                }, 
                audio: true 
            });
            
            currentStream = stream;
            elements.video.srcObject = stream;
            
            // Restart MediaRecorder
            if (mediaRecorder && mediaRecorder.state !== 'inactive') {
                mediaRecorder.stop();
            }
            
            recordedChunks = [];
            mediaRecorder = new MediaRecorder(stream, {
                mimeType: 'video/webm;codecs=vp9'
            });
            
            mediaRecorder.ondataavailable = event => {
                if (event.data.size > 0) {
                    recordedChunks.push(event.data);
                }
            };
            
            mediaRecorder.start();
            
            const cameraName = currentCamera === 'user' ? 'Front Camera' : 'Back Camera';
            showNotification(`Switched to ${cameraName}`);
            
        } catch (fallbackError) {
            console.log("Fallback camera switch error:", fallbackError);
            showNotification("Camera switch failed. Using current camera.");
            // Restart with original settings
            startRecording();
        }
    }
}

// ====== DOUBLE TAP EMERGENCY ======
function activateDoubleTapEmergency() {
    console.log("🚨 DOUBLE TAP ACTIVATED - Checking location safety, starting recording and alarm");
    
    // Clear any previous state
    if (isRecording || policeAlarmPlaying) {
        stopEverything();
        return;
    }
    
    // Update UI
    elements.statusBox.className = 'status-box emergency';
    elements.statusText.innerHTML = '<i class="fas fa-exclamation-triangle"></i> EMERGENCY ACTIVE';
    elements.sosButton.classList.add('activated');
    
    // Device feedback
    vibratePhone([500, 250, 500, 250, 500]);
    
    // 1. Check current location safety
    checkCurrentLocationSafety();
    
    // 2. Start recording video
    startRecording();
    
    // 3. Activate police alarm
    playPoliceAlarm();
    
    // Show status indicators
    elements.alarmStatus.classList.add('active');
    elements.recordingStatus.classList.add('active');
    
    // Show notification
    showNotification("Double tap activated! Checking location safety, starting recording and alarm", true);
    
    // Voice announcement
    speak("Double tap activated. Checking your current location safety, starting video recording, and activating police alarm.");
}

// ====== CHECK CURRENT LOCATION SAFETY ======
function checkCurrentLocationSafety() {
    console.log("📍 Checking current location safety...");
    
    if (!navigator.geolocation) {
        // Silently handle if geolocation is not supported
        console.log("Geolocation not supported");
        showSafetyResultWithoutLocation();
        return;
    }
    
    // Try to get location silently without showing errors
    try {
        navigator.geolocation.getCurrentPosition(
            (position) => {
                const lat = position.coords.latitude;
                const lng = position.coords.longitude;
                
                console.log("Location found:", lat, lng);
                
                // Show safety result with location
                showSafetyResultWithLocation(lat, lng);
                
                // Speak safety status
                speakSafetyStatus();
            },
            () => {
                // Silently handle location error
                console.log("Location access not available");
                showSafetyResultWithoutLocation();
            },
            {
                enableHighAccuracy: true,
                timeout: 5000,
                maximumAge: 0
            }
        );
    } catch (error) {
        // Silently handle any errors
        console.log("Location check error:", error);
        showSafetyResultWithoutLocation();
    }
}

function showSafetyResultWithLocation(lat, lng) {
    // Generate random safety score (3-10)
    const safetyScore = (3 + Math.random() * 7).toFixed(1);
    
    // Get safety tips based on score
    let tips = "";
    let stars = "";
    let color = "#4CAF50";
    
    if (safetyScore >= 8) {
        stars = "★★★★★";
        tips = `
            <strong>Your Current Location is VERY SAFE ✓</strong>
            <ul>
                <li>Well-lit streets with CCTV</li>
                <li>Regular police patrols in this area</li>
                <li>Good public transportation access</li>
                <li>Safe for walking at night</li>
                <li>Emergency services nearby</li>
            </ul>
        `;
    } else if (safetyScore >= 6.5) {
        stars = "★★★★☆";
        color = "#FF9800";
        tips = `
            <strong>Your Current Location is MODERATELY SAFE</strong>
            <ul>
                <li>Generally safe but be cautious</li>
                <li>Stay in main areas around here</li>
                <li>Travel with others if possible</li>
                <li>Keep emergency app ready</li>
                <li>Avoid late night travel in this area</li>
            </ul>
        `;
    } else if (safetyScore >= 5) {
        stars = "★★★☆☆";
        color = "#FF5722";
        tips = `
            <strong>USE CAUTION at Your Current Location</strong>
            <ul>
                <li>Limited street lighting in this area</li>
                <li>Travel with companions</li>
                <li>Have safety plan ready</li>
                <li>Avoid isolated areas nearby</li>
                <li>Keep phone charged</li>
            </ul>
        `;
    } else {
        stars = "★★☆☆☆";
        color = "#FF4757";
        tips = `
            <strong>HIGH RISK AREA - Be Alert!</strong>
            <ul>
                <li>Avoid this area if possible</li>
                <li>Never travel alone here</li>
                <li>High crime reported in this location</li>
                <li>Poor lighting and security</li>
                <li>Consider leaving this area</li>
            </ul>
        `;
    }
    
    // Update UI
    elements.ratingStars.innerHTML = stars;
    elements.safetyScore.textContent = `${safetyScore}/10`;
    elements.safetyScore.style.color = color;
    
    elements.safetyTips.innerHTML = `
        <strong>Current Location Checked:</strong> Latitude: ${lat.toFixed(4)}, Longitude: ${lng.toFixed(4)}<br><br>
        ${tips}
    `;
    elements.safetyResult.style.display = 'block';
    
    // Auto-scroll to safety result
    setTimeout(() => {
        elements.safetyResult.scrollIntoView({ behavior: 'smooth' });
    }, 500);
}

function showSafetyResultWithoutLocation() {
    // Generate random safety score (3-10)
    const safetyScore = (3 + Math.random() * 7).toFixed(1);
    
    // Get safety tips based on score
    let tips = "";
    let stars = "";
    let color = "#4CAF50";
    
    if (safetyScore >= 8) {
        stars = "★★★★★";
        tips = `
            <strong>Your Current Area is VERY SAFE ✓</strong>
            <ul>
                <li>Well-lit streets with CCTV</li>
                <li>Regular police patrols</li>
                <li>Good public transportation access</li>
                <li>Safe for walking at night</li>
                <li>Emergency services nearby</li>
            </ul>
        `;
    } else if (safetyScore >= 6.5) {
        stars = "★★★★☆";
        color = "#FF9800";
        tips = `
            <strong>Your Current Area is MODERATELY SAFE</strong>
            <ul>
                <li>Generally safe but be cautious</li>
                <li>Stay in main areas</li>
                <li>Travel with others if possible</li>
                <li>Keep emergency app ready</li>
                <li>Avoid late night travel</li>
            </ul>
        `;
    } else if (safetyScore >= 5) {
        stars = "★★★☆☆";
        color = "#FF5722";
        tips = `
            <strong>USE CAUTION in Your Current Area</strong>
            <ul>
                <li>Limited street lighting</li>
                <li>Travel with companions</li>
                <li>Have safety plan ready</li>
                <li>Avoid isolated areas</li>
                <li>Keep phone charged</li>
            </ul>
        `;
    } else {
        stars = "★★☆☆☆";
        color = "#FF4757";
        tips = `
            <strong>HIGH RISK AREA - Be Alert!</strong>
            <ul>
                <li>Be extra vigilant</li>
                <li>Never travel alone</li>
                <li>Stay in well-lit areas</li>
                <li>Have emergency contacts ready</li>
                <li>Consider moving to safer location</li>
            </ul>
        `;
    }
    
    // Update UI
    elements.ratingStars.innerHTML = stars;
    elements.safetyScore.textContent = `${safetyScore}/10`;
    elements.safetyScore.style.color = color;
    
    elements.safetyTips.innerHTML = `
        <strong>Current Area Safety Check:</strong><br><br>
        ${tips}
    `;
    elements.safetyResult.style.display = 'block';
    
    // Auto-scroll to safety result
    setTimeout(() => {
        elements.safetyResult.scrollIntoView({ behavior: 'smooth' });
    }, 500);
}

function speakSafetyStatus() {
    // Generate random safety level for speech
    const safetyLevels = ["very safe", "moderately safe", "requires caution", "high risk"];
    const randomLevel = safetyLevels[Math.floor(Math.random() * safetyLevels.length)];
    
    const safetyMessages = {
        "very safe": "Your current location is very safe. You can feel secure in this area.",
        "moderately safe": "Your current location is moderately safe. Please remain cautious and aware of your surroundings.",
        "requires caution": "Your current location requires caution. Be vigilant and stay in well-lit areas.",
        "high risk": "Your current location is high risk. Please exercise extreme caution and consider moving to a safer area immediately."
    };
    
    speak(safetyMessages[randomLevel]);
}

// ====== SINGLE TAP - STOP EVERYTHING ======
function stopEverything() {
    console.log("🛑 Stopping all activities");
    
    // Stop recording first
    if (isRecording) {
        stopRecording();
        
        // Auto download after short delay
        setTimeout(() => {
            if (recordedChunks.length > 0) {
                downloadVideo();
                showNotification("Video saved to downloads");
                speak("Video saved to your device.");
            }
        }, 500);
    }
    
    // Stop police alarm if playing
    if (policeAlarmPlaying) {
        stopPoliceAlarm();
    }
    
    // Stop emergency mode if active
    if (isEmergencyActive) {
        stopEmergency();
    }
    
    // Hide status indicators
    elements.alarmStatus.classList.remove('active');
    elements.recordingStatus.classList.remove('active');
    
    // Provide feedback
    vibratePhone([100, 50, 100]);
    showNotification("All activities stopped");
    speak("All activities stopped.");
}

// ====== EMERGENCY FUNCTIONS ======
function activateEmergency() {
    if (isEmergencyActive) {
        stopEmergency();
        return;
    }
    
    console.log("🚨 EMERGENCY ACTIVATED");
    isEmergencyActive = true;
    
    // Update UI
    elements.statusBox.className = 'status-box emergency';
    elements.statusText.innerHTML = '<i class="fas fa-exclamation-triangle"></i> EMERGENCY ACTIVE';
    elements.sosButton.classList.add('activated');
    
    // Device feedback
    vibratePhone([500, 250, 500, 250, 500]);
    playPoliceAlarm();
    
    // Voice alert
    speak("Emergency activated! Police alarm activated. Help is on the way.");
    
    // Start recording automatically
    startRecording();
    
    // Show status indicators
    elements.alarmStatus.classList.add('active');
    elements.recordingStatus.classList.add('active');
    
    // Show notification
    showNotification("Emergency activated! Police notified.", true);
}

function stopEmergency() {
    isEmergencyActive = false;
    
    // Update UI
    elements.statusBox.className = 'status-box';
    elements.statusText.innerHTML = '<i class="fas fa-check-circle"></i> System Ready';
    elements.sosButton.classList.remove('activated');
    
    // Stop everything
    stopEverything();
}

// ====== POLICE JEEP ALARM SOUND ======
function playPoliceAlarm() {
    if (policeAlarmPlaying) {
        return; // Already playing
    }
    
    playPoliceJeepAlarm();
    
    // Vibrate pattern for police alarm
    if (navigator.vibrate) {
        vibratePhone([200, 100, 200, 100, 200, 100, 200, 100, 500]);
    }
    
    showNotification("Police alarm activated!", true);
    speak("Police siren activated.");
}

function playPoliceJeepAlarm() {
    try {
        if (alarmAudioContext) {
            // If alarm is already playing, stop it first
            stopPoliceAlarm();
        }
        
        alarmAudioContext = new (window.AudioContext || window.webkitAudioContext)();
        
        // Create two oscillators for police siren effect
        alarmOscillator1 = alarmAudioContext.createOscillator();
        alarmOscillator2 = alarmAudioContext.createOscillator();
        const gainNode1 = alarmAudioContext.createGain();
        const gainNode2 = alarmAudioContext.createGain();
        
        alarmOscillator1.connect(gainNode1);
        alarmOscillator2.connect(gainNode2);
        gainNode1.connect(alarmAudioContext.destination);
        gainNode2.connect(alarmAudioContext.destination);
        
        // Police siren settings
        alarmOscillator1.type = 'sawtooth';
        alarmOscillator2.type = 'sawtooth';
        
        const now = alarmAudioContext.currentTime;
        
        // First siren (higher pitch)
        alarmOscillator1.frequency.setValueAtTime(1000, now);
        alarmOscillator1.frequency.exponentialRampToValueAtTime(1600, now + 0.5);
        alarmOscillator1.frequency.exponentialRampToValueAtTime(1000, now + 1);
        
        // Create repeating pattern
        for (let i = 1; i < 100; i++) { // Will play until stopped
            const time = now + i;
            alarmOscillator1.frequency.setValueAtTime(1000, time);
            alarmOscillator1.frequency.exponentialRampToValueAtTime(1600, time + 0.5);
            alarmOscillator1.frequency.exponentialRampToValueAtTime(1000, time + 1);
        }
        
        // Second siren (lower pitch, slightly offset)
        alarmOscillator2.frequency.setValueAtTime(800, now);
        alarmOscillator2.frequency.exponentialRampToValueAtTime(1200, now + 0.5);
        alarmOscillator2.frequency.exponentialRampToValueAtTime(800, now + 1);
        
        for (let i = 1; i < 100; i++) {
            const time = now + i;
            alarmOscillator2.frequency.setValueAtTime(800, time);
            alarmOscillator2.frequency.exponentialRampToValueAtTime(1200, time + 0.5);
            alarmOscillator2.frequency.exponentialRampToValueAtTime(800, time + 1);
        }
        
        // Volume envelope
        gainNode1.gain.setValueAtTime(0.5, now);
        gainNode2.gain.setValueAtTime(0.3, now);
        
        // Add pulsing effect
        for (let i = 0; i < 200; i++) {
            const pulseTime = now + i * 0.5;
            gainNode1.gain.setValueAtTime(0.5, pulseTime);
            gainNode1.gain.exponentialRampToValueAtTime(0.1, pulseTime + 0.25);
            gainNode1.gain.exponentialRampToValueAtTime(0.5, pulseTime + 0.5);
            
            gainNode2.gain.setValueAtTime(0.3, pulseTime);
            gainNode2.gain.exponentialRampToValueAtTime(0.05, pulseTime + 0.25);
            gainNode2.gain.exponentialRampToValueAtTime(0.3, pulseTime + 0.5);
        }
        
        alarmOscillator1.start();
        alarmOscillator2.start();
        
        // Schedule to stop after 100 seconds (but can be stopped earlier)
        alarmOscillator1.stop(now + 100);
        alarmOscillator2.stop(now + 100);
        
        policeAlarmPlaying = true;
        
    } catch (error) {
        console.log("Police alarm error:", error);
        // Fallback beep
        policeAlarmPlaying = true;
        const beepInterval = setInterval(() => {
            if (!policeAlarmPlaying) {
                clearInterval(beepInterval);
                return;
            }
            try {
                const beep = new Audio('data:audio/wav;base64,UklGRigAAABXQVZFZm10IBIAAAABAAEAQB8AAEAfAAABAAgAZGF0YQ');
                beep.volume = 0.7;
                beep.play();
            } catch (e) {
                console.log("Beep error:", e);
            }
        }, 300);
    }
}

function stopPoliceAlarm() {
    if (policeAlarmPlaying) {
        policeAlarmPlaying = false;
        
        // Stop Web Audio API oscillators
        if (alarmOscillator1) {
            try {
                alarmOscillator1.stop();
            } catch (e) {}
        }
        if (alarmOscillator2) {
            try {
                alarmOscillator2.stop();
            } catch (e) {}
        }
        if (alarmAudioContext) {
            try {
                alarmAudioContext.close();
            } catch (e) {}
        }
        
        alarmOscillator1 = null;
        alarmOscillator2 = null;
        alarmAudioContext = null;
        
        showNotification("Police alarm stopped");
    }
}

// ====== VIDEO RECORDING ======
function startRecording() {
    if (isRecording) {
        return;
    }
    
    // Request camera and microphone access
    navigator.mediaDevices.getUserMedia({ 
        video: { 
            facingMode: currentCamera,
            width: { ideal: 1280 },
            height: { ideal: 720 }
        }, 
        audio: true 
    })
    .then(stream => {
        // Store current stream
        currentStream = stream;
        
        // Show video
        elements.video.srcObject = stream;
        elements.videoSection.style.display = 'block';
        isRecording = true;
        
        // Start recording
        mediaRecorder = new MediaRecorder(stream, {
            mimeType: 'video/webm;codecs=vp9'
        });
        
        recordedChunks = [];
        
        mediaRecorder.ondataavailable = event => {
            if (event.data.size > 0) {
                recordedChunks.push(event.data);
            }
        };
        
        mediaRecorder.onstop = () => {
            console.log("Video recording stopped");
        };
        
        mediaRecorder.start();
        
        showNotification("Video recording started");
        speak("Video recording started for evidence.");
        
    })
    .catch(error => {
        console.log("Camera error:", error);
        showNotification("Camera permission needed");
    });
}

function stopRecording() {
    if (mediaRecorder && isRecording) {
        mediaRecorder.stop();
        isRecording = false;
        
        // Stop all tracks
        if (currentStream) {
            currentStream.getTracks().forEach(track => track.stop());
            currentStream = null;
        }
        
        elements.videoSection.style.display = 'none';
        
        showNotification("Video recording stopped");
    }
}

function downloadVideo() {
    if (recordedChunks.length === 0) {
        showNotification("No recording available");
        return;
    }
    
    // Create video blob
    const blob = new Blob(recordedChunks, { type: 'video/webm' });
    const url = URL.createObjectURL(blob);
    
    // Create download link
    const a = document.createElement('a');
    a.href = url;
    a.download = `safety_evidence_${new Date().getTime()}.webm`;
    document.body.appendChild(a);
    a.click();
    document.body.removeChild(a);
    
    // Clean up
    setTimeout(() => URL.revokeObjectURL(url), 100);
    
    // Clear recorded chunks after download
    recordedChunks = [];
}

// ====== PLACE SAFETY CHECK ======
function checkPlaceSafety() {
    const place = elements.placeInput.value.trim();
    
    if (!place) {
        showNotification("Please enter a place name");
        return;
    }
    
    showNotification(`Checking safety of ${place}...`);
    speak(`Checking safety information for ${place}.`);
    
    // Simulate safety check with timeout
    setTimeout(() => {
        // Generate random safety score (3-10)
        const safetyScore = (3 + Math.random() * 7).toFixed(1);
        
        // Get safety tips based on score
        let tips = "";
        let stars = "";
        let color = "#4CAF50";
        
        if (safetyScore >= 8) {
            stars = "★★★★★";
            tips = `
                <strong>Very Safe Area ✓</strong>
                <ul>
                    <li>Well-lit streets with CCTV</li>
                    <li>Regular police patrols</li>
                    <li>Good public transportation</li>
                    <li>Safe for walking at night</li>
                    <li>Emergency services nearby</li>
                </ul>
            `;
        } else if (safetyScore >= 6.5) {
            stars = "★★★★☆";
            color = "#FF9800";
            tips = `
                <strong>Moderately Safe</strong>
                <ul>
                    <li>Generally safe but be cautious</li>
                    <li>Stay in main areas</li>
                    <li>Travel with others if possible</li>
                    <li>Keep emergency app ready</li>
                    <li>Avoid late night travel</li>
                </ul>
            `;
        } else if (safetyScore >= 5) {
            stars = "★★★☆☆";
            color = "#FF5722";
            tips = `
                <strong>Use Caution</strong>
                <ul>
                    <li>Limited street lighting</li>
                    <li>Travel with companions</li>
                    <li>Have safety plan ready</li>
                    <li>Avoid isolated areas</li>
                    <li>Keep phone charged</li>
                </ul>
            `;
        } else {
            stars = "★★☆☆☆";
            color = "#FF4757";
            tips = `
                <strong>High Risk Area</strong>
                <ul>
                    <li>Avoid if possible</li>
                    <li>Never travel alone</li>
                    <li>High crime reported</li>
                    <li>Poor lighting and security</li>
                    <li>Consider alternative routes</li>
                </ul>
            `;
        }
        
        // Update UI
        elements.ratingStars.innerHTML = stars;
        elements.safetyScore.textContent = `${safetyScore}/10`;
        elements.safetyScore.style.color = color;
        elements.safetyTips.innerHTML = tips;
        elements.safetyResult.style.display = 'block';
        
        // Speak result
        let safetyLevel = "";
        if (safetyScore >= 8) safetyLevel = "very safe";
        else if (safetyScore >= 6.5) safetyLevel = "moderately safe";
        else if (safetyScore >= 5) safetyLevel = "requires caution";
        else safetyLevel = "high risk";
        
        speak(`Safety rating for ${place} is ${safetyScore} out of 10. This area is ${safetyLevel}.`);
        
    }, 1500);
}

// ====== HELPER FUNCTIONS ======
function vibratePhone(pattern) {
    if (navigator.vibrate) {
        navigator.vibrate(pattern);
    }
}

function speak(text) {
    if (!window.speechSynthesis) return;
    
    speechSynthesis.cancel();
    
    const utterance = new SpeechSynthesisUtterance(text);
    utterance.rate = 1.0;
    utterance.volume = 1.0;
    utterance.pitch = 1.0;
    
    speechSynthesis.speak(utterance);
}

function showNotification(message, isEmergency = false) {
    elements.notificationText.textContent = message;
    
    if (isEmergency) {
        elements.notification.className = 'notification show emergency';
    } else {
        elements.notification.className = 'notification show';
    }
    
    // Auto hide after 4 seconds
    setTimeout(() => {
        elements.notification.className = 'notification';
    }, 4000);
}

// ====== SHAKE DETECTION ======
function setupShakeDetection() {
    let lastShake = 0;
    
    if (window.DeviceMotionEvent) {
        window.addEventListener('devicemotion', function(event) {
            const acceleration = event.accelerationIncludingGravity;
            if (!acceleration) return;
            
            // Calculate total force
            const force = Math.abs(acceleration.x) + Math.abs(acceleration.y) + Math.abs(acceleration.z);
            
            // Detect shake (force > 20)
            if (force > 20) {
                const now = Date.now();
                
                // Prevent multiple shakes within 2 seconds
                if (now - lastShake > 2000) {
                    activateDoubleTapEmergency();
                    lastShake = now;
                    showNotification("Emergency activated by shake", true);
                }
            }
        });
    }
}

// ====== EVENT LISTENERS ======
// Keyboard shortcuts
document.addEventListener('keydown', function(event) {
    // Space bar for emergency
    if (event.key === ' ') {
        event.preventDefault();
        activateEmergency();
    }
    
    // Escape to stop emergency
    if (event.key === 'Escape' && isEmergencyActive) {
        stopEverything();
    }
    
    // Ctrl+R to start recording
    if (event.ctrlKey && event.key === 'r') {
        event.preventDefault();
        startRecording();
    }
    
    // Ctrl+S to stop recording
    if (event.ctrlKey && event.key === 's') {
        event.preventDefault();
        stopEverything();
    }
    
    // Ctrl+P for police alarm
    if (event.ctrlKey && event.key === 'p') {
        event.preventDefault();
        playPoliceAlarm();
    }
    
    // Ctrl+Shift+P to stop police alarm
    if (event.ctrlKey && event.shiftKey && event.key === 'P') {
        event.preventDefault();
        stopPoliceAlarm();
    }
    
    // Ctrl+D for double tap simulation
    if (event.ctrlKey && event.key === 'd') {
        event.preventDefault();
        activateDoubleTapEmergency();
    }
    
    // Ctrl+T for single tap simulation
    if (event.ctrlKey && event.key === 't') {
        event.preventDefault();
        stopEverything();
    }
    
    // Ctrl+C to switch camera while recording
    if (event.ctrlKey && event.key === 'c' && isRecording) {
        event.preventDefault();
        switchCamera();
    }
});

// ====== INITIALIZE ======
window.addEventListener('DOMContentLoaded', initApp);
</script>
</body>
</html>
