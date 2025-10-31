---
mdx.format: md
---

# Creating Road Intersections in GIS

Step-by-step procedure for generating and refining intersection data

<dl >
    <dt>Calculate Intersection Geometry</dt>
    <dd>Utilize highway class segments to compute intersection points for each line segment. This step generates multiple points.</dd>
    <dt>Save Initial Intersection File</dt>
    <dd>Make a duplicate of this file for backup purposes.</dd>
    <dt>Remove Duplicate Intersection Points</dt>
    <dd>Ensure each intersection geometry retains only one unique point by deleting duplicate points.</dd>
    <dt>Merge with Historical Data</dt>
    <dd>Integrate data from previous years, such as intersection keys, with single intersection points. This step helps identify and categorize false intersections.</dd>
    <dt>Manual Review of Unmatched Intersections</dt>
    <dd>Identify and manually review intersecions without matches to historical data. Use feature type codes and road types to validate if the intersection is genuine.</dd>
    <blockquote>
    <dd><strong>Example</strong>: Feature type code "C" for an off-ramp suggests an exit rather than a true intersection.</dd>
    <dd><strong>Example</strong>: Feature type code "X" for a crossover indicates a divided roadway, not a true intersection.</dd>
    </blockquote>
    <dt>Filter Out False Intersections</dt>
    <dd>Exclude false intersections identified in past analyses, such as overpasses or intersections with differing Z values (elevations).</dd>
    <dt>Verify Data Integrity</dt>
    <dd>Valiate data integrity by filtering and visually inspecting potential false intersections, especially along interstate and state highways.</dd>
    <dt>Final Data Cleanup and Attribute Integration</dt>
    <dd>Once single-point intersection data is cleaned and relevant attributes are integrated, proceed to merge this data with multipoint data using a key field. This establishes a many-to-one relationship where multipoint data encapsulates all relevant row data. </dd>
</dl>