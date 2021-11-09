---
layout: post
title: Column Chart in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about column chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Column Chart in Flutter Cartesian Charts (SfCartesianChart)

To render a column chart, create an instance of [`ColumnSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/XyDataSeries-class.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html). The following properties can be used to customize the appearance:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) - changes the color of the series.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) - changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) - changes the stroke color of the series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            // Renders column chart
                            ColumnSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )      
            )
        );
    }

{% endhighlight %}

![Column chart](cartesian-chart-types-images/column.jpg)

## Side-by-side series placement

By default, all the column series that have the same x and y-axes are placed side by side in a chart. If you want to place a series one over the other (overlapped), set the [`enableSideBySideSeriesPlacement`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/enableSideBySideSeriesPlacement.html) property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/SfCartesianChart.html) to false and configure the [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) property to differentiate the series. The following code snippet and screenshot illustrate the overlapped placement of column series.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        final List<SalesData> chartData = [
            SalesData(2010, 35, 23),
            SalesData(2011, 38, 49),
            SalesData(2012, 34, 12),
            SalesData(2013, 52, 33),
            SalesData(2014, 40, 30)
        ];
        
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: DateTimeAxis(),
                        // Columns will be rendered back to back
                        enableSideBySideSeriesPlacement: false,
                        series: <ChartSeries>[
                            ColumnSeries<SalesData, DateTime>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            ),
                            ColumnSeries<SalesData, DateTime>(
                                opacity: 0.9,
                                width: 0.4,
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.loss
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Column side by side placement](cartesian-chart-types-images/sidebySidePlacement.jpg)

## Column width and spacing

The [`spacing`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/spacing.html) property is used to change the spacing between two segments. The default value of spacing is 0, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available space, respectively.

The [`width`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/width.html) property is used to change the width of the rectangle. The default value of the width is 0.7, and the value ranges from 0 to 1. Here, 1 and 0 correspond to 100% and 0% of the available width, respectively.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            ColumnSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales,
                                width: 0.8, // Width of the columns
                                spacing: 0.2 // Spacing between the columns
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Column width and spacing](cartesian-chart-types-images/column_width_spacing.jpg)

## Rounded corners

The [`borderRadius`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/borderRadius.html) property is used to add the rounded corners to the rectangle.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            ColumnSeries<SalesData, double>(
                                dataSource: chartData,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales,
                                // Sets the corner radius
                                borderRadius: BorderRadius.all(Radius.circular(15))
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Rounded corners](cartesian-chart-types-images/rounded_column.jpg)

### See Also

* [Rendering each data points with different border radius in column charts](https://www.syncfusion.com/kb/12074/how-to-set-different-border-radius-for-each-rect-series-data-points-by-extending-the).

* [Adding rounded corners for the specific sides in column charts](https://www.syncfusion.com/kb/12059/how-to-add-rounded-corners-for-specific-sides-in-the-rect-series-types-sfcartesianchart)

## Track customization

Renders column with track. Track is a rectangular bar rendered from the start to the end of the axis. Column series will be rendered above the track. The [`isTrackVisible`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/isTrackVisible.html) property is used to enable the track. The following properties can be used to customize the appearance:

* [`trackColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/trackColor.html) - changes the color of the track.
* [`trackBorderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/trackBorderWidth.html) - changes the stroke width of the track.
* [`trackBorderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/trackBorderColor.html) - changes the stroke color of the track.
* [`trackPadding`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/ColumnSeries/trackPadding.html) - adds padding to the track.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        series: <ChartSeries>[
                            ColumnSeries<SalesData, double>(
                                dataSource: chartData,
                                // Renders the track
                                isTrackVisible: true,
                                xValueMapper: (SalesData sales, _) => sales.year,
                                yValueMapper: (SalesData sales, _) => sales.sales
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Track](cartesian-chart-types-images/track_column.jpg)

Also refer, [color palette](./series-customization#color-palette), [color mapping](./series-customization#color-mapping-for-data-points), [animation](./series-customization#animation), [gradient](./series-customization#gradient-fill) and [empty points](./series-customization#empty-points) for customizing the column series further.

N> You can refer to our [Flutter Column Chart](https://www.syncfusion.com/flutter-widgets/flutter-charts/chart-types/column-chart) feature tour page for its groundbreaking feature representations.