<template>
  <div>
    <v-plotly
      style="width: 300px !important; height: 350px !important"
      :data="plotData"
      :layout="plotLayout"
      :config="{ displayModeBar: False }"
      :options="{}"
    />
    <div style="width: 300px; padding: 0 5px;">
      <input
        type="range"
        v-model.number="sliderValue"
        :min="-5"
        :max="5"
        :step="0.05"
        style="width: 100%;"
      />
      <div style="display: flex; justify-content: space-between; font-size: 11px; color: #888; margin-top: -2px;">
        <span>x = {{ sliderValue.toFixed(2) }}</span>
        <span>σ(x) = {{ sigmoidAt.toFixed(3) }}</span>
        <span>lin(x) = {{ linearAt.toFixed(3) }}</span>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const xVals = [-5, -4.814815, -4.62963, -4.444444, -4.259259, -4.074074, -3.888889, -3.703704, -3.518519, -3.333333, -3.148148, -2.962963, -2.777778, -2.592593, -2.407407, -2.222222, -2.037037, -1.851852, -1.666667, -1.481481, -1.296296, -1.111111, -0.925926, -0.740741, -0.555556, -0.37037, -0.185185, 0, 0.185185, 0.37037, 0.555556, 0.740741, 0.925926, 1.111111, 1.296296, 1.481481, 1.666667, 1.851852, 2.037037, 2.222222, 2.407407, 2.592593, 2.777778, 2.962963, 3.148148, 3.333333, 3.518519, 3.703704, 3.888889, 4.074074, 4.259259, 4.444444, 4.62963, 4.814815, 5]

const sigmoidY = [0.006693, 0.008044, 0.009664, 0.011607, 0.013936, 0.016724, 0.020058, 0.02404, 0.02879, 0.034445, 0.041164, 0.049127, 0.058537, 0.069617, 0.08261, 0.097773, 0.115369, 0.135656, 0.158869, 0.185204, 0.214789, 0.247664, 0.283752, 0.322842, 0.364576, 0.408452, 0.453836, 0.5, 0.546164, 0.591548, 0.635424, 0.677158, 0.716248, 0.752336, 0.785211, 0.814796, 0.841131, 0.864344, 0.884631, 0.902227, 0.91739, 0.930383, 0.941463, 0.950873, 0.958836, 0.965555, 0.97121, 0.97596, 0.979942, 0.983276, 0.986064, 0.988393, 0.990336, 0.991956, 0.993307]

const linearY = [-0.053, -0.0291, -0.0045, 0.0197, 0.0437, 0.0678, 0.0920, 0.1162, 0.1404, 0.1644, 0.1886, 0.2127, 0.2368, 0.2610, 0.2851, 0.3092, 0.3334, 0.3575, 0.3816, 0.4058, 0.4299, 0.4541, 0.4782, 0.5024, 0.5265, 0.5507, 0.5748, 0.5990, 0.6232, 0.6473, 0.6715, 0.6956, 0.7198, 0.7439, 0.7681, 0.7922, 0.8164, 0.8405, 0.8646, 0.8888, 0.9129, 0.9370, 0.9612, 0.9853, 1.0094, 1.0336, 1.0576, 1.0818, 1.1060, 1.1302, 1.1543, 1.1783, 1.2025, 1.2271, 1.2510]

// Pre-generated random data points (seeded for reproducibility)
// Class 0: x in [-5, -1], y = 0
const class0x = [-4.93, -4.71, -4.52, -4.38, -4.21, -4.07, -3.88, -3.74, -3.61, -3.42, -3.29, -3.15, -2.98, -2.83, -2.71, -2.56, -2.43, -2.31, -2.18, -2.02, -1.91, -1.78, -1.63, -1.49, -1.37, -1.22, -1.09, -4.65, -4.44, -3.97, -3.53, -3.06, -2.62, -2.14, -1.71, -1.33, -4.82, -4.15, -3.38, -2.77, -2.25, -1.85, -1.44, -1.12, -4.55, -3.81, -2.91, -2.48, -1.57, -1.05]
const class0y = class0x.map(() => 0)

