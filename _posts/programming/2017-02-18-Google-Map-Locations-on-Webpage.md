---
layout: page
#
# Content
#
subheadline: "Google Map Locations on Webpage"
title: "Display Locations on Google Map using HTML & Javascript"
teaser: "Do you want to use google maps on your site or in your project and wondering where to start? Than you likely will like the integration of <em>Google Maps</em>. It enables you to display Maps and put locations marakers on maps that looks in each browser delicious."
categories:
  - programming
tags:
  - HTML
  - JavaScript
  - CSS
#
# Styling
# 
# header: no
header:
  image_fullwidth: lrssalok1fu-rawpixel-com.jpg
image:
    title: screenshots/google_maps_places_javascript_api.jpg
    thumb: screenshots/google_maps_places_javascript_api.jpg
    homepage: lrssalok1fu-rawpixel-com.jpg
#    caption: Photo by UnSplash
#    caption_url: http://unsplash.com/
---

You can see working [Demo here][1].<br/>

Want to download this code head over to [My Code Repository][2].<br/>

Put your Google API Key on this line:<br/>
{% highlight javascript %}
<script type="text/javascript" src="https://maps.googleapis.com/maps/api/js?key=YourKey"></script>
{% endhighlight %}

<b>Note:</b><br/>
Replace <b>YourKey</b> value with the key you get from [Google Developer Site Maps Section][3] as the one I am using will not work with your site it is specific to my site.

Below is complete page code to display Google Map with markers using HTML & Javascript it requires Google Map API.<br/>

{% highlight html %}
<html>
<head>
    <meta name="viewport" content="width=device-width" />
    <title>Index</title>
</head>
<body>
    <div id="divMap" style="width: 500px; height: 500px">
    </div>
    <script type="text/javascript" src="https://maps.googleapis.com/maps/api/js?key=AIzaSyBip14VfDly0JQJXcMDy7wUVIdS-MfAiVo"></script>
    <script type="text/javascript">
        var markers = [{'title': 'Islamabad','lat': '33.669300','lng': '72.844800','description': 'Capital City of Pakistan. Lush green and great views and weather.'},{'title': 'Lahore','lat': '31.924600','lng': '74.284700','description': 'Lahore City of Lively People, is the Heart of the Pakistani Province Punjab.'}];
        window.onload = function () {
            var mapOptions = {
                center: new google.maps.LatLng(markers[0].lat, markers[0].lng),
                zoom: 7,
                mapTypeId: google.maps.MapTypeId.ROADMAP,
                //disableDefaultUI: true
                panControl: true,
                zoomControl: true,
                mapTypeControl: true,
                scaleControl: true,
                streetViewControl: true,
                overviewMapControl: true,
                rotateControl: true,
                mapTypeId: google.maps.MapTypeId.TERRAIN
            };
            var infoWindow = new google.maps.InfoWindow();
            var map = new google.maps.Map(document.getElementById("divMap"), mapOptions);
            for (i = 0; i < markers.length; i++) {
                var data = markers[i]
                var myLatlng = new google.maps.LatLng(data.lat, data.lng);
                var marker = new google.maps.Marker({
                    position: myLatlng,
                    map: map,
                    title: data.title,
                    animation: google.maps.Animation.BOUNCE
                });
                (function (marker, data) {
                    google.maps.event.addListener(marker, "click", function (e) {
                        infoWindow.setContent(data.description);
                        infoWindow.open(map, marker);
                    });
                })(marker, data);
            }
        }
    </script>

</body>
</html>
{% endhighlight %}


 [1]: https://gilyas.github.io/google_maps_apis.github.io/google_maps_places_api/google_map_places.html
 [2]: https://github.com/gilyas/google_maps_apis.github.io
 [3]: https://developers.google.com/maps/
