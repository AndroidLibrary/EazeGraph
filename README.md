EazeGraph
=========

EazeGraph is an Android library for creating beautiful and fancy charts. Its main goal was to create a lighweight library which is easy to use and highly customizeable with an "up-to-date"-look.

Currently 4 different chart types are available, which can be viewed below.

__________
<b>IMPORTANT:</b>

This library is not intented for "mathematical" purposes like "achartengine" or "androidplot". It is intented to have a beautiful visual presentation of "user related"-data where only one value is provided and the rest is calculated dynamically.

So for example it's not possible to push 2D-values in the LineChart and let them plot just like in our beloved math lessons.

If you want such functionality either you use one of the libraries I named before or you wait some time until I finished a "mathematical plotting"-chart ;)

Currently BarCharts only support positive values. I will provide this functionality later.

<b>Your Android application should at least use Android API Level 14 in order to use this library!!!</b>

Chart types
===========

- Bar Chart

<img src="https://raw.github.com/blackfizz/EazeGraph/master/imagery/bar_chart.png" width="400px" height="300px" />


- Stacked Bar Chart

<img src="https://raw.github.com/blackfizz/EazeGraph/master/imagery/stacked_bar_chart.png" width="450px" height="300px" />

- Pie Chart

<img src="https://raw.github.com/blackfizz/EazeGraph/master/imagery/pie_chart.png" width="400px" height="420px" >


- Line Chart

<img src="https://raw.github.com/blackfizz/EazeGraph/master/imagery/line_chart.png" width="600px" height="320px" />
<img src="https://raw.github.com/blackfizz/EazeGraph/master/imagery/cubic_line_chart.png" width="600px" height="320px" />


Features
========

- 4 different chart types
- dynamic legend label generation
- possibility to use your own legend labels 
- animations for every chart
- touch interaction for PieChart and LineChart
- various xml attributes for customizing the charts
- and much more


Examples
========

Examples on how to correctly use these charts are either below or you can view the source of the sample app I provided.


Including in your project
=========================

Insert in your root project's 'build.gradle' under repositories:

    repositories {
        maven {
            url 'https://oss.sonatype.org/content/groups/public'
        }
    }

and in your android app project folder in the 'build.gradle' under dependencies:

    dependencies {
        compile 'com.github.blackfizz:eazegraph:1.0.10-SNAPSHOT@aar'
    }

That's it. now you are ready to use the library!

Usage
=====

### Bar Chart

##### XML

    <org.eazegraph.lib.charts.BarChart
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:id="@+id/barchart"
        android:layout_width="match_parent"
        android:layout_height="256dp"
        android:padding="10dp"
        app:egFixedBarWidth="true"
        app:egBarWidth="20dp"
        app:egLegendHeight="40dp"/>

##### Java

    BarChart mBarChart = (BarChart) findViewById(R.id.barchart);
    
    mBarChart.addBar(new BarModel(2.3f, 0xFF123456));
    mBarChart.addBar(new BarModel(2.f,  0xFF343456));
    mBarChart.addBar(new BarModel(3.3f, 0xFF563456));
    mBarChart.addBar(new BarModel(1.1f, 0xFF873F56));
    mBarChart.addBar(new BarModel(2.7f, 0xFF56B7F1));
    mBarChart.addBar(new BarModel(2.f,  0xFF343456));
    mBarChart.addBar(new BarModel(0.4f, 0xFF1FF4AC));
    mBarChart.addBar(new BarModel(4.f,  0xFF1BA4E6));
    
    mBarChart.startAnimation();

__________
### Stacked Bar Chart
 
##### XML

    <org.eazegraph.lib.charts.StackedBarChart
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:id="@+id/stackedbarchart"
        android:layout_width="match_parent"
        android:layout_height="256dp"
        android:padding="10dp"
        app:egFixedBarWidth="true"
        app:egBarWidth="20dp"
        app:egLegendHeight="40dp"/>

##### Java

    StackedBarChart mStackedBarChart = (StackedBarChart) findViewById(R.id.stackedbarchart);

    StackedBarModel s1 = new StackedBarModel("12.4");

    s1.addBar(new BarModel(2.3f, 0xFF63CBB0));
    s1.addBar(new BarModel(2.3f, 0xFF56B7F1));
    s1.addBar(new BarModel(2.3f, 0xFFCDA67F));

    StackedBarModel s2 = new StackedBarModel("13.4");
    s2.addBar(new BarModel(1.1f, 0xFF63CBB0));
    s2.addBar(new BarModel(2.7f, 0xFF56B7F1));
    s2.addBar(new BarModel(0.7f, 0xFFCDA67F));

    StackedBarModel s3 = new StackedBarModel("14.4");

    s3.addBar(new BarModel(2.3f, 0xFF63CBB0));
    s3.addBar(new BarModel(2.f, 0xFF56B7F1));
    s3.addBar(new BarModel(3.3f, 0xFFCDA67F));

    StackedBarModel s4 = new StackedBarModel("15.4");
    s4.addBar(new BarModel(1.f, 0xFF63CBB0));
    s4.addBar(new BarModel(4.2f, 0xFF56B7F1));
    s4.addBar(new BarModel(2.1f, 0xFFCDA67F));

    mStackedBarChart.addBar(s1);
    mStackedBarChart.addBar(s2);
    mStackedBarChart.addBar(s3);
    mStackedBarChart.addBar(s4);

    mStackedBarChart.startAnimation();