// Class 1: x in [-1.5, 5], y = 1
const class1x = [-1.47, -1.31, -1.18, -1.02, -0.89, -0.73, -0.58, -0.42, -0.27, -0.11, 0.04, 0.19, 0.33, 0.48, 0.62, 0.77, 0.91, 1.06, 1.21, 1.35, 1.49, 1.64, 1.78, 1.93, 2.07, 2.22, 2.36, 2.51, 2.65, 2.79, 2.94, 3.15, 3.38, 3.61, 3.83, 4.05, 4.28, 4.51, 4.73, 4.96, -1.38, -0.95, -0.52, -0.08, 0.36, 0.79, 1.13, 1.57, 1.88, 2.31, 2.72, 3.24, 3.71, 4.19, 4.67]
const class1y = class1x.map(() => 1)

const sliderValue = ref(0)

function sigmoid(x) {
  return 1 / (1 + Math.exp(-x))
}

function linear(x) {
  return 0.5 + x * 0.1
}

const sigmoidAt = computed(() => sigmoid(sliderValue.value))
const linearAt = computed(() => linear(sliderValue.value))

// Build vertical line data for class 0
const class0LineX = []
const class0LineY = []
class0x.forEach(x => {
  class0LineX.push(x, x, null)
  class0LineY.push(-0.02, 0.02, null)
})

// Build vertical line data for class 1
const class1LineX = []
const class1LineY = []
class1x.forEach(x => {
  class1LineX.push(x, x, null)
  class1LineY.push(0.98, 1.02, null)
})

// Static traces (don't depend on slider)
const staticTraces = [
  {
    mode: 'lines',
    name: 'Class 0',
    type: 'scatter',
    x: class0LineX,
    y: class0LineY,
    line: { color: 'orange', width: 2 },
    showlegend: false,
    hoverinfo: 'skip'
  },
  {
    mode: 'lines',
    name: 'Class 1',
    type: 'scatter',
    x: class1LineX,
    y: class1LineY,
    line: { color: 'orange', width: 2 },
    showlegend: false,
    hoverinfo: 'skip'
  },
  {
    mode: 'lines',
    name: 'Sigmoid',
    type: 'scatter',
    x: xVals,
    y: sigmoidY,
    line: { color: 'blue' },
    visible: 'legendonly',
    showlegend: true
  },
  {
    mode: 'lines',
    name: 'Linear',
    type: 'scatter',
    x: xVals,
    y: linearY,
    line: { color: 'black' },
    visible: true,
    showlegend: true
  },
  {
    mode: 'lines',
    name: 'x position',
    type: 'scatter',
    x: [sliderValue.value, sliderValue.value],
    y: [-0.1, 1.1],
    line: { color: 'red', width: 2, dash: 'dash' },
    showlegend: false,
    hoverinfo: 'skip'
  }
]

const plotData = computed(() => {
  // Update only the dynamic traces
  staticTraces[4].x = [sliderValue.value, sliderValue.value]
  
  return [
    ...staticTraces,
    {
      mode: 'markers',
      name: 'σ(x)',
      type: 'scatter',
      x: [sliderValue.value],
      y: [sigmoidAt.value],
      marker: { color: 'blue', size: 10, symbol: 'circle' },
      visible: true,
      showlegend: false,
      hovertemplate: 'σ(%{x:.2f}) = %{y:.3f}<extra></extra>'
    }
  ]
})

const plotLayout = computed(() => ({
  xaxis: { title: 'x', range: [-5.2, 5.2] },
  yaxis: { title: 'f(x)', range: [-0.15, 1.15] },
  margin: { l: 40, r: 0, b: 70, t: 20, pad: 2 },
  legend: { x: 0.95, y: 0.3, xanchor: 'right', yanchor: 'bottom' },
  shapes: [
    {
      type: 'line',
      x0: -5, x1: 5,
      y0: 0.5, y1: 0.5,
      line: { color: 'gray', width: 1, dash: 'dot' }
    }
  ]
}))
</script>
