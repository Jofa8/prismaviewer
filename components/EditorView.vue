<template>
  <div class="border-l border-[#e5e7eb] bg-[#fafafa]">
    <VueFlow :nodes="nodes" :edges="edges" :vueFlowProps="{ fitView: true }" style="width: 100%; height: 100%">
      <Background />
    </VueFlow>
  </div>
</template>

<script setup lang="ts">
const nodes = ref([
  {
    id: 'node-1',
    color: '#ff00ff',
    position: { x: 150, y: 100 },
    label: 'Start Node',
    type: 'default',
    data: { label: 'Start Node' },
  },
  {
    id: 'node-2',
    position: { x: 300, y: 200 },
    label: 'Approval Node',
    type: 'default',
    data: { label: 'Approval Node' },
  },
  {
    id: 'node-3',
    position: { x: 450, y: 100 },
    label: 'End Node',
    type: 'default',
    data: { label: 'End Node' },
  },
])

const edges = ref([
  { id: 'e1-2', source: 'node-1', target: 'node-2' },
  { id: 'e2-3', source: 'node-2', target: 'node-3' },
])
</script>
