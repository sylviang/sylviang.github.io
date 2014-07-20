---
layout: post
type: text
title: Batch generate thumbnails using Image Magick
date: 2013-07-17 15:06:00
---

I was helping to populate content, only to realise the system wasn't smart enough to generate its own thumbnails. Someone told me to screenshot the 1st page of each pdf and then upload the image.

This is an utterly waste of time. Hence, I decided to write something to batch generate thumbnails using Image Magick.

Use the command below to generate 100 pixels wide image from the sample.pdf. the [0] means 1st page. You can select the page you want by inputing the page number - 1.

> convert -thumbnail 100x sample.pdf[0] sample.png

You can combine them with any PHP, Django script. I'm lazy so I use my Mac's Automator to batch execute it. You can also use the bash command below.

> for file in *.pdf; do convert $file[0] -thumbnail 100x -quality 85 -background white -flatten $file-tn.jpg; done