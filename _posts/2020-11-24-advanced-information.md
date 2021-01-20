---
title: Test and Verification
description: 5
---

<p>Upon completing the essential parts of the code, connect your mobile device to the PC and enable the USB debugging mode. In the Android Studio window, run the project you have created in Android Studio to generate an APK. Then install the APK on the mobile device.</p>
  
<p><strong>1. Open the app upon installing it to your device.</strong></p>
<p><strong>2. Choose Keyword Search in main screen, type your keyword and press Enter.</strong></p>
<pre><div id="copy-button34" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  seekBar?.progress?.let {player.seek(it)}
<span class="pln">
</span></code></pre>

 <li><h3>Handler and Runnable:</h3></li>
<p>A Handler allows you to send and process Message and Runnable objects associated with a thread's MessageQueue. With the feature of Handler, we can update the UI elements for every 1 seconds.</p>
<p><strong>1. Locate following line in Play Activity.</strong></p>
<pre><div id="copy-button35" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  //TODO Handler and Runnable Implementation
<span class="pln">
</span></code></pre>
<p><strong>2. Implement the Wise Player’s seek method.</strong></p>
<pre><div id="copy-button36" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>        //Player UI
        configureControlView()
        //Text UI Elements 
        configureContentView()
        if (!mStopHandler) {
            mHandler.postDelayed(runnable, DELAY_SECOND)
        }
        <span class="pln">
</span></code></pre>
</ol>
