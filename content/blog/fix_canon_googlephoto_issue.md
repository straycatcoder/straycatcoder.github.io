+++
title = 'Fix Not eligible for Storage Saver issue in Google Photos'
date = '2026-11-09T10:44:42-05:00'
draft = false
description = "Fix Not eligible for Storage Saver issues for Canon Canon PowerShot SX280 HS"
tags = ["old-hardware", "photo", "tips"]
+++

I noticed that the most photos from the old Canon PowerShot SX280 HS point-and-shot camera (2013) in Google Photos are marked as “Not eligible for Storage Saver”.  And the photos from Canon PowerShot S95 (2010) have no such issue.

According to the help, the issue is from Multi-Picture Format (MPF) or Embedded Data, basically SX280 adds the thumbnail preview directly into the JPEG file.

![Goat](/images/blog/goat_farm.jpg "Goat")

Using exiftool to check the exif of this goat image, MPF is in the metadata.

```
MPF Version                     : 0100
Number Of Images                : 2
MP Image Flags                  : Dependent child image
MP Image Format                 : JPEG
MP Image Type                   : Large Thumbnail (full HD equivalent)
MP Image Length                 : 624680
MP Image Start                  : 4340736
Preview Image                   : (Binary data 624680 bytes)
```

There is 624Kb preview directly inside the JPEG file using the MPF specification.

To remove the preview, run this command in the image folder, the processed images inside the cleaned_photos/ folder will have the MPF metadata and trailers stripped out.
 
```bash
exiftool -o cleaned_photos/ -MPF:All= -Trailer:All= .
```

Then upload the cleaned photos for storage saver, once confirmed everything is fine, the original photos can be removed from Google Photos.

The list of the impacted Canon cameras (pulled from Gemini AI):
* SX Series: SX240 HS, SX260 HS, SX270 HS, SX280 HS, SX50 HS, SX60 HS, SX500 IS, SX700/710/720 HS
* S Series: S100, S110, S120
* G Series: G15, G16, G1 X, G7
* XELPH / IXUS Series: 115 HS, 300 HS, 310 HS, 500 HS
