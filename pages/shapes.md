---
layout: best-practices
permalink: /best-practices/shapes/


table_data:
  All Fields:
    1: "Ideally, for alignments that are shared (i.e. in a case where Routes 1 and 2 operate on the same segment of roadway or track) then the shared portion of alignment should match exactly. This helps to facilitate high-quality transit cartography. <!-- (77) -->"
    2: "Alignments should follow the centerline of the right of way on which the vehicle travels. This could be either the centerline of the street if there are no designated lanes, or the centerline of the side of the roadway that travels in the direction the vehicle moves. <!-- (78) -->"
  shape_dist_traveled:
    3: "Must be provided in both <code>shapes.txt</code> and <code>stop_times.txt</code> if an alignment includes looping or inlining (the vehicle crosses or travels over the same portion of alignment in one trip). <!-- (79) -->
      <figure id='inlining-fig'>
        <img src='/best-practices/images/inlining.svg' alt='An Inlining Route'>
        <figcaption>If a vehicle retraces or crosses the route alignment at points in the course of a trip, <code>shape_dist_traveled</code> is important to clarify how portions of the points in <code>shapes.txt</code> line up correspond with records in <code>stop_times.txt</code>.</figcaption>
      </figure>"
    4: "The <code>shape_dist_traveled</code> field allows the agency to specify exactly how the stops in the <code>stop_times.txt</code> file fit into their respective shape. A common value to use for the <code>shape_dist_traveled</code> field is the distance from the beginning of the shape as traveled by the vehicle (think something like an odometer reading).

      <ul>
        <li>Route alignments (in <code>shapes.txt</code>) should be within 100 meters of stop locations which a trip serves.  <!-- (80) --></li>
        <li>Simplify alignments so that <code>shapes.txt</code> does not contain extraneous points (i.e. remove extra points on straight-line segments; see discussion of line simplification problem). <!-- (81) --></li>
      </ul>"
---

## shapes.txt (alignments)

<table class="recommendation">
  <thead>
    <tr>
      <th>Field Name</th>
      <th>ID</th>
      <th>Recommendation</th>
    </tr>
  </thead>
  <tbody>
    {% for field_name in page.table_data %}
      {% for recommendation in field_name[1] %}
        <tr id="shapes_{{ recommendation[0] }}" class="anchor-row">
          <td>{% if forloop.first == true %}<code>{{ field_name[0] }}</code>{% endif %}</td>
          <td>{{ recommendation[0] }}</td>
          <td>{{ recommendation[1] }}</td>
        </tr>
      {% endfor %}
    {% endfor %}
  </tbody>
</table>
