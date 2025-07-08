<script setup>
import { ref } from 'vue'
import Sidebar from './Sidebar.vue'
import PatientRecords from './PatientRecords.vue'
import MedicalExaminations from './MedicalExaminations.vue'
import Notifications from './Notifications.vue'

const activeTab = ref('patient-records')
const notifications = ref(0)

const handleTabChange = (tab) => {
  activeTab.value = tab
}
</script>

<template>
  <div class="app">
    <Header />
    <Sidebar 
      :active-tab="activeTab" 
      :notifications="notifications"
      @tab-change="handleTabChange" 
    />
    
    <main class="main-content">
      <div class="breadcrumb">
        <span class="breadcrumb-item">Trang chủ</span>
        <span class="breadcrumb-separator">></span>
        <span class="breadcrumb-item active" v-if="activeTab === 'patient-records'">Hồ sơ bệnh nhân</span>
        <span class="breadcrumb-item active" v-if="activeTab === 'medical-examinations'">Phiếu khám bệnh</span>
        <span class="breadcrumb-item active" v-if="activeTab === 'notifications'">Thông báo</span>
      </div>
      
      <PatientRecords v-if="activeTab === 'patient-records'" />
      <MedicalExaminations v-if="activeTab === 'medical-examinations'" />
      <Notifications v-if="activeTab === 'notifications'" />
    </main>
  </div>
</template>

<style scoped>
.app {
  display: flex;
  min-height: 100vh;
  background-color: #f8fafc;
  padding-top: 120px; 
}

.main-content {
  flex: 1;
  padding: 32px;
  margin-left: 280px;
}

.breadcrumb {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 32px;
  font-size: 14px;
  color: #64748b;
}

.breadcrumb-item {
  color: #64748b;
}

.breadcrumb-item.active {
  color: #22d3ee;
  font-weight: 500;
}

.breadcrumb-separator {
  color: #cbd5e1;
}

@media (max-width: 768px) {
  .app {
    padding-top: 80px; 
  }
  
  .main-content {
    margin-left: 0;
    padding: 16px;
  }
}

@media (max-width: 992px) {
  .app {
    padding-top: 80px; 
  }
}
</style>