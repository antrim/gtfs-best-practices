---
layout: best-practices
permalink: /best-practices/stop-times/

table_data:
  pickup_type:
    1: "Non-revenue (deadhead) trips that do not provide passenger service should be marked with <code>pickup_type</code> and <code>drop_off_type</code> value of <code>1</code> for all <code>stop_times</code> rows.<!-- (13) -->"
    2: "On revenue trips, internal “timing points” for monitoring operational performance and other places such as garages that a passenger cannot board should be marked with <code>pickup_type = 1</code> (no pickup available) and <code>drop_off_type = 1</code> (no drop off available). <!-- (46) -->"
  drop_off_type:
    7: "See <code>pickup_type</code> (above)"
  timepoint:
    3: "The <code>timepoint</code> field should be provided. It specifies which <code>stop_times</code> the operator will attempt to strictly adhere to (<code>timepoint=1</code>), and that other stop times are estimates (<code>timepoint=0</code>).<!-- (44) -->"
  arrival_time:
    4: "<code>arrival_time</code> and <code>departure_time</code> fields should specify time values whenever possible, including non-binding estimated or interpolated times between timepoints. <!-- (45) -->"
  departure_time:
    8: "See <code>arrival_time</code> (above)"
  stop_headsign:
    5: "<code>stop_headsign</code> values override the <code>trip_headsign</code> (in <code>trips.txt</code>). <code>stop_headsign</code> values should be provided when the text displayed on the headsign changes during a trip. <code>stop_headsign</code> values do not 'carry down' to subsequent stops, and therefore values must be repeated if the stop headsign remains the same. In general, headsign values should also correspond to signs in the stations. <!-- (47) -->
    Examples:
    <table class='example'>
      <thead>
        <tr>
          <th colspan='2'>In NYC, for the 2 going Southbound:</th>
        </tr>
        <tr>
          <th>For <code>stop_times.txt</code> rows:</th>
          <th>Use <code>stop_headsign</code> value: </th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Until Manhattan is Reached</td>
          <td><code>Manhattan & Brooklyn</code></td>
        </tr>
        <tr>
          <td>Until Downtown is Reached</td>
          <td><code>Downtown & Brooklyn</code></td>
        </tr>
        <tr>
          <td>Until Brooklyn is Reached</td>
          <td><code>Brooklyn</code></td>
        </tr>
        <tr>
          <td>Once Brooklyn is Reached</td>
          <td><code>Brooklyn (New Lots Av)</code></td>
        </tr>
      </tbody>
    </table>

    <table class='example'>
      <thead>
        <tr>
          <th colspan='2'>In Boston, for the Red Line going Southbound, for the Braintree branch:</th>
        </tr>
        <tr>
          <th>For <code>stop_times.txt</code> rows:</th>
          <th>Use this <code>stop_headsign</code> Value: </th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Until Downtown is Reached</td>
          <td><code>Inbound to Braintree</code></td>
        </tr>
        <tr>
          <td>Once Downtown is Reached</td>
          <td><code>Braintree</code></td>
        </tr>
        <tr>
          <td>After Downtown</td>
          <td><code>Outbound to Braintree</code></td>
        </tr>
      </tbody>
    </table>
    In the above two cases, “Southbound” would mislead customers because it is not used in the station signs."
  shape_dist_traveled:
    6: "<code>shape_dist_traveled</code> must be provided for routes that have looping or inlining (the vehicle crosses or travels over the same portion of alignment in one trip). See <a href='/best-practices/shapes/#shapes_3'><code>shapes.shape_dist_traveled</code></a> recommendation.<!-- (48) -->"


---

## stop_times.txt

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
        <tr id="stop_times_{{ recommendation[0] }}" class="anchor-row">
          <td>{% if forloop.first == true %}<code>{{ field_name[0] }}</code>{% endif %}</td>
          <td>{{ recommendation[0] }}</td>
          <td>{{ recommendation[1] }}</td>
        </tr>
      {% endfor %}
    {% endfor %}
  </tbody>
</table>

Loop routes: Loop routes require special `stop_times` considerations. (See: [Loop route case](/best-practices/loop-routes))
