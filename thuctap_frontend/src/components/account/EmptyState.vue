<script setup>
import { defineProps } from 'vue'

const props = defineProps({
  title: {
    type: String,
    required: true
  },
  description: {
    type: String,
    required: true
  },
  showIllustration: {
    type: Boolean,
    default: true
  }
})
</script>

<template>
  <div class="empty-state">
    <div v-if="showIllustration" class="illustration">
      <svg width="120" height="120" viewBox="0 0 120 120" fill="none">
        <!-- Magnifying glass illustration -->
        <circle cx="45" cy="45" r="20" stroke="#22d3ee" stroke-width="3" fill="none"/>
        <path d="M61 61L75 75" stroke="#22d3ee" stroke-width="3" stroke-linecap="round"/>
        <circle cx="45" cy="45" r="12" fill="#e0f2fe"/>
        <path d="M39 45L51 45M45 39L45 51" stroke="#ef4444" stroke-width="2" stroke-linecap="round"/>
        
        <!-- Decorative elements -->
        <circle cx="25" cy="25" r="2" fill="#22d3ee" opacity="0.5"/>
        <circle cx="85" cy="30" r="3" fill="#06b6d4" opacity="0.3"/>
        <circle cx="90" cy="80" r="2" fill="#22d3ee" opacity="0.4"/>
        <circle cx="30" cy="85" r="2" fill="#06b6d4" opacity="0.3"/>
        
        <!-- Lines -->
        <path d="M15 15L25 25" stroke="#22d3ee" stroke-width="2" opacity="0.3"/>
        <path d="M95 15L105 25" stroke="#06b6d4" stroke-width="2" opacity="0.3"/>
        <path d="M15 95L25 105" stroke="#22d3ee" stroke-width="2" opacity="0.3"/>
      </svg>
    </div>
    
    <h3 class="empty-title">{{ title }}</h3>
    <p class="empty-description">{{ description }}</p>
  </div>
</template>

<style scoped>
.empty-state {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 48px 24px;
  color: #64748b;
}

.illustration {
  margin-bottom: 24px;
  opacity: 0.8;
}

.empty-title {
  font-size: 20px;
  font-weight: 600;
  color: #334155;
  margin: 0 0 12px 0;
}

.empty-description {
  font-size: 16px;
  color: #64748b;
  margin: 0;
  max-width: 400px;
  line-height: 1.5;
}
</style>