---
title: Complete the Essentials in the Code
description: 15
---

<p><strong>1. Locate and open *presenter.kt classes. Locate the TODO for creating a SearchService instance and request object in all presenter classes.</strong></p>
<pre><div id="copy-button10" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>//TODO Create a SearchService instance and instantiate request object
<span class="pln">
</span></code></pre>
<p><strong>2. Complete the code for presenter classes except Widget.</strong></p>
<pre><div id="copy-button11" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>try {
    searchService = SearchServiceFactory.create(App.context, URLEncoder.encode(Constants.API_KEY, "utf-8"))
} catch (e: UnsupportedEncodingException) {
    Log.e(KeywordSearchActivity.TAG, "encode apikey error")
}

// instantiate request object in corresponding presenter classes
textSearchRequest = TextSearchRequest()//Keyword Search
nearbySearchRequest = NearbySearchRequest()//Nearby Place Search
detailSearchRequest = DetailSearchRequest()//Place Detail Search
querySuggestionRequest = QuerySuggestionRequest()//Place Search Suggestion
<span class="pln">
</span></code></pre>
<p><strong>3. Locate TODO for setting editor action listener of Keyword Search function in KeywordSearchPresenter.kt class.</strong></p>
<pre><div id="copy-button10" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>//TODO Set editor action listener of Keyword Search function.
<span class="pln">
</span></code></pre>
<p><strong>4. Complete the TODO with the following code block.</strong></p>
<pre><div id="copy-button11" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>view.getMyTextView().setOnEditorActionListener(TextView.OnEditorActionListener { textView, actionId, keyEvent ->
    if (actionId == EditorInfo.IME_ACTION_SEARCH || actionId == EditorInfo.IME_ACTION_DONE || keyEvent.action == KeyEvent.ACTION_DOWN || keyEvent.action == KeyEvent.KEYCODE_ENTER) {
        search()
        view.hideSoftKeyboard()
        return@OnEditorActionListener true
    }
    false
})
<span class="pln">
</span></code></pre>
<p><strong>5. Locate TODO for setting request body of Keyword Search function in KeywordSearchPresenter.kt class.</strong></p>
<pre><div id="copy-button10" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>//TODO Set request body of Keyword Search function.
<span class="pln">
</span></code></pre>
<p><strong>6. Complete the TODO with the following code block.</strong></p>
<pre><div id="copy-button11" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>//Specify Query Parameters
textSearchRequest!!.query = view.getMyText() 
//textSearchRequest!!.location = Coordinate(Constants.MY_LAT, Constants.MY_LNG)
//textSearchRequest!!.radius = 4000  
//textSearchRequest!!.poiType  
//textSearchRequest!!.hwPoiType = HwLocationType.RESTAURANT 
textSearchRequest!!.countryCode = "TR"   
textSearchRequest!!.language = "en" 
textSearchRequest!!.pageSize = 10 
textSearchRequest!!.pageIndex = 1 
<span class="pln">
</span></code></pre>
<p>In the object, the  <strong>query</strong> parameter is mandatory, and other parameters are optional:<br></p>
<ul>
	<li><strong>query:</strong> search keyword.</li>
	<li><strong>location:</strong> longitude and latitude to which search results need to be biased.</li>
	<li><strong>radius:</strong> search radius, in meters. The value ranges from 1 to 50000. The default value is <strong>50000:</strong>.</li>
	<li><strong>poiType:</strong> POI type. The value range is the same as that of <a href="https://developer.huawei.com/consumer/en/doc/development/HMSCore-References/api-locationtype-0000001050154741" target="_blank">LocationType</a>.</li>
  <li><strong>HwPoiType:</strong> Huawei POI type. This parameter is recommended. The value range is the same as that of  <a href="https://developer.huawei.com/consumer/en/doc/development/HMSCore-References/api-hwlocationtype-0000001050154745" target="_blank">HwLocationType</a>.</li>
  <li><strong>countryCode:</strong> code of the country where places are searched. The country code must comply with the ISO 3166-1 alpha-2 standard.</li>
  <li><strong>language:</strong> language in which search results are displayed. For details about the value range, please refer to language codes in  <a href="https://developer.huawei.com/consumer/en/doc/development/HMSCore-Guides/language-mapping-0000001050162856" target="_blank">LanguageMapping</a>. If this parameter is not passed, the language of the <strong>query:</strong> field is used in priority. If the field language is unavailable, the local language will be used.</li>
  <li><strong>pageSize:</strong> number of records on each page. The value ranges from 1 to 20. The default value is <strong>20</strong>.</li>
  <li><strong>pageIndex:</strong> current page number. The value ranges from 1 to 60. The default value is <strong>1</strong>.</li>
</ul>
<p><strong>3. Locate following line and set the EditTexts Urls in MainActivity to play related buttons</strong></p>
<pre><div id="copy-button12" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>   // TODO Set video Url or Urls
<span class="pln">
</span></code></pre>
<p><strong>4.Set the EditTexts Urls </strong></p>
<pre><div id="copy-button13" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code> edtUrl.setText(resources.getString(R.string.single_url))
 edtMultipleUrl.setText(resources.getString(R.string.multiple_url))
 <span class="pln">
</span></code></pre>
<p><strong>5. Locate following line and create Wise Player Instance in WisePlayerInit Object. </strong></p>
<pre><div id="copy-button14" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  // TODO Initializing of Wise Player Instance
<span class="pln">
</span></code></pre>
<p><strong>6. Create Wise Player Instance</strong></p>
<pre><div id="copy-button15" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  return wisePlayerFactory.createWisePlayer()
<span class="pln">
</span></code></pre>
<aside class="special">
	<p><strong>Note: Frame Layout is necessary for SurfaceView to display videos, otherwise only audio will be listened</strong></p>
</aside>
<br><img style="width: 400.00px" src="https://raw.githubusercontent.com/bekiryavuzkoc/testRepo/gh-pages/assets/framelayout.PNG" onclick="imageclick(src)">
<p><strong>7. Locate following line in Play Activity.</strong></p>
<pre><div id="copy-button17" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  //TODO Setting the Listeners
<span class="pln">
</span></code></pre>
<p><strong>8. Set listeners in Play Activity.</strong></p>
<pre><div id="copy-button18" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  player.setReadyListener(this)
  player.setErrorListener(this)
  player.setEventListener(this)
  player.setResolutionUpdatedListener(this)
  player.setLoadingListener(this)
  player.setPlayEndListener(this)
  player.setSeekEndListener(this)
  <span class="pln">
</span></code></pre>
<p><strong>9. Locate following line in Play Activity.</strong></p>
<pre><div id="copy-button19" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code> //TODO Callback Listener
<span class="pln">
</span></code></pre>
<p><strong>10. Set the Callback Listener in Play Activity.</strong></p>
<pre><div id="copy-button20" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  surfaceView.holder.addCallback(this)
<span class="pln">
</span></code></pre>
<p><strong>11. Locate following line in Play Activity.</strong></p>
<pre><div id="copy-button21" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code> //TODO Callback Listener
<span class="pln">
</span></code></pre>
<p><strong>12. Set the Seekbar Listener in Play Activity.</strong></p>
<pre><div id="copy-button22" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  seekBar.setOnSeekBarChangeListener(this)
<span class="pln">
</span></code></pre>
<p><strong>13. Locate following line in Play Activity.</strong></p>
<pre><div id="copy-button23" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  //TODO Starting the Player
	<span class="pln">
</span></code></pre>
<p><strong>14. Start Wise Player in Play Activity.</strong></p>
<pre><div id="copy-button24" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  player?.start()
<span class="pln">
</span></code></pre>
<p><strong>15. Locate following line in Play Activity. </strong></p>
<pre><div id="copy-button25" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  //TODO Surface Change
<span class="pln">
</span></code></pre>
<p><strong>16. Set surface change to Wise Player.</strong></p>
<pre><div id="copy-button26" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  player.setSurfaceChange()
<span class="pln">
</span></code></pre>
<p><strong>17. Locate following line in Play Activity. </strong></p>
<pre><div id="copy-button27" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  //TODO Surface Destroy
<span class="pln">
</span></code></pre>
<p><strong>18. Suspend the Wise Player if surface is destroyed.</strong></p>
<pre><div id="copy-button28" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  player.suspend()
<span class="pln">
</span></code></pre>
<p><strong>19. Locate following line in Play Activity. </strong></p>
<pre><div id="copy-button29" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  //TODO Surface Create
<span class="pln">
</span></code></pre>
<p><strong>20. Resume Wise Player with the current time when app is sent to foreground.</strong></p>
<pre><div id="copy-button30" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  player.setView(surfaceView)
  player.resume(PlayerConstants.ResumeType.KEEP)
<span class="pln">
</span></code></pre>
<p><strong>21. Locate following line in Play Activity.</strong></p>
<pre><div id="copy-button31" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  //TODO Release Wise Player
<span class="pln">
</span></code></pre>
<p><strong>22. Release Wise Player and listeners in Play Activity. </strong></p>
<pre><div id="copy-button32" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  player.setErrorListener(null)
  player.setEventListener(null)
  player.setResolutionUpdatedListener(null)
  player.setReadyListener(null)
  player.setLoadingListener(null)
  player.setPlayEndListener(null)
  player.setSeekEndListener(null)
  player.release()
<span class="pln">
</span></code></pre>
