# LeonImageView [![](https://jitpack.io/v/am-Leon/LeonImageView.svg)](https://jitpack.io/#am-Leon/LeonImageView)

Leon is an android library written to makes it easy for the programmer to display a set of images in a simple way using Picasso.

## Installation

1- Add this library as a dependency in your app's build.project file.

```groovy

allprojects {  
      repositories {  
         maven { url 'https://jitpack.io' }  
      }  
   }  
   
   ```

2- Add the dependency.

```groovy

    implementation 'com.github.am-Leon:LeonImageView:v1.1.4'

```

## Usage

```text
- Used for Represent Single image view.
- set of images view in viewPager.
- Supporting (LTR, RTL) Directions.
- Images Features (Animated zooming, Zooming where it clicks,...)
- Reloading image in case of failure.
- Picasso features (place holder,error icon).
- Finger gesture swipe to destroy view of images in full screen.
- LoadImages through 4 ways (stings, files, Media, Uri).
- Load thumbnail view of youtube links and open video link on youtube app. using (media object).

```

<img src="demo.gif" width="250" height="400"/>

In Xml file.

```xml

    <am.leon.LeonImageView
        android:id="@+id/img_itemPhoto"
        android:layout_width="match_parent"
        android:layout_height="168dp"
        app:leon_default_icon=""
        app:leon_place_holder_icon=""
        app:leon_play_video_icon=""
        app:leon_reload_icon=""
        tools:src="@tools:sample/avatars" />

```

1- For Single image 
    - in your activity leon can load different types(String, File, Uri, Media).
    - when calling loadImage after, loading can click to open in full screen.

```java

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        LeonImageView imageView = findViewById(R.id.img_itemPhoto);
        
        // for string
        String path = "https://via.placeholder.com/250";
        imageView.loadImage(path);
        
        // for file
        File file = new File("your image file path");
        imageView.loadImage(file);
        
        // for uri object
        imageView.loadImage("uri object");
   
        // for resource object
        imageView.loadImage(R.drawable.ic_directions_bike_black_24dp);

        // for media object supports photos url and youtube url videos only
        Media media = new Media("https://via.placeholder.com/250", Media.TYPE_PHOTO);
        imageView.loadImage(media);
        
        Media media = new Media("https://www.youtube.com/watch?v=hGLuCMrUuFk", Media.TYPE_VIDEO);
        imageView.loadImage(media);
        
    }

}

```

2- For set of images
    - in adapter viewHolder use image setOnClickListener
    - for Rtl direction set "ar" 
    - for opening images list with specific position set position

```java

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        LeonImageView imageView = findViewById(R.id.img_itemPhoto);
        
        // for any type used from (String, File, Uri, Media, Drawable).
        imageView.loadImage("any type listed");
     
        //--------------------------------------Media List------------------------------------------
        
        // after loading image use setOnClickListener  
        // to open full screen view and load images list
        imageView.loadMediaImages(getImagesList());
        
        // for opening images list with specific position set position
        imageView.loadMediaImages(items, 2);
        
        // for Rtl direction set "ar" 
        imageView.loadMediaImages(items, 2, "ar");  
        
        //--------------------------------------Drawables List--------------------------------------
        
        // after loading image use setOnClickListener  
        // to open full screen view and load images list
        imageView.loadResImages(getIntegerList());
        
        // for opening images list with specific position set position
        imageView.loadResImages(items, 2);
        
        // for Rtl direction set "ar" 
        imageView.loadResImages(items, 2, "ar");
        
        // used for open full screen view.
        imageView.show();
        
    }
    
    
    private List<String> getImagesList() {
        List<String> mediaList = new ArrayList<>();

        mediaList.add("https://via.placeholder.com/210");
        mediaList.add("https://via.placeholder.com/220");
        mediaList.add("https://via.placeholder.com/230");
        mediaList.add("https://via.placeholder.com/240");
        mediaList.add("https://via.placeholder.com/250");
        mediaList.add("https://via.placeholder.com/260");

        return mediaList;
    }


    private List<Integer> getIntegerList() {
        List<Integer> integerList = new ArrayList<>();
        integerList.add(R.drawable.ic_delete_sweep_black_24dp);
        integerList.add(R.drawable.ic_directions_bike_black_24dp);

        return integerList;
    }
    
}


```

## License

```text
MIT License

Copyright (c) 2020 am-Leon

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

```
