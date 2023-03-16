<script setup lang='ts'>
import { computed, ref } from 'vue'
import { NModal } from 'naive-ui'
import General from './General.vue'

const props = defineProps<Props>()

const emit = defineEmits<Emit>()

interface Props {
  visible: boolean
}

interface Emit {
  (e: 'update:visible', visible: boolean): void
}

const show = computed({
  get() {
    return props.visible
  },
  set(visible: boolean) {
    emit('update:visible', visible)
  },
})
</script>

<template>
  <NModal v-model:show="show" :auto-focus="false" preset="card" style="width: 95%; max-width: 640px">
    <div>
      <div class="min-h-[100px]">
        <General />
      </div>
    </div>
  </NModal>
</template>
