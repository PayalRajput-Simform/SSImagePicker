# 📸SSImagePicker 

[![Android-Studio](https://img.shields.io/badge/Android%20Studio-4.0+-orange.svg?style=flat)](https://developer.android.com/studio/)
[![API](https://img.shields.io/badge/API-19%2B-brightgreen.svg?style=flat)](https://android-arsenal.com/api?level=19)
![Language](https://img.shields.io/badge/language-Kotlin-orange.svg)

Easy to use and configurable library to **Pick an image from the Gallery or Capture image using Camera**.

You can easily select image from camera and gallery and upload it wherever you want. I have created this library to simplify pick or capture image feature.

# Features :

* Capture Image Using Camera
* Pick Image From Gallery
* Handle Runtime Pemission For Storage And Camera
* ImagePicker Bottomsheet 
* Retrieve Image Result In Uri Format
* Crop Image
* Rotate Image
* Image Zoom In, Zoom Out
* Customize Image Picker BottomSheet Options Like :
     - Customize only text of buttons
     - Customize only text color of buttons
     - Customize multiple values of buttons like:
          - Text color, size, font family, padding using your own styles.xml
     - Customize bottomsheet's background shape and color


# 🎬Preview

| Capture Image Using Camera | Pick Image From Gallery | Customize Bottomsheet |
|--|--|--|
| ![](Camera.gif) | ![](Gallery.gif) | ![](cutomize_bottomsheet.gif) |

| Crop Image | Rotate Image | Image Zoom in, Zoom out |
|--|--|--|
| ![](crop_image.gif) | ![](Rotate.gif) | ![](Zoom%20in%20Zoom%20Out.gif)

# How it works:

1. Gradle Dependency

- Add the JitPack repository to your project's build.gradle file

```
    allprojects {
    		repositories {
    			...
    			maven { url 'https://jitpack.io' }
    		}
    	}
```
- Add the dependency in your app's build.gradle file

```
    dependencies {
    	        implementation 'com.github.SimformSolutionsPvtLtd:SSImagePicker:-SNAPSHOT'
    	}
```
2. Use ImagePicker Bottomsheet To Choose Option For Pick Image From Gallery Or Camera

```
    val fragment = ImagePickerBottomsheet()
    fragment.show(FragmentManager, String) 
```
3. Allow Camera And Storage Permission To Pick Image And Send Your onRequestPermissionsResult To ImagePickerActivity

```
    override fun onRequestPermissionsResult(requestCode: Int, permissions: Array<out String>, grantResults: IntArray) 
    {
         imagePicker.onRequestPermissionsResult(requestCode, permissions, grantResults)
    }
```

4. Call ImagePickerActivityClass To Handle Camera, Gallery Click And Permission Result. Pass Context, Activity And Request Permission Result Callback:

```
    var imagePicker = ImagePickerActivityClass(Context,Activity,onResult_Callback)
```
5. To Capture Image From Camera Use takePhotoFromCamera()

```
    imagePicker.takePhotoFromCamera()
```
6. To Pick Image From Gallery Use choosePhotoFromGallary()

```
    imagePicker.choosePhotoFromGallary()
```

7. You Will Get Image Result In Uri Format In returnString() And Customize It To Upload 

```
     override fun returnString(item: Uri?) {
            **Here You Will Get Your Image Result In Uri Format**
        }
```
# To customize bottomsheet:
* To customize bottomsheet, first override below method in your activity.
```
     override fun doCustomisations(fragment: ImagePickerBottomsheet) {
         Do customizations here...
     }
```
* To customize text of buttons in Bottomsheet.
```
     fragment.setButtonText("Select Camera","Select Gallery","Remove")
```
* To only change text color of buttons in Bottomsheet.
```
     fragment.setButtonColors(ContextCompat.getColor(requireContext(), R.color.colorPrimary))
```
* To customize multiple values of buttons (Text color, size, font family, padding), you need to create a style in your style.xml.
```
     fragment.setTextAppearance(R.style.fontForNotificationLandingPage)
```
In styles.xml (Note: parent must be "Widget.AppCompat.TextView")
```
     <style name="fontForNotificationLandingPage" parent="Widget.AppCompat.TextView">
         <item name="android:fontFamily">@font/poppins_medium</item>
         <item name="android:textColor">@color/white</item>
         <item name="android:textSize">@dimen/_18ssp</item>
     </style>
```
Note: if setTextAppearance and setButtonColors both are used than whichever function is last called will override other one.
* To change bottomsheet's background (shape, color).
```
     fragment.setBottomSheetBackgroundStyle(R.drawable.drawable_bottom_sheet_dialog)
```
You need to make one drawable file of type shape.
```
     <shape xmlns:android="http://schemas.android.com/apk/res/android"
         android:shape="rectangle">
         <corners
             android:topLeftRadius="@dimen/_25sdp"
             android:topRightRadius="@dimen/_25sdp" />
         <padding android:top="@dimen/_5sdp" />
         <solid android:color="@color/colorPrimary" />
     </shape>
```
# Other Library used:
* __[UCrop Library](https://github.com/Yalantis/uCrop)__

## Find this library useful? :heart:
Support it by joining __[stargazers](https://github.com/SimformSolutionsPvtLtd/SSImagePicker/stargazers)__ for this repository. :star:

## License

```
Copyright 2020 Simform Solutions

 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
    http://www.apache.org/licenses/LICENSE-2.0
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and limitations under the License.
```