<script setup>
import { ref } from 'vue'
import EmptyState from './EmptyState.vue'
import EditPatientForm from './EditPatientForm.vue'
import PatientDetailsModal from './PatientDetailsModal.vue'

const patients = ref([
  {
    id: 1,
    name: 'Nguyễn Minh Duy',
    birthDate: '12/06/2005',
    phone: '033****255',
    gender: 'Nam',
    address: 'Thành phố Cần Thơ',
    ethnicity: 'Kinh'
  }
])

const searchQuery = ref('')
const selectedPatient = ref(null)
const showEditForm = ref(false)
const showDetailsModal = ref(false)

const handleDelete = (patient) => {
  if (confirm(`Bạn có chắc chắn muốn xóa hồ sơ của ${patient.name}?`)) {
    patients.value = patients.value.filter(p => p.id !== patient.id)
  }
}

const handleEdit = (patient) => {
  selectedPatient.value = patient
  showEditForm.value = true
}

const handleViewDetails = (patient) => {
  selectedPatient.value = patient
  showDetailsModal.value = true
}

const handleUpdatePatient = (updatedPatient) => {
  const index = patients.value.findIndex(p => p.id === selectedPatient.value.id)
  if (index !== -1) {
    patients.value[index] = { ...patients.value[index], ...updatedPatient }
  }
  showEditForm.value = false
  selectedPatient.value = null
}

const handleCancelEdit = () => {
  showEditForm.value = false
  selectedPatient.value = null
}

const handleCloseDetailsModal = () => {
  showDetailsModal.value = false
  selectedPatient.value = null
}
</script>

<template>
  <div class="patient-records">
    <PatientDetailsModal 
      v-if="showDetailsModal && selectedPatient"
      :patient="selectedPatient"
      @close="handleCloseDetailsModal"
    />
    
    <EditPatientForm 
      v-if="showEditForm"
      :patient="selectedPatient"
      @update="handleUpdatePatient"
      @cancel="handleCancelEdit"
    />
    
    <div v-else-if="!showEditForm">
    <div class="page-header">
      <h1 class="page-title">Danh sách hồ sơ bệnh nhân</h1>
    </div>
    
    
    <div v-if="patients.length > 0" class="patient-list">
      <div v-for="patient in patients" :key="patient.id" class="patient-card">
        <div class="patient-info">
          <div class="info-row">
            <span class="label">Họ và tên:</span>
            <span class="value">{{ patient.name }}</span>
          </div>
          <div class="info-row">
            <span class="label">Ngày sinh:</span>
            <span class="value">{{ patient.birthDate }}</span>
          </div>
          <div class="info-row">
            <span class="label">Số điện thoại:</span>
            <span class="value">{{ patient.phone }}</span>
          </div>
          <div class="info-row">
            <span class="label">Giới tính:</span>
            <span class="value">{{ patient.gender }}</span>
          </div>
          <div class="info-row">
            <span class="label">Địa chỉ:</span>
            <span class="value">{{ patient.address }}</span>
          </div>
          <div class="info-row">
            <span class="label">Dân tộc:</span>
            <span class="value">{{ patient.ethnicity }}</span>
          </div>
        </div>
        
        <div class="patient-actions">
          <button class="action-btn delete" @click="handleDelete(patient)">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <polyline points="3,6 5,6 21,6"/>
              <path d="M19 6v14a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2V6m3 0V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2"/>
            </svg>
            Xóa hồ sơ
          </button>
          <button class="action-btn edit" @click="handleEdit(patient)">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M11 4H4a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7"/>
              <path d="M18.5 2.5a2.121 2.121 0 0 1 3 3L12 15l-4 1 1-4 9.5-9.5z"/>
            </svg>
            Sửa hồ sơ
          </button>
          <button class="action-btn details" @click="handleViewDetails(patient)">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"/>
              <circle cx="12" cy="12" r="3"/>
            </svg>
            Chi tiết
          </button>
        </div>
      </div>
    </div>
    
    <EmptyState 
      v-else
      title="Chưa có hồ sơ bệnh nhân"
      description="Bạn chưa có hồ sơ bệnh nhân nào. Hãy thêm hồ sơ mới."
    />
    </div>
  </div>
</template>

<style scoped>
.patient-records {
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

.search-bar {
  margin-bottom: 24px;
}

.search-input {
  width: 100%;
  max-width: 400px;
  padding: 12px 16px;
  border: 1px solid #e2e8f0;
  border-radius: 8px;
  font-size: 14px;
  color: #334155;
  background: white;
  transition: border-color 0.2s;
}

.search-input:focus {
  outline: none;
  border-color: #22d3ee;
  box-shadow: 0 0 0 3px rgba(34, 211, 238, 0.1);
}

.patient-list {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.patient-card {
  background: white;
  border-radius: 12px;
  padding: 24px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  border: 1px solid #e2e8f0;
  transition: transform 0.2s, box-shadow 0.2s;
}

.patient-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

.patient-info {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 16px;
  margin-bottom: 24px;
}

.info-row {
  display: flex;
  align-items: center;
  gap: 8px;
}

.label {
  font-weight: 500;
  color: #64748b;
  min-width: 120px;
}

.value {
  color: #1e293b;
  font-weight: 500;
}

.patient-actions {
  display: flex;
  gap: 12px;
  justify-content: flex-end;
  flex-wrap: wrap;
}

.action-btn {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 8px 16px;
  border: 1px solid;
  border-radius: 6px;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s;
}

.action-btn.delete {
  color: #ef4444;
  border-color: #ef4444;
  background: white;
}

.action-btn.delete:hover {
  background: #ef4444;
  color: white;
}

.action-btn.edit {
  color: #22d3ee;
  border-color: #22d3ee;
  background: white;
}

.action-btn.edit:hover {
  background: #22d3ee;
  color: white;
}

.action-btn.details {
  color: #334155;
  border-color: #334155;
  background: white;
}

.action-btn.details:hover {
  background: #334155;
  color: white;
}

@media (max-width: 768px) {
  .patient-info {
    grid-template-columns: 1fr;
  }
  
  .patient-actions {
    justify-content: stretch;
  }
  
  .action-btn {
    flex: 1;
    justify-content: center;
  }
}
</style>