__________
### PieChart
 
##### XML

     <org.eazegraph.lib.charts.PieChart
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:id="@+id/piechart"
        android:layout_width="match_parent"
        android:layout_height="300dp"
        android:padding="8dp"
        app:egLegendTextSize="18sp"
        app:egUsePieRotation="true"
        app:egValueTextSize="36sp"/>


##### Java

    PieChart mPieChart = (PieChart) findViewById(R.id.piechart);
    
    mPieChart.addPieSlice(new PieModel("Freetime", 15, Color.parseColor("#FE6DA8")));
    mPieChart.addPieSlice(new PieModel("Sleep", 25, Color.parseColor("#56B7F1")));
    mPieChart.addPieSlice(new PieModel("Work", 35, Color.parseColor("#CDA67F")));
    mPieChart.addPieSlice(new PieModel("Eating", 9, Color.parseColor("#FED70E")));
    
    mPieChart.startAnimation();

__________
### Line Chart 
 
##### XML

    <org.eazegraph.lib.charts.ValueLineChart
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:id="@+id/cubiclinechart"
        android:layout_width="match_parent"
        android:layout_height="200dp"
        app:egUseCubic="true"
        app:egUseOverlapFill="true"
        app:egCurveSmoothness="0.4"
        app:egIndicatorColor="#FE6DA8"
        app:egLegendHeight="40dp"
        app:egShowStandardValue="true"/>

##### Java

    ValueLineChart mCubicValueLineChart = (ValueLineChart) findViewById(R.id.cubiclinechart);
    
    ValueLineSeries series = new ValueLineSeries();
    series.setColor(0xFF56B7F1);

    series.addPoint(new ValueLinePoint("Jan", 2.4f));
    series.addPoint(new ValueLinePoint("Feb", 3.4f));
    series.addPoint(new ValueLinePoint("Mar", .4f));
    series.addPoint(new ValueLinePoint("Apr", 1.2f));
    series.addPoint(new ValueLinePoint("Mai", 2.6f));
    series.addPoint(new ValueLinePoint("Jun", 1.0f));
    series.addPoint(new ValueLinePoint("Jul", 3.5f));
    series.addPoint(new ValueLinePoint("Aug", 2.4f));
    series.addPoint(new ValueLinePoint("Sep", 2.4f));
    series.addPoint(new ValueLinePoint("Oct", 3.4f));
    series.addPoint(new ValueLinePoint("Nov", .4f));
    series.addPoint(new ValueLinePoint("Dec", 1.3f));
    
    mCubicValueLineChart.addSeries(series);
    mCubicValueLineChart.startAnimation();

Wiki
====

[Project Wiki][10]

Changelog
=========
**1.0.10**
* fixed bug in PieChart's current item calculation and autocenter

**1.0.9**
* fixed bug in BarCharts, when layout size changed and the chart tried to calculate positions for empty elements.

**1.0.8**
* LineChart's value will now set its position the the left of the indicator, if it doesn't fit on the screen
* fixed bug where the LineChart GraphOverlay wasn't updated when new values are imported 

**1.0.7**
* the opening animation can now be opened clockwise or counterclockwise (use attribute "egOpenClockwise"

**1.0.6**
* added possibility to use a custom set inner value in PieChart

**1.0.5**
* added x-axis for Line Charts
* Line Charts now support negative values

**1.0.4**
* added standard value for line chart and the corresponding XML-attributes
* fixed some calculation bugs which caused some displaying errors when a lot of data is inserted
* added clearing methods for Charts
* fixed the legend calculation function

**1.0.1**
* added 'eg' namespace for attributes

**1.0.0**
* initial commit of this library

Contributing
=============

I would love to see people contributing to this project. So just go ahead. If you think you did something amazing and your feature should be implemented in this library, make a pull request! Do not hesitate.

Credit
======

This library was developed for the official YAZIO Android app:

https://play.google.com/store/apps/details?id=com.yazio.android

https://play.google.com/store/apps/details?id=com.yazio.android.pro

License
=======

    Copyright (C) 2014 Paul Cech

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at
 
    http://www.apache.org/licenses/LICENSE-2.0
 
    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.

[5]: https://raw.github.com/blackfizz/EazeGraph/master/imagery/bar_chart.png
[6]: https://raw.github.com/blackfizz/EazeGraph/master/imagery/stacked_bar_chart.png
[7]: https://raw.github.com/blackfizz/EazeGraph/master/imagery/pie_chart.png
[8]: https://raw.github.com/blackfizz/EazeGraph/master/imagery/line_chart.png
[9]: https://raw.github.com/blackfizz/EazeGraph/master/imagery/cubic_line_chart.png
[10]: https://github.com/blackfizz/EazeGraph/wiki
