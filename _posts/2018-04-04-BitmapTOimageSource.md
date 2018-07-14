---
layout: post
title:  "BitmapTOimageSource"
image: ''
date:   2018-04-04 00:06:31
tags:
- C#
description: ''
categories:
- CS 
---

```csharp
 public static BitmapSource ChangeBitmapToBitmapSource(this Bitmap bmp)
        {
            BitmapSource returnSource;
            try
            {
                returnSource = Imaging.CreateBitmapSourceFromHBitmap(bmp.GetHbitmap(), IntPtr.Zero, Int32Rect.Empty, BitmapSizeOptions.FromEmptyOptions());
            }
            catch
            {
                returnSource = null;
            }
            return returnSource;
        }
```
