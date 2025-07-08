<script setup>
import { ref } from 'vue'
import EmptyState from './EmptyState.vue'

const activeFilter = ref('paid')
const examinations = ref([])

const filters = [
  { key: 'paid', label: 'Đã thanh toán', count: 0 },
  { key: 'unpaid', label: 'Chưa thanh toán', count: 0 },
  { key: 'examined', label: 'Đã khám', count: 0 },
  { key: 'cancelled', label: 'Đã huỷ', count: 0 }
]

const setActiveFilter = (filter) => {
  activeFilter.value = filter
}
</script>

<template>
  <div class="medical-examinations">
    <div class="page-header">
      <h1 class="page-title">Danh sách phiếu khám bệnh</h1>
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
    
    <div class="examination-content">
      <EmptyState 
        title="Bạn chưa có phiếu khám nào"
        description="Hiện tại không có phiếu khám bệnh nào trong hệ thống."
        :show-illustration="true"
      />
    </div>
  </div>
</template>

<style scoped>
.medical-examinations {
  max-width: 1200px;
}

.page-header {
  margin-bottom: 24px;
}

.page-title {
  font-size: 28px;
  font-weight: 600;
  color: #1e293b;
  margin: 0;
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

.examination-content {
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
  .examination-content {
    padding: 24px;
  }
}
</style>