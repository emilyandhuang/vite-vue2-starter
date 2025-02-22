<template>
  <div id="base-flow">
    <div ref="containerRef" id="graph"></div>
  </div>
</template>

<script>
import LogicFlow from '@logicflow/core'
import { register } from '@logicflow/vue-node-registry'

import ProgressNode from './progress-node.vue'
import ProgressNode2 from './progress-node-2.vue'
import '@logicflow/core/dist/index.css'

export default {
  name: 'BaseFlow',
  data() {
    return {
      lf: null,
    }
  },
  mounted() {
    this.lf = new LogicFlow({
      container: this.$refs.containerRef,
      grid: true,
    })
    register(
      // 方案1
      // {
      //   type: 'progress',
      //   component: ProgressNode,
      // },
      // 方案2
      {
        type: 'progress',
        component: ProgressNode2,
      },
      this.lf,
    )

    this.lf.render({})

    const node1 = this.lf.addNode({
      id: 'vue-node-1',
      type: 'progress',
      x: 80,
      y: 80,
      properties: {
        progress: 60,
        // width: 224, // 方案1
        width: 204, // 方案2
        height: 100,
      },
    })
  },
}
</script>

<style>
#graph {
  height: 100vh;
}

#graph .lf-graph {
  background: #f2f3f5;
}
</style>