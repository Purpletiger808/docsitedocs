---
mdx.format: md
---

# What Is Linear Referencing?

Linear referencing is the method to store and geographically locate data using relative positions along a measured line feature without the need to explicitly use x,y coordinates or an address.


<img src="https://pro.arcgis.com/en/pro-app/latest/help/data/linear-referencing/GUID-AFF5EF8F-855D-4A7B-9D4F-D5E3001DD012-web.gif" Alt="Description of the image" Width="300">

When data is linearly referenced, measure values are used to measure the distance along a line feature, allowing multiple sets of dynamically changing attribute data to be associated with any portion of an existing linear feature, independent of its beginning and end. Measurements along features are used to locate point events and line events using several conventions.

Below are some common examples illustrated in the following image:

<img src="https://pro.arcgis.com/en/pro-app/latest/help/data/linear-referencing/GUID-AFF5EF8F-855D-4A7B-9D4F-D5E3001DD012-web.gif" Alt="Description of the image" Width="300" />

A point event feature can be located along the line:
<div class="stupidlistthing">

- At measure 12 along the line.
- 4 units east of measure marker 10 along the line.

A line event feature can be referenced along the line where:

- The line starts at measurement 18 and ends at 26.
- The line starts at measurement 28 and continues for 12 units. 
</div>

## Why use linear referencing?

Linear referencing is used for many reasons. The following are the two primary reasons:
Many locations are recorded as events along linear features. For example, locations of traffic accidents are recorded using a convention such as "27 meters east of reference mile marker 35 along State Highway 287." Many sensors record conditions using measures of distance or time along the lines—along pipelines, along roads, along streams, and so forth. Linear referencing is also used to associate multiple sets of attributes to portions of linear features without requiring that underlying lines be segmented (split) each time that attribute values change. For example, most road centerline feature classes are segmented where three or more road segments intersect and where the road names change. Users often want to record many additional attributes about the roads. Without the use of linear referencing, this could require that roads be split into many tiny segments at each location where attribute values change. As an alternative, these situations can be handled as linear referencing events along the roads, as in the figure below. 


<img src="https://pro.arcgis.com/en/pro-app/latest/help/data/linear-referencing/GUID-1E88CD49-ECDC-4315-8E78-BD57B4FC1218-web.png" Alt="Description of the image" Width="300" />

## What is dynamic segmentation?

Dynamic segmentation is the process of computing the map locations of events stored and managed in an event table and displaying them on a map using route features. The term dynamic segmentation is derived from the concept that line features need not be split (in other words, segmented) each time an attribute value changes; you can dynamically locate the segment.
Using dynamic segmentation, multiple sets of attributes can be associated with any portion of an existing linear feature independently of where it begins or ends. These attributes can be displayed, queried, edited, and analyzed without affecting the underlying linear feature's geometry.

## Video Example

<iframe src="https://www.youtube.com/embed/fEdRIYyqPao?si=j__tvMHnEOjAfFmL"
        title="YouTube video player"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
        referrerpolicy="strict-origin-when-cross-origin"
        allowfullscreen>
</iframe>