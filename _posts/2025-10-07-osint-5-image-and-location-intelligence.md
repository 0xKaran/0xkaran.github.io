---
layout: post
title: "OSINT EP05: Images, Geolocation & Metadata"
categories: [OSINT, IMINT, GEOINT]
---

They say a picture is worth a thousand words. In OSINT, a picture is worth a thousand data points. This episode focuses on **IMINT** (Imagery Intelligence) and **GEOINT** (Geospatial Intelligence).

### 1. Reverse Image Search (RIS)
*Don't just look at the image; look for where else it exists.*

Different search engines have different "brains." You must use the right one for the job.

* **[Google Images](https://images.google.com){:target="_blank"}:** The jack-of-all-trades. Good for identifying general contexts, but often censors facial search.
* **[Yandex Images](https://yandex.com/images){:target="_blank"}:** The heavy hitter. Unbelievably good at face matching, background landmark detection, and OCR (reading text on billboards in the background).
* **[Bing Visual Search](https://www.bing.com){:target="_blank"}:** Excellent for **Object Detection**. If you need to identify a specific brand of sunglasses or a car model, use Bing.
* **[TinEye](https://tineye.com){:target="_blank"}:** The "Exact Match" king. Perfect for seeing if an image is original or a stock photo/repost.

**Browser Extensions:**
* **Search By Image:** Adds a context menu to right-click any image and search across all these engines simultaneously.

---

### 2. Facial Recognition OSINT
*Finding people, not just pictures.*

* **[Search4Faces](https://search4faces.com){:target="_blank"}:** Specialized for VK/Russian databases, but surprisingly effective globally.
* **[PimEyes](https://pimeyes.com){:target="_blank"}:** The most powerful commercial face search. Paid, but highly effective.
* **[FaceCheck.id](https://facecheck.id){:target="_blank"}:** A strong alternative.

> **Pro Tip: Bypassing Paywalls/Blur**
> Sometimes services like FaceCheck show a match but blur the source.
> 1. Inspect Element (`F12`) on the blurred image.
> 2. Look for the image source URL. It might be a Base64 string (`data:image/webp:base64...`).
> 3. Copy the string and use a Base64 decoder. Sometimes the source URL is hidden within the metadata of that string.

---

### 3. Metadata (EXIF Data)
Every digital photo has a "fingerprint" unless it has been scrubbed.
* **What to look for:** GPS Coordinates, Device Model (iPhone 14 Pro), Date/Time original.
* **Note:** Social media (FB, Insta, Twitter) strips this data. You need original files (uploaded to blogs, forums, or sent via document mode).
* **Tools:**
    * **[ExifTool](https://exif.tools){:target="_blank"}:** Command line powerhouse.
    * **[Exif Viewer (Firefox Add-on)](https://addons.mozilla.org/en-US/firefox/addon/exif-viewer/){:target="_blank"}**

---

### 4. Geolocation Tools
*Where in the world is this?*

**AI Assistance:**
* **[GeoSpy.ai](https://geospy.ai){:target="_blank"}:** An AI model trained to guess locations based on vegetation, architecture, and lighting.

**Mapping Powerhouses:**
* **Google Maps:** Street view is essential. Don't forget the "Time Machine" feature in Street View to see how a building changed over years.
* **[Yandex Maps](https://yandex.com/maps){:target="_blank"}:** Excellent for Eastern Europe/Russia. Has unique "Pedestrian" and "heatmap" views.
* **[Mappls](https://www.mappls.com){:target="_blank"}:** The best detailed maps for **India**.
* **[DualMaps](https://data.mashedworld.com/dualmaps/map.htm){:target="_blank"}:** Splits your screen into Street View, Aerial View, and Map View simultaneously.

**Street Level Alternatives:**
If Google didn't drive there, someone else might have.
* **[Mapillary](https://www.mapillary.com){:target="_blank"}** & **[KartaView](https://kartaview.org){:target="_blank"}**: Crowdsourced dashcam footage.

### 5. Manual Geolocation Tips
1.  **Look for text:** Store signs, billboards, license plates. Translate them immediately.
2.  **The Sun:** Check shadows to determine cardinal direction (North/South).
3.  **Cross-Reference:** If the target's friend tagged them in a coffee shop, but the target didn't check in... verify the coffee shop's interior photos on Google Maps Reviews.
4.  **Gamify Learning:** Play **[GeoGuessr](https://www.geoguessr.com){:target="_blank"}** to train your brain to recognize soil, bollards, and electric poles.