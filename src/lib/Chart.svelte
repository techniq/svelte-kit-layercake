<script>
  // import { LayerCake, Svg } from "layercake";
  // import LayerCake from "layercake/src/LayerCake.svelte";
  // import Svg from "layercake/src/layouts/Svg.svelte";
  import { LayerCake, Svg } from "$lib/layercake";

  import Line from "./Line.svelte";
  import Area from "./Area.svelte";
  import AxisX from "./AxisX.svelte";
  import AxisY from "./AxisY.svelte";

  import data from "./points";

  const xKey = "myX";
  const yKey = "myY";

  data.forEach((d) => {
    d[yKey] = +d[yKey];
  });
</script>

<div class="chart-container">
  <LayerCake
    padding={{ right: 10, bottom: 20, left: 25 }}
    x={xKey}
    y={yKey}
    yDomain={[0, null]}
    {data}
  >
    <Svg>
      <AxisX />
      <AxisY ticks={4} />
      <Line />
      <Area />
    </Svg>
  </LayerCake>
</div>

<style>
  /*
    The wrapper div needs to have an explicit width and height in CSS.
    It can also be a flexbox child or CSS grid element.
    The point being it needs dimensions since the <LayerCake> element will
    expand to fill it.
  */
  .chart-container {
    width: 500px;
    height: 500px;
  }
</style>
