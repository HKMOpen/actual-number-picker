Actual Number Picker
====================
[![Android Weekly](https://img.shields.io/badge/Android%20Weekly-185-blue.svg)](http://androidweekly.net/issues/issue-185)
[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-Actual%20Number%20Picker-brightgreen.svg?style=flat)](http://android-arsenal.com/details/1/3415)

What is this?
-------------
Actual Number Picker is an Android custom-built View for choosing numbers. 
It's simple, elegant, fits in a small-height constraint box and it can be completely customized in XML.
You can easily swipe it right and left, or click on arrow controls to increase/decrease the current value.

Requirements
------------
- Android 3.0 or later (Minimum SDK level 11)
- Android Studio (to compile and use)
- **Eclipse is not supported**

Getting Started
---------------
1. [Download Android Studio](http://developer.android.com/sdk/index.html)
1. Launch Android Studio
1. Start your new project
1. Open your project's main Gradle file, in root directory (**/build.gradle**)
1. Make sure you are using **jcenter()** in the repository block (**mavenCentral()** should work too)
1. Open your app module Gradle file, for example **/app/build.gradle**
1. In **dependencies** block, add the following line: `compile 'me.angrybyte.picker:picker:1.2.0'`
1. Click **Tools/Android/Sync Project with Gradle Files** or click on the *Sync* icon in the top toolbar
1. Click **Run/Run 'app'** to see if it's resolved correctly

This will run the app on your device. You may need to download a newer version of Gradle, which will be available in the Android Studio UI if compile fails.

What does it look like?
----------------------
![scene_shot_2](https://raw.githubusercontent.com/milosmns/actual-number-picker/master/assets/Imagery_3.png)
A Lollipop-inspired look

![screenshot_4](https://raw.githubusercontent.com/milosmns/actual-number-picker/master/assets/Imagery_4.png)
Various configuration options (v1)

![screenshot_5](https://raw.githubusercontent.com/milosmns/actual-number-picker/master/assets/Imagery_5.png)
Various configuration options (v2)

Sample usage
------------
First, define the View in your layout file (of course, you don't need to add all the `app` attributes, I just added them for demo).

```xml
<me.angrybyte.numberpicker.view.ActualNumberPicker
    android:id="@+id/actual_picker"
    android:layout_width="wrap_content"
    android:layout_height="48dp"
    android:layout_centerHorizontal="true"
    android:layout_marginTop="25dp"
    android:background="#FFFF3040"
    app:anp_bar_color="@android:color/white"
    app:anp_bar_width="1dp"
    app:anp_bars_count="26"
    app:anp_controls_color="@android:color/white"
    app:anp_draw_over_controls="true"
    app:anp_draw_over_text="false"
    app:anp_fast_controls_color="@android:color/darker_gray"
    app:anp_highlight_color="#FFFF3040"
    app:anp_max_value="100"
    app:anp_min_value="0"
    app:anp_selection_color="#A0FF3040"
    app:anp_show_bars="true"
    app:anp_show_controls="true"
    app:anp_show_fast_controls="true"
    app:anp_show_highlight="true"
    app:anp_show_text="false"
    app:anp_text_color="@android:color/white"
    app:anp_text_size="16sp"
    app:anp_value="50" />
```

Then, from Java (your Activity or Fragment), you can easily get the view and attach the listener.
```java
public class DemoActivity extends AppCompatActivity implements OnValueChangeListener {

    private static final String TAG = DemoActivity.class.getSimpleName();

    private ActualNumberPicker mPicker;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_demo);
        mPicker = (ActualNumberPicker) findViewById(R.id.actual_picker);
        mPicker.setListener(this);
    }

    @Override
    public void onValueChanged(int oldValue, int newValue) {
        float percent = (float) newValue / (float) (mPicker.getMaxValue() - mPicker.getMinValue());
        Log.d(TAG, "Currently the picker is at " + percent + " percent.");
    }

}
```
**Note**: `onValueChanged()` event will always get fired on the UI thread.

Explanation of attributes
-------------------------
Here are some short explanations for the attributes provided by the view. You can leave out any of them, values will get set to default ones.

- `anp_show_bars`: (**boolean**) Whether show the vertical lines or not.
- `anp_bars_count`: (**integer**) How many bars to show. Note that the number may be changed by 1 if symmetry issues occur (*ignored if bars are not visible*).
- `anp_bar_color`: (**color**) Recolors all of the vertical lines to the specified color (*ignored if bars are not visible*).
- `anp_bar_width`: (**dimension**) How wide should each bar be (*ignored if bars are not visible*).
- `anp_draw_over_text`: (**boolean**) Whether to show the bars over the text (*ignored if text or bars are not visible*).
- `anp_draw_over_controls`: (**boolean**) Whether to show the bars over the arrow controls (*ignored if controls or bars are not visible*).

- `anp_selection_color`: (**color**) The touch highlight color on each of the arrow controls (*ignored if controls are not visible*).

- `anp_show_highlight`: (**boolean**) Whether to show the blurry highlight behind each of the arrow controls (*ignored if controls are not visible*).
- `anp_highlight_color`: (**color**) Recolors the blurry highlight to the specified color (*ignored if controls or highlights are not visible*).

- `anp_show_controls`: (**boolean**) Whether to show the slow arrow controls or not.
- `anp_controls_color`: (**color**) Recolors all of the slow arrows to the specified color (*ignored if slow arrows are not visible*).

- `anp_show_fast_controls`: (**boolean**) Whether to show the fast arrow controls or not.
- `anp_fast_controls_color`: (**color**) Recolors all of the fast arrows to the specified color (*ignored if fast arrows are not visible*).

- `anp_show_text`: (**boolean**) Whether to show the text with the current number value or not.
- `anp_text_size`: (**dimension**) Set the current number value text size (*ignored if text is not shown*).
- `anp_text_color`: (**color**) Recolors the current number value text to the specified color (*ignored if text is not shown*).

- `anp_min_value`: (**integer**) How low can the value numbers go.
- `anp_max_value`: (**integer**) How high can the value numbers go.
- `anp_value`: (**integer**) Set the current value (*must be between `min_value` and `max_value`*).

Support
-------
If you've found an error while using the library, please [file an issue](https://github.com/milosmns/actual-number-picker/issues/new).
All patches are encouraged, and may be submitted by [forking this project](https://github.com/milosmns/actual-number-picker/fork) and
submitting a pull request through GitHub.
Some more help can be found here:
- [Stack Overflow](http://stackoverflow.com/questions/tagged/actual-number-picker)
- [On my blog](http://angrybyte.me)
