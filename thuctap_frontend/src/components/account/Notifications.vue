<script setup>
import { ref } from 'vue'
import EmptyState from './EmptyState.vue'

const activeFilter = ref('examinations')
const notifications = ref([])

const filters = [
  { key: 'examinations', label: 'Phiếu khám', count: 0 },
  { key: 'news', label: 'Tin tức', count: 0 },
  { key: 'notifications', label: 'Thông báo', count: 0 }
]

const setActiveFilter = (filter) => {
  activeFilter.value = filter
}
</script>

<template>
  <div class="notifications">
    <div class="page-header">
      <h1 class="page-title">Danh sách thông báo</h1>
      <button class="options-btn">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M12 13a1 1 0 1 0 0-2 1 1 0 0 0 0 2z"/>
          <path d="M19 13a1 1 0 1 0 0-2 1 1 0 0 0 0 2z"/>
          <path d="M5 13a1 1 0 1 0 0-2 1 1 0 0 0 0 2z"/>
        </svg>
        Tuỳ chọn
      </button>
    </div>
    
    <div class="filter-tabs">
      <button 
        v-for="filter in filters" 
        :key="filter.key"
        class="filter-tab"
        :class="{ active: activeFilter === filter.key }"
        @click="setActiveFilter(filter.key)"
      >
        {{ filter.label }}
        <span v-if="filter.count > 0" class="count">{{ filter.count }}</span>
      </button>
    </div>
    
    <div class="notification-content">
      <EmptyState 
        title="Bạn chưa có thông báo"
        description="Hiện tại không có thông báo nào trong hệ thống."
        :show-illustration="true"
      />
    </div>
  </div>
</template>

<style scoped>
.notifications {
  max-width: 1200px;
}

.page-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 24px;
}

.page-title {
  font-size: 28px;
  font-weight: 600;
  color: #1e293b;
  margin: 0;
}

.options-btn {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 8px 16px;
  border: 1px solid #e2e8f0;
  border-radius: 6px;
  background: white;
  color: #64748b;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s;
}

.options-btn:hover {
  background: #f1f5f9;
  color: #334155;
}

.filter-tabs {
  display: flex;
  gap: 4px;
  margin-bottom: 32px;
  flex-wrap: wrap;
}

.filter-tab {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 10px 20px;
  border: 1px solid #e2e8f0;
  border-radius: 20px;
  background: white;
  color: #64748b;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s;
}

.filter-tab:hover {
  background: #f1f5f9;
  color: #334155;
}

.filter-tab.active {
  background: #22d3ee;
  color: white;
  border-color: #22d3ee;
}

.count {
  background: rgba(255, 255, 255, 0.2);
  padding: 2px 8px;
  border-radius: 12px;
  font-size: 12px;
  font-weight: 600;
}

.filter-tab.active .count {
  background: rgba(255, 255, 255, 0.3);
}

.notification-content {
  background: white;
  border-radius: 12px;
  padding: 48px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  border: 1px solid #e2e8f0;
  text-align: center;
  min-height: 400px;
  display: flex;
  align-items: center;
  justify-content: center;
}

@media (max-width: 768px) {
  .page-header {
    flex-direction: column;
    gap: 16px;
    align-items: stretch;
  }
  
  .notification-content {
    padding: 24px;
  }
}
</style>