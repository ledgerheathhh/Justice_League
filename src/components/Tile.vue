<template name="BaseTile">
  <div 
    class="tile" 
    :class="[size, { 'live': isLive }]" 
    :style="{ backgroundColor: color }"
    @click="handleClick"
  >
    <div class="tile-content">
      <div v-if="icon" class="tile-icon">
        <component :is="icon" />
      </div>
      <div class="tile-title">{{ title }}</div>
      <div v-if="isLive" class="tile-live-content">
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { defineProps, defineEmits, defineOptions } from 'vue';

// 定义组件名称为多词组合
defineOptions({
  name: 'BaseTile'
});

const props = defineProps({
  title: {
    type: String,
    required: true
  },
  size: {
    type: String,
    default: 'medium', // small, medium, large
    validator: (value: string) => ['small', 'medium', 'large'].includes(value)
  },
  color: {
    type: String,
    default: '#0078D7'
  },
  icon: {
    type: Object,
    default: null
  },
  isLive: {
    type: Boolean,
    default: false
  },
  route: {
    type: String,
    default: ''
  }
});

const emit = defineEmits(['click']);

const handleClick = () => {
  emit('click', props.route);
};
</script>

<style scoped>
.tile {
  position: relative;
  border-radius: 4px;
  margin: 8px;
  padding: 16px;
  color: white;
  cursor: pointer;
  transition: transform 0.2s, box-shadow 0.2s;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}

.tile:hover {
  transform: translateY(-4px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
}

.tile-content {
  display: flex;
  flex-direction: column;
  height: 100%;
}

.tile-icon {
  font-size: 2rem;
  margin-bottom: 8px;
}

.tile-title {
  font-weight: bold;
  font-size: 1.2rem;
  margin-bottom: 8px;
}

.tile-live-content {
  flex-grow: 1;
  overflow: hidden;
}

.small {
  width: 120px;
  height: 120px;
}

.medium {
  width: 250px;
  height: 120px;
}

.large {
  width: 250px;
  height: 250px;
}

.live {
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0% {
    opacity: 1;
  }
  50% {
    opacity: 0.8;
  }
  100% {
    opacity: 1;
  }
}
</style>