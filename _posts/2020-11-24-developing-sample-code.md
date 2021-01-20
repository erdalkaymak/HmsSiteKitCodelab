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
<pre><div id="copy-button11" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>view.getMyTextView().setOnEditorActionListener(TextView.OnEditorActionListener { textView, actionId, keyEvent -&gt;
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
<p>In the object, the  <strong>query</strong> parameter is mandatory, and other parameters are optional:<br /></p>
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
<aside class="special">
	<p><strong>Note:<strong> If both <strong>poiType<strong> and <strong>HwPoiType<strong> are set, search results of <strong>HwPoiType<strong> take precedence. The following formula must be met: pageIndex * pageSize &lt;= 60.</strong></strong></strong></strong></strong></strong></strong></strong></p>
</aside>
<p><strong>7. Locate TODO for calling textSearch method by passing the request object and SearchResultListener in KeywordSearchPresenter.kt class </strong></p>
<pre><div id="copy-button12" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>//TODO Call textSearch method by passing request object and SearchResultListener
<span class="pln">
</span></code></pre>
<p><strong>8. Complete the TODO with the following code block.</strong></p>
<pre><div id="copy-button11" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code><div>searchService!!.textSearch(textSearchRequest, object :
    SearchResultListener<TextSearchResponse> {
    override fun onSearchResult(textSearchResponse: TextSearchResponse) {
        if (textSearchResponse.sites != null) {
            view.showAllSites(textSearchResponse.sites as ArrayList<Site>)
        } else {
            view.showMessage("Sorry, we couldn't find any results matching with your query ")
        }
    }
    override fun onSearchError(searchStatus: SearchStatus) {
        Log.e(KeywordSearchActivity.TAG, "onSearchError is: " + searchStatus.errorCode)
    }
})
<span class="pln">
</span></div></code></pre>
<p><strong>9. Locate TODO for setting request body of Nearby Place Search function in NearbyPlaceSearchPresenter.kt class.</strong></p>
<pre><div id="copy-button14" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>//TODO Set request body of Nearby Place Search function.
<span class="pln">
</span></code></pre>
<p><strong>10. Complete the TODO with the following code block.</strong></p>
<pre><div id="copy-button15" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>nearbySearchRequest!!.location =  Coordinate(Constants.MY_LAT, Constants.MY_LNG)
nearbySearchRequest!!.radius = 4000
nearbySearchRequest!!.query = view.getMyText()
nearbySearchRequest!!.poiType = view.getMyType()
//nearbySearchRequest!!.hwPoiType
nearbySearchRequest!!.language = "en"
nearbySearchRequest!!.pageSize = 10
nearbySearchRequest!!.pageIndex = 1
<span class="pln">
</span></code></pre>
<p>In the object, the  <strong>location</strong> parameter is mandatory, and other parameters are optional:<br></p>
<ul>
	<li><strong>location:</strong> current location of a user.</li>
	<li><strong>radius:</strong> search radius, in meters. The value ranges from 1 to 50000. The default value is <strong>1000</strong>. The search radius is used to specify an area where places are searched in priority, but not restrict the search result to this area.</li>
	<li><strong>query:</strong> search keyword.</li>
	<li><strong>poiType:</strong> POI type of returned places. The value range is the same as that of <a href="https://developer.huawei.com/consumer/en/doc/HMSCore-References/api-locationtype-0000001050154741-V5" target="_blank">LocationType</a>.</li>
  <li><strong>HwPoiType:</strong> Huawei POI type of returned places. This parameter is recommended. The value range is the same as that of <a href="https://developer.huawei.com/consumer/en/doc/HMSCore-References/api-hwlocationtype-0000001050154745-V5" target="_blank">HwLocationType</a>.</li>
  <li><strong>language:</strong> language in which search results are displayed. For details about the value range, please refer to language codes in <a href="https://developer.huawei.com/consumer/en/doc/HMSCore-Guides-V5/language-mapping-0000001050162856-V5" target="_blank">Language Mapping</a>. If this parameter is not passed, English will be used. If English is unavailable, the local language will be used.</li>
  <li><strong>pageSize:</strong> number of records on each page. The value ranges from 1 to 20. The default value is <strong>20</strong>.</li>
  <li><strong>pageIndex:</strong> current page number. The value ranges from 1 to 60. The default value is <strong>1</strong>.</li>
</ul>
<aside class="special">
	<p><strong>Note:<strong> If both <strong>poiType<strong> and <strong>HwPoiType<strong> are set, search results of <strong>HwPoiType<strong> take precedence. The following formula must be met: pageIndex * pageSize &lt;= 60.</strong></strong></strong></strong></strong></strong></strong></strong></p>
</aside> 
<p><strong>11. Locate TODO for calling nearbySearch method by passing request object and SearchResultListener in NearbyPlaceSearchPresenter.kt class.</strong></p>
<pre><div id="copy-button14" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>//TODO Call nearbySearch method by passing request object and SearchResultListener
<span class="pln">
</span></code></pre>
<p><strong>12. Complete the TODO with the following code block.</strong></p>
<pre><div id="copy-button15" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>searchService!!.nearbySearch(nearbySearchRequest, object:
    SearchResultListener<NearbySearchResponse> {
    override fun onSearchResult(nearbySearchResponse: NearbySearchResponse) {
        if (nearbySearchResponse.sites != null) {
            view.showAllSites(nearbySearchResponse.sites as ArrayList<Site>)
        } else {
            view.showMessage("Sorry, we couldn't find any results matching with your query ")
        }
    }
    @SuppressLint("LongLogTag")
    override fun onSearchError(searchStatus: SearchStatus) {
        Log.e(NearbyPlaceSearchActivity.TAG, "onSearchError is: " + searchStatus.errorCode)
    }
})
<span class="pln">
</span></code></pre>
<p><strong>13. Locate TODO for setting request body of Place Detail Search function in PlaceDetailSearchPresenter.kt class.</strong></p>
<pre><div id="copy-button14" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>//TODO Set request body of Place Detail Search function.
<span class="pln">
</span></code></pre>
<p><strong>14. Complete the TODO with the following code block.</strong></p>
<pre><div id="copy-button15" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>view.getResponse().text = null
//detailSearchRequest!!.siteId = "707417C262FF450B4858ABD02A6479AB"
detailSearchRequest!!.siteId = view.getSiteID()
//detailSearchRequest!!.language = "tr"
detailSearchRequest!!.language = view.getLang()
<span class="pln">
</span></code></pre>
<p>In the object, the  <strong>siteID</strong> parameter is mandatory, and other parameters are optional:<br></p>
<ul>
	<li><strong>siteID:</strong> ID of a place.</li>
	<li><strong>Language:</strong> language in which search results are displayed. If this parameter is not passed, the local language will be used.</li>
</ul>
<p><strong>15. Locate TODO for calling detailSearch method by passing request object and SearchResultListener in PlaceDetailSearchPresenter.kt class.</strong></p>
<pre><div id="copy-button14" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>//TODO Call detailSearch method by passing request object and SearchResultListener
<span class="pln">
</span></code></pre>
<p><strong>16. Complete the TODO with the following code block.</strong></p>
<pre><div id="copy-button15" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>searchService!!.detailSearch(detailSearchRequest, object:
    SearchResultListener<DetailSearchResponse> {
    override fun onSearchResult(detailSearchResponse: DetailSearchResponse) {
        if (detailSearchResponse.site != null) {
            view.getResponse().text = Convert.convertToString(detailSearchResponse,true )
        } else {
            view.showMessage("Sorry, we couldn't find any results matching with your query ")
        }
    }
    @SuppressLint("LongLogTag")
    override fun onSearchError(searchStatus: SearchStatus) {
        Log.e(PlaceDetailSearchActivity.TAG, "onSearchError is: " + searchStatus.errorCode)
        view.getResponse().text = searchStatus.errorMessage
    }
})
<span class="pln">
</span></code></pre>
<p><strong>17. Locate TODO for setting request body of Place Search Suggestion function in PlaceSearchSuggestionPresenter.kt class.</strong></p>
<pre><div id="copy-button14" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>//TODO Set request body of Place Search Suggestion function.
<span class="pln">
</span></code></pre>
<p><strong>18. Complete the TODO with the following code block.</strong></p>
<pre><div id="copy-button15" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>querySuggestionRequest!!.query = view.getMyText()
querySuggestionRequest!!.location = Coordinate(Constants.MY_LAT, Constants.MY_LNG)
querySuggestionRequest!!.radius = 10000
//querySuggestionRequest!!.bounds = CoordinateBounds()
//querySuggestionRequest!!.poiTypes = LocationType.
querySuggestionRequest!!.countryCode = "TR"
querySuggestionRequest!!.language = "tr"
<span class="pln">
</span></code></pre>
<p>In the object, the  <strong>query</strong> parameter is mandatory, and other parameters are optional:<br></p>
<ul>
	<li><strong>query:</strong> search keyword.</li>
	<li><strong>location:</strong> longitude and latitude to which search results need to be biased.</li>
	<li><strong>radius:</strong> search radius, in meters. The value ranges from 1 to 50000. The default value is <strong>50000</strong>. The search radius is used to specify an area where places are searched in priority, but not restrict the search result to this area.</li>
	<li><strong>bounds:</strong> coordinate bounds to which search results need to be biased.</li>
  <li><strong>poiTypes:</strong> List of POI types. The value range is a subset of <a href="https://developer.huawei.com/consumer/en/doc/HMSCore-References/api-locationtype-0000001050154741-V5" target="_blank">LocationType</a>.</li>
  <li><strong>countryCode:</strong> code of the country where places are searched, which complies with the ISO 3166-1 alpha-2 standard.</li>
  <li><strong>language:</strong> language in which search results are displayed. For details about the value range, please refer to language codes in <a href="https://developer.huawei.com/consumer/en/doc/HMSCore-Guides-V5/language-mapping-0000001050162856-V5" target="_blank">Language Mapping</a>. If this parameter is not passed, English will be used. If English is unavailable, the local language will be used.</li>
</ul>
<p><strong>19. Locate TODO for calling querySuggestion method by passing request object and SearchResultListener PlaceSearchSuggestionPresenter.kt class.</strong></p>
<pre><div id="copy-button14" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>//TODO Call querySuggestion method by passing request object and SearchResultListener
<span class="pln">
</span></code></pre>
<p><strong>20. Complete the TODO with the following code block.</strong></p>
<pre><div id="copy-button15" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>searchService!!.querySuggestion(querySuggestionRequest, object:
    SearchResultListener<QuerySuggestionResponse> {
    override fun onSearchResult(querySuggestionResponse: QuerySuggestionResponse?) {
        if (querySuggestionResponse!!.sites != null) {
            view.getMyTextView().visibility = View.INVISIBLE
            view.showAllSites(querySuggestionResponse.sites as ArrayList<Site>)
        } else {
            view.showMessage("Sorry, we couldn't find any results matching with your query ")
        }
    }

    @SuppressLint("LongLogTag")
    override fun onSearchError(searchStatus: SearchStatus?) {
        if (searchStatus != null) {
            Log.e(PlaceSearchSuggestionActivity.TAG, "onSearchError is: " + searchStatus.errorCode)
        }
    }
})
<span class="pln">
</span></code></pre>
<p><strong>21. Locate TODO to instantiate SearchFragment for Widget in WidgetActivity.kt class.</strong></p>
<pre><div id="copy-button14" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>//TODO Instantiate SearchFragment for Widget
<span class="pln">
</span></code></pre>
<p><strong>22. Complete the TODO with the following code block.</strong></p>
<pre><div id="copy-button15" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>searchFragment = (supportFragmentManager.findFragmentById(R.id.widget_fragment) 
as SearchFragment?)!!
<span class="pln">
</span></code></pre>
<p><strong>23. Locate TODO for Setting API Key and SiteSelectionListener to fetch the suggested places in WidgetPresenter.kt class.</strong></p>
<pre><div id="copy-button14" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>//TODO Set API Key and SiteSelectionListener to fetch suggested places
<span class="pln">
</span></code></pre>
<p><strong>24. Complete the TODO with the following code block.</strong></p>
<pre><div id="copy-button15" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>view.getMyFragment().setApiKey(Constants.API_KEY)
view.getMyFragment().setOnSiteSelectedListener(object : SiteSelectionListener {
    @SuppressLint("SetTextI18n")
    override fun onSiteSelected(site: Site) {
       view.showMySite(site)
    }
    override fun onError(searchStatus: SearchStatus) {
        view.showMessage("Sorry, we couldn't find any results matching with your query ")
    }
})
<span class="pln">
</span></code></pre>
<p><strong>25. Locate TODO for Using Site object to show details of selected places on Widget in WidgetActivity.kt class.</strong></p>
<pre><div id="copy-button14" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>//TODO Use Site object to show details of selected places on Widget
<span class="pln">
</span></code></pre>
<p><strong>26. Complete the TODO with the following code block.</strong></p>
<pre><div id="copy-button15" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>textName.text = site.name
textAddr.text = site.formatAddress
textLocation.text = "Lat: " + site.location.lat + ", " + "Lng: " + site.location.lng
phno.text = "Phone: " + site.poi.internationalPhone
card.visibility = View.VISIBLE
<span class="pln">
</span></code></pre>


