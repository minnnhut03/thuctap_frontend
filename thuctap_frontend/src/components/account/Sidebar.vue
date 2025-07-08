<script setup>
import { defineEmits, defineProps } from 'vue'

const emit = defineEmits(['tab-change'])
const props = defineProps({
  activeTab: String,
  notifications: Number
})

const handleTabClick = (tab) => {
  emit('tab-change', tab)
}
</script>

<template>
  <aside class="sidebar">
    <div class="sidebar-header">
      <button class="add-record-btn" @click="handleTabClick('add-record')">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M12 5v14M5 12h14"/>
        </svg>
        Thêm hồ sơ
      </button>
    </div>
    
    <nav class="sidebar-nav">
      <button 
        class="nav-item"
        :class="{ active: activeTab === 'patient-records' }"
        @click="handleTabClick('patient-records')"
      >
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M16 21v-2a4 4 0 0 0-4-4H6a4 4 0 0 0-4 4v2"/>
          <circle cx="9" cy="7" r="4"/>
          <path d="M22 21v-2a4 4 0 0 0-3-3.87M16 3.13a4 4 0 0 1 0 7.75"/>
        </svg>
        Hồ sơ bệnh nhân
      </button>
      
      <button 
        class="nav-item"
        :class="{ active: activeTab === 'medical-examinations' }"
        @click="handleTabClick('medical-examinations')"
      >
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/>
          <polyline points="14,2 14,8 20,8"/>
          <line x1="16" y1="13" x2="8" y2="13"/>
          <line x1="16" y1="17" x2="8" y2="17"/>
          <polyline points="10,9 9,9 8,9"/>
        </svg>
        Phiếu khám bệnh
      </button>
      
      <button 
        class="nav-item"
        :class="{ active: activeTab === 'notifications' }"
        @click="handleTabClick('notifications')"
      >
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M18 8A6 6 0 0 0 6 8c0 7-3 9-3 9h18s-3-2-3-9"/>
          <path d="M13.73 21a2 2 0 0 1-3.46 0"/>
        </svg>
        Thông báo
        <span class="notification-badge">{{ notifications }}+</span>
      </button>
    </nav>
  </aside>
</template>

<style scoped>
.sidebar {
  position: fixed;
  top: 120px;
  left: 0;
  width: 280px;
  height: calc(100vh - 120px);
  background: white;
  border-right: 1px solid #e2e8f0;
  padding: 24px;
  z-index: 100;
}

.sidebar-header {
  margin-bottom: 32px;
}

.add-record-btn {
  display: flex;
  align-items: center;
  gap: 8px;
  width: 100%;
  padding: 12px 16px;
  background: #22d3ee;
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s;
}

.add-record-btn:hover {
  background: #06b6d4;
  transform: translateY(-1px);
}

.sidebar-nav {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.nav-item {
  display: flex;
  align-items: center;
  gap: 12px;
  width: 100%;
  padding: 12px 16px;
  background: none;
  border: none;
  border-radius: 8px;
  color: #64748b;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s;
  text-align: left;
}

.nav-item:hover {
  background: #f1f5f9;
  color: #334155;
}

.nav-item.active {
  background: #e0f2fe;
  color: #0891b2;
  border-left: 3px solid #22d3ee;
}

.nav-item svg {
  flex-shrink: 0;
}

.notification-badge {
  margin-left: auto;
  background: #ef4444;
  color: white;
  font-size: 12px;
  padding: 2px 8px;
  border-radius: 12px;
  font-weight: 600;
}

@media (max-width: 768px) {
  .sidebar {
    top: 80px; 
    height: calc(100vh - 80px);
    transform: translateX(-100%);
    transition: transform 0.3s;
  }
  
  .sidebar.open {
    transform: translateX(0);
  }
}

@media (max-width: 992px) {
  .sidebar {
    top: 80px; 
    height: calc(100vh - 80px);
  }
}
</style>