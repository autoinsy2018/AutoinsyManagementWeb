<template>
  <div class="row">
    <div class="col-sm-7">
      <div class="widget-box transparent">
        <div class="widget-header widget-header-flat" style="text-align: left;">
          <h4 class="lighter">
            <i class="icon-signal"></i>
            销售统计
          </h4>
          <div class="widget-toolbar">
            <a href="#" data-action="collapse">
              <i class="icon-chevron-up"></i>
            </a>
          </div>
        </div>
        <div class="widget-body">
          <div class="widget-main padding-4">
            <div id="sales-charts" style="width: 100%; height: 220px; padding: 0px; position: relative;"><canvas class="flot-base" width="955" height="220" style="direction: ltr; position: absolute; left: 0px; top: 0px; width: 955px; height: 220px;"></canvas><div class="flot-text" style="position: absolute; top: 0px; left: 0px; bottom: 0px; right: 0px; font-size: smaller; color: rgb(84, 84, 84);"><div class="flot-x-axis flot-x1-axis xAxis x1Axis" style="position: absolute; top: 0px; left: 0px; bottom: 0px; right: 0px; display: block;"><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 79px; top: 201px; left: 34px; text-align: center;">0.0</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 79px; top: 201px; left: 179px; text-align: center;">1.0</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 79px; top: 201px; left: 325px; text-align: center;">2.0</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 79px; top: 201px; left: 471px; text-align: center;">3.0</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 79px; top: 201px; left: 617px; text-align: center;">4.0</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 79px; top: 201px; left: 763px; text-align: center;">5.0</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 79px; top: 201px; left: 908px; text-align: center;">6.0</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 68px; top: 201px; left: 106px; text-align: center;">0.5</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 68px; top: 201px; left: 252px; text-align: center;">1.5</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 68px; top: 201px; left: 398px; text-align: center;">2.5</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 68px; top: 201px; left: 544px; text-align: center;">3.5</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 68px; top: 201px; left: 690px; text-align: center;">4.5</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 68px; top: 201px; left: 835px; text-align: center;">5.5</div></div><div class="flot-y-axis flot-y1-axis yAxis y1Axis" style="position: absolute; top: 0px; left: 0px; bottom: 0px; right: 0px; display: block;"><div class="flot-tick-label tickLabel" style="position: absolute; top: 187px; left: 1px; text-align: right;">-2.000</div><div class="flot-tick-label tickLabel" style="position: absolute; top: 164px; left: 1px; text-align: right;">-1.500</div><div class="flot-tick-label tickLabel" style="position: absolute; top: 140px; left: 1px; text-align: right;">-1.000</div><div class="flot-tick-label tickLabel" style="position: absolute; top: 117px; left: 1px; text-align: right;">-0.500</div><div class="flot-tick-label tickLabel" style="position: absolute; top: 94px; left: 6px; text-align: right;">0.000</div><div class="flot-tick-label tickLabel" style="position: absolute; top: 70px; left: 6px; text-align: right;">0.500</div><div class="flot-tick-label tickLabel" style="position: absolute; top: 47px; left: 6px; text-align: right;">1.000</div><div class="flot-tick-label tickLabel" style="position: absolute; top: 23px; left: 6px; text-align: right;">1.500</div><div class="flot-tick-label tickLabel" style="position: absolute; top: 0px; left: 6px; text-align: right;">2.000</div></div></div><canvas class="flot-overlay" width="955" height="220" style="direction: ltr; position: absolute; left: 0px; top: 0px; width: 955px; height: 220px;"></canvas><div class="legend"><div style="position: absolute; width: 69px; height: 60px; top: 14px; right: 14px; background-color: rgb(255, 255, 255); opacity: 0.85;"> </div><table style="position:absolute;top:14px;right:14px;;font-size:smaller;color:#545454"><tbody><tr><td class="legendColorBox"><div style="border:1px solid #ccc;padding:1px"><div style="width:4px;height:0;border:5px solid rgb(237,194,64);overflow:hidden"></div></div></td><td class="legendLabel">Domains</td></tr><tr><td class="legendColorBox"><div style="border:1px solid #ccc;padding:1px"><div style="width:4px;height:0;border:5px solid rgb(175,216,248);overflow:hidden"></div></div></td><td class="legendLabel">Hosting</td></tr><tr><td class="legendColorBox"><div style="border:1px solid #ccc;padding:1px"><div style="width:4px;height:0;border:5px solid rgb(203,75,75);overflow:hidden"></div></div></td><td class="legendLabel">Services</td></tr></tbody></table></div></div>
          </div>
        </div>
      </div>
    </div>
    <div class="col-sm-5">
      <div class="widget-box transparent">
        <div class="widget-header widget-header-flat" style="text-align: left;">
          <h4 class="lighter">
            <i class="icon-signal"></i>
            销售统计
          </h4>
          <div class="widget-toolbar">
            <a href="#" data-action="collapse">
              <i class="icon-chevron-up"></i>
            </a>
          </div>
        </div>
        <div class="widget-body">
          <div class="widget-main padding-4">
            <div id="sales-charts" style="width: 100%; height: 220px; padding: 0px; position: relative;"><canvas class="flot-base" width="955" height="220" style="direction: ltr; position: absolute; left: 0px; top: 0px; width: 955px; height: 220px;"></canvas><div class="flot-text" style="position: absolute; top: 0px; left: 0px; bottom: 0px; right: 0px; font-size: smaller; color: rgb(84, 84, 84);"><div class="flot-x-axis flot-x1-axis xAxis x1Axis" style="position: absolute; top: 0px; left: 0px; bottom: 0px; right: 0px; display: block;"><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 79px; top: 201px; left: 34px; text-align: center;">0.0</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 79px; top: 201px; left: 179px; text-align: center;">1.0</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 79px; top: 201px; left: 325px; text-align: center;">2.0</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 79px; top: 201px; left: 471px; text-align: center;">3.0</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 79px; top: 201px; left: 617px; text-align: center;">4.0</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 79px; top: 201px; left: 763px; text-align: center;">5.0</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 79px; top: 201px; left: 908px; text-align: center;">6.0</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 68px; top: 201px; left: 106px; text-align: center;">0.5</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 68px; top: 201px; left: 252px; text-align: center;">1.5</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 68px; top: 201px; left: 398px; text-align: center;">2.5</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 68px; top: 201px; left: 544px; text-align: center;">3.5</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 68px; top: 201px; left: 690px; text-align: center;">4.5</div><div class="flot-tick-label tickLabel" style="position: absolute; max-width: 68px; top: 201px; left: 835px; text-align: center;">5.5</div></div><div class="flot-y-axis flot-y1-axis yAxis y1Axis" style="position: absolute; top: 0px; left: 0px; bottom: 0px; right: 0px; display: block;"><div class="flot-tick-label tickLabel" style="position: absolute; top: 187px; left: 1px; text-align: right;">-2.000</div><div class="flot-tick-label tickLabel" style="position: absolute; top: 164px; left: 1px; text-align: right;">-1.500</div><div class="flot-tick-label tickLabel" style="position: absolute; top: 140px; left: 1px; text-align: right;">-1.000</div><div class="flot-tick-label tickLabel" style="position: absolute; top: 117px; left: 1px; text-align: right;">-0.500</div><div class="flot-tick-label tickLabel" style="position: absolute; top: 94px; left: 6px; text-align: right;">0.000</div><div class="flot-tick-label tickLabel" style="position: absolute; top: 70px; left: 6px; text-align: right;">0.500</div><div class="flot-tick-label tickLabel" style="position: absolute; top: 47px; left: 6px; text-align: right;">1.000</div><div class="flot-tick-label tickLabel" style="position: absolute; top: 23px; left: 6px; text-align: right;">1.500</div><div class="flot-tick-label tickLabel" style="position: absolute; top: 0px; left: 6px; text-align: right;">2.000</div></div></div><canvas class="flot-overlay" width="955" height="220" style="direction: ltr; position: absolute; left: 0px; top: 0px; width: 955px; height: 220px;"></canvas><div class="legend"><div style="position: absolute; width: 69px; height: 60px; top: 14px; right: 14px; background-color: rgb(255, 255, 255); opacity: 0.85;"> </div><table style="position:absolute;top:14px;right:14px;;font-size:smaller;color:#545454"><tbody><tr><td class="legendColorBox"><div style="border:1px solid #ccc;padding:1px"><div style="width:4px;height:0;border:5px solid rgb(237,194,64);overflow:hidden"></div></div></td><td class="legendLabel">Domains</td></tr><tr><td class="legendColorBox"><div style="border:1px solid #ccc;padding:1px"><div style="width:4px;height:0;border:5px solid rgb(175,216,248);overflow:hidden"></div></div></td><td class="legendLabel">Hosting</td></tr><tr><td class="legendColorBox"><div style="border:1px solid #ccc;padding:1px"><div style="width:4px;height:0;border:5px solid rgb(203,75,75);overflow:hidden"></div></div></td><td class="legendLabel">Services</td></tr></tbody></table></div></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
    export default {
        name: "middle"
    }
</script>

<style scoped>

</style>
