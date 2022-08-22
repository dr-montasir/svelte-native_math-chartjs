<script>
  import nm from 'native_math';

  import { Line, Bar, Radar } from 'svelte-chartjs';

  const ROTATION_MATRIX_2D = nm.range(0, 360, 15);

  // Color Manipulation
  const r = nm.rib(0, 204),
    g = nm.rib(0, 100),
    b = nm.rib(0, 240),
    o = nm.divi(nm.rib(1, 8), 10),
    randomColor = `rgb(${r}, ${g}, ${b}, ${o})`;

  // Adjust Point Radius
  const pointRadius = nm.rib(4, 11);

  // Chart Data
  let data = {
    labels: ROTATION_MATRIX_2D,
    datasets: [
      {
        label: '# The sin of 2D Rotation Matrix',
        data: nm.sin.deg(ROTATION_MATRIX_2D),
        backgroundColor: [randomColor],
        borderColor: ['rgba(27, 89, 161, 1)'],
        borderWidth: 2,
        pointRadius: `${pointRadius}`,
      },
    ],
  };
</script>

<h1>Svelte demo project using native math together with chartjs</h1>

<br />

<div class="chart">
  <h3>Radar Chart Example</h3>
  <div>
    <Radar
      {data}
      width={400}
      height={200}
      options={{
        maintainAspectRatio: false,
      }}
    />
  </div>
</div>

<br />

<div class="chart">
  <h3>Line Chart Example</h3>

  <div>
    <Line
      {data}
      width={400}
      height={200}
      options={{
        maintainAspectRatio: false,
      }}
    />
  </div>
</div>

<br />

<div class="chart">
  <h3>Bar Chart Example</h3>
  <div>
    <Bar
      {data}
      width={400}
      height={200}
      options={{
        maintainAspectRatio: false,
      }}
    />
  </div>
</div>

<br />

<div class="chart">
  <h3>Random Values</h3>
  <div
    style="background-color: {randomColor}; padding: 10px; text-align: center"
  >
    <p>
      <b>Color : {randomColor}</b>
    </p>
    <p>
      <b>Point Radius : {pointRadius} px</b>
    </p>
  </div>
</div>

<br />

<div class="chart">
  <h3>Data Table</h3>
  <div class="divTable blueTable" style="text-align: center; margin: 0 auto">
    <div class="divTableHeading">
      <div class="divTableRow">
        <div class="divTableHead">
          &nbsp;X=[sin<sup>−1</sup>(Y)]°
        </div>
        <div class="divTableHead">&nbsp;Y=sin(X°)</div>
      </div>
    </div>
    <div class="divTableBody">
      {#each ROTATION_MATRIX_2D as X}
        <div class="divTableRow">
          <div class="divTableCell">&nbsp;{X}</div>
          <div class="divTableCell">
            &nbsp;{nm.zeros(nm.sin.deg(X), 10)}
          </div>
        </div>
      {/each}
    </div>
  </div>
</div>

<div style="margin: 100px 50px;">
  <h3>Links:</h3>
  <ul>
    <li>
      <b>GitHub</b>:<br />
      <a
        href="https://github.com/dr-montasir/svelte-native_math-chartjs"
        target="_blank"
      >
        https://github.com/dr-montasir/svelte-native_math-chartjs
      </a>
    </li>

    <br />

    <li>
      <b>NATIVE MATH</b>:<br />
      <a href="https://www.npmjs.com/package/native_math" target="_blank">
        https://www.npmjs.com/package/native_math
      </a>
      <br />
      <a href="https://github.com/dr-montasir/native_math" target="_blank">
        https://github.com/dr-montasir/native_math
      </a>
    </li>

    <br />

    <li>
      <b>Chart.js</b>:<br />
      <a href="https://www.chartjs.org/" target="_blank">
        https://www.chartjs.org/
      </a>
      <br />
      <a href="https://www.npmjs.com/package/svelte-chartjs" target="_blank">
        https://www.npmjs.com/package/svelte-chartjs
      </a>
    </li>
  </ul>
</div>

<div style="text-align: center;">
  <div>{'_'.repeat(60)}</div>
  <br />
  <div>
    {#if new Date().getFullYear() === 2021}
      {new Date().getFullYear()}
    {:else}
      {2021} - {new Date().getFullYear()}
    {/if} All rights reserved @ https://github.com/dr-montasir
  </div>
  <div>{'_'.repeat(60)}</div>
  <br />
</div>

<style>
  h1 {
    text-align: center;
  }
  .chart {
    max-width: 800px;
    min-width: 400px;
    margin: 0 auto;
  }

  /* Data Table */
  div.blueTable {
    border: 1px solid #1c6ea4;
    background-color: #eeeeee;
    width: 100%;
    text-align: left;
    border-collapse: collapse;
  }
  .divTable.blueTable .divTableCell,
  .divTable.blueTable .divTableHead {
    border: 1px solid #aaaaaa;
    padding: 3px 2px;
  }
  .divTable.blueTable .divTableBody .divTableCell {
    font-size: 13px;
  }
  .divTable.blueTable .divTableRow:nth-child(even) {
    background: #d0e4f5;
  }
  .divTable.blueTable .divTableHeading {
    background: #1c6ea4;
    background: -moz-linear-gradient(
      top,
      #5592bb 0%,
      #327cad 66%,
      #1c6ea4 100%
    );
    background: -webkit-linear-gradient(
      top,
      #5592bb 0%,
      #327cad 66%,
      #1c6ea4 100%
    );
    background: linear-gradient(
      to bottom,
      #5592bb 0%,
      #327cad 66%,
      #1c6ea4 100%
    );
    border-bottom: 2px solid #444444;
  }
  .divTable.blueTable .divTableHeading .divTableHead {
    font-size: 15px;
    font-weight: bold;
    color: #ffffff;
    border-left: 2px solid #d0e4f5;
  }
  .divTable.blueTable .divTableHeading .divTableHead:first-child {
    border-left: none;
  }
  .divTable {
    display: table;
  }
  .divTableRow {
    display: table-row;
  }
  .divTableHeading {
    display: table-header-group;
  }
  .divTableCell,
  .divTableHead {
    display: table-cell;
  }
  .divTableHeading {
    display: table-header-group;
  }
  .divTableBody {
    display: table-row-group;
  }
</style>
