---
title: "HS23 score table"
layout: page
menu: HS23 score table
datatable: true
---

# HS23 score table

{% assign table_rows = site.data.HS23scores %}

Data displayed in the following table are available in csv format in the github repository of [HEPiX-Forum](https://github.com/HEPiX-Forum/hepix-forum.github.io/blob/master/_data/HS23scores.csv)


Starting with **HEP Benchmark Suite version 3**, sites can enrich benchmark results by including **electric power consumption** measurements collected during the benchmark execution.  
For details on how to enable this, see the [official script documentation](https://w3.hepix.org/benchmarking/how_to_run_HS23.html).

Power consumption is measured using the command: `ipmitool dcmi power reading`

<div class="update-banner update-banner--new" role="note">
  <p class="update-banner__label"><span class="update-banner__badge">New</span> Interactive plot</p>
  <p class="update-banner__message">For an interactive view of the power-related metrics, see the
  <a href="{{ "/benchmarking/time_energy_to_solution.html" | relative_url }}">Time and Energy to Solution</a>
  page.</p>
</div>

**Important note:**  
The values reported by `ipmitool` may differ from those obtained via Power Distribution Units (PDUs).  
Accuracy depends on the server’s hardware and firmware implementation. Therefore, these results should be considered **experimental and approximate**.

<details class="metrics-toggle">
<summary>Metrics description</summary>

<p>Benchmark result tables include several metrics. Only those that are <strong>not immediately self-explanatory</strong> are described below:</p>

<ul>
  <li><strong><code># Meas</code></strong>: The number of independent benchmark measurements performed.</li>
  <li><strong><code>Score/Ncores</code></strong>: The performance score normalized by the number of available cores (physical or logical).</li>
  <li><strong><code>sem</code></strong> (Standard Error of the Mean): A measure of the statistical uncertainty of the score, calculated from multiple runs.</li>
  <li><strong><code>Spread</code></strong>: A measure of variability across the benchmark runs, calculated as the relative difference between the 95th and 5th percentiles, normalized by the median.</li>
  <li><strong><code>Average Electric Power [W]</code></strong>, <strong><code>Std Electric Power [W]</code></strong>: For each measurement time series collected during the benchmark run, the <strong>85th percentile</strong> is determined. Mean and std are then evaluated across all measurement series.</li>
  <li><strong><code>HS23/W</code></strong> = Score / <code>Average Electric Power [W]</code></li>
  <li><strong><code>W/HS23</code></strong>: Watt per unit score (an energy-to-solution proxy).</li>
  <li><strong><code>Relative Time To Solution</code></strong>, <strong><code>Relative Energy To Solution</code></strong>: time-to-solution and energy-to-solution proxies, each normalized to the fastest power-reporting configuration. These drive the interactive <a href="{{ "/benchmarking/time_energy_to_solution.html" | relative_url }}">Time and Energy to Solution</a> plot.</li>
</ul>

</details>


 
<br>
<br>
<div class="datatable-container">
  <table id="myTable" class="display" style="width:100%;">
      {% for row in table_rows %}
          {% if forloop.first %}
              <thead>
              <tr>
                  {% for pair in row %}
                      <th>
                          {{ pair[0] }}
                      </th>
                  {% endfor %}
              </tr>
              </thead>
          {% endif %}
          {% tablerow pair in row %}
              {{ pair[1] }}
          {% endtablerow %}
      {% endfor %}
  </table>
</div>

