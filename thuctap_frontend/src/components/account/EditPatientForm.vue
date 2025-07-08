<template>
  <div class="edit-patient-form">
    <div class="page-header">
      <div class="breadcrumb">
        <span class="breadcrumb-item">Trang chủ</span>
        <span class="breadcrumb-separator">></span>
        <span class="breadcrumb-item active">Cập nhật thông tin</span>
      </div>
    </div>

    <div class="form-container">
      <div class="info-notice">
        <i class="fas fa-info-circle"></i>
        Vui lòng cung cấp thông tin chính xác để được phục vụ tốt nhất.
      </div>

      <form @submit.prevent="handleSubmit" class="patient-form">
        <div class="form-section">
          <div class="section-header">
            <span class="required-indicator">(*) Thông tin bắt buộc nhập</span>
          </div>

          <h3 class="section-title">Thông tin chung</h3>

          <div class="form-row">
            <div class="form-group">
              <label class="form-label">
                Họ và tên (có dấu) <span class="required">*</span>
              </label>
              <input
                type="text"
                v-model="formData.fullName"
                class="form-input"
                placeholder="NGUYỄN MINH DUY"
                required
              />
            </div>

            <div class="form-group">
              <label class="form-label">
                Ngày sinh (năm/tháng/ngày) <span class="required">*</span>
              </label>
              <div class="date-inputs">
                <select v-model="formData.birthYear" class="form-select" required>
                  <option value="">2005</option>
                  <option v-for="year in years" :key="year" :value="year">{{ year }}</option>
                </select>
                <select v-model="formData.birthMonth" class="form-select" required>
                  <option value="">6</option>
                  <option v-for="month in months" :key="month.value" :value="month.value">
                    {{ month.label }}
                  </option>
                </select>
                <select v-model="formData.birthDay" class="form-select" required>
                  <option value="">12</option>
                  <option v-for="day in days" :key="day" :value="day">{{ day }}</option>
                </select>
              </div>
            </div>
          </div>

          <div class="form-row">
            <div class="form-group">
              <label class="form-label">
                Số điện thoại <span class="required">*</span>
              </label>
              <input
                type="tel"
                v-model="formData.phone"
                class="form-input"
                placeholder="0338890255"
                required
              />
            </div>

            <div class="form-group">
              <label class="form-label">
                Giới tính <span class="required">*</span>
              </label>
              <select v-model="formData.gender" class="form-select" required>
                <option value="">Nam</option>
                <option value="Nam">Nam</option>
                <option value="Nữ">Nữ</option>
                <option value="Khác">Khác</option>
              </select>
            </div>
          </div>

          <div class="form-row">
            <div class="form-group">
              <label class="form-label">
                Nghề nghiệp <span class="required">*</span>
              </label>
              <input
                type="text"
                v-model="formData.occupation"
                class="form-input"
                placeholder="Khác"
                required
              />
            </div>

            <div class="form-group">
              <label class="form-label">
                Mã định danh/CCCD/Passport <span class="required">*</span>
              </label>
              <input
                type="text"
                v-model="formData.idNumber"
                class="form-input"
                placeholder="Vui lòng nhập Mã định danh/CCCD/Passport"
                required
              />
            </div>
          </div>

          <div class="form-row">
            <div class="form-group">
              <label class="form-label">Địa chỉ Email</label>
              <input
                type="email"
                v-model="formData.email"
                class="form-input"
                placeholder="Nhập địa chỉ email để nhận phiếu khám"
              />
            </div>

            <div class="form-group">
              <label class="form-label">Dân tộc</label>
              <select v-model="formData.ethnicity" class="form-select">
                <option value="">Kinh</option>
                <option value="Kinh">Kinh</option>
                <option value="Tày">Tày</option>
                <option value="Thái">Thái</option>
                <option value="Hoa">Hoa</option>
                <option value="Khmer">Khmer</option>
                <option value="Mường">Mường</option>
                <option value="Nùng">Nùng</option>
                <option value="Hmông">Hmông</option>
                <option value="Dao">Dao</option>
                <option value="Gia Rai">Gia Rai</option>
                <option value="Ê Đê">Ê Đê</option>
                <option value="Ba Na">Ba Na</option>
                <option value="Sán Chay">Sán Chay</option>
                <option value="Chăm">Chăm</option>
                <option value="Sán Dìu">Sán Dìu</option>
                <option value="Hrê">Hrê</option>
                <option value="Ra Glai">Ra Glai</option>
                <option value="Mnông">Mnông</option>
                <option value="Thổ">Thổ</option>
                <option value="Xtiêng">Xtiêng</option>
                <option value="Khác">Khác</option>
              </select>
            </div>
          </div>
        </div>

        <div class="form-section">
          <h3 class="section-title">Địa chỉ theo CCCD</h3>

          <div class="form-row">
            <div class="form-group">
              <label class="form-label">
                Tỉnh/Thành <span class="required">*</span>
              </label>
              <select 
                v-model="formData.province" 
                @change="onProvinceChange"
                class="form-select" 
                required
              >
                <option value="">Thành phố Cần Thơ</option>
                <option v-for="province in provinces" :key="province.code" :value="province">
                  {{ province.name }}
                </option>
              </select>
            </div>

            <div class="form-group">
              <label class="form-label">
                Quận/Huyện <span class="required">*</span>
              </label>
              <select 
                v-model="formData.district" 
                @change="onDistrictChange"
                class="form-select" 
                :disabled="!formData.province"
                required
              >
                <option value="">Chọn quận huyện</option>
                <option v-for="district in districts" :key="district.code" :value="district">
                  {{ district.name }}
                </option>
              </select>
            </div>
          </div>

          <div class="form-row">
            <div class="form-group">
              <label class="form-label">
                Phường/Xã <span class="required">*</span>
              </label>
              <select 
                v-model="formData.ward" 
                class="form-select" 
                :disabled="!formData.district"
                required
              >
                <option value="">Chọn xã phường</option>
                <option v-for="ward in wards" :key="ward.code" :value="ward">
                  {{ ward.name }}
                </option>
              </select>
            </div>

            <div class="form-group">
              <label class="form-label">
                Số nhà/Tên đường/Ấp thôn xóm <span class="required">*</span>
              </label>
              <div class="address-note">(Không bao gồm tỉnh/thành, quận/huyện, phường/xã)</div>
              <input
                type="text"
                v-model="formData.address"
                class="form-input"
                placeholder="Nhập số nhà, tên đường, ấp thôn xóm,..."
                required
              />
            </div>
          </div>
        </div>

        <div class="form-actions">
          <button type="submit" class="btn btn-primary" :disabled="loading">
            <i class="fas fa-save" v-if="!loading"></i>
            <i class="fas fa-spinner fa-spin" v-if="loading"></i>
            {{ loading ? 'Đang cập nhật...' : 'Cập nhật' }}
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive, onMounted, computed } from 'vue'

const props = defineProps({
  patient: {
    type: Object,
    default: () => ({})
  }
})

const emit = defineEmits(['update', 'cancel'])

const loading = ref(false)
const provinces = ref([])
const districts = ref([])
const wards = ref([])

const formData = reactive({
  fullName: 'NGUYỄN MINH DUY',
  birthYear: '2005',
  birthMonth: '6',
  birthDay: '12',
  phone: '0338890255',
  gender: 'Nam',
  occupation: 'Khác',
  idNumber: '',
  email: '',
  ethnicity: 'Kinh',
  province: null,
  district: null,
  ward: null,
  address: ''
})


const years = computed(() => {
  const currentYear = new Date().getFullYear()
  const yearList = []
  for (let year = currentYear; year >= 1920; year--) {
    yearList.push(year)
  }
  return yearList
})


const months = computed(() => [
  { value: 1, label: '1' },
  { value: 2, label: '2' },
  { value: 3, label: '3' },
  { value: 4, label: '4' },
  { value: 5, label: '5' },
  { value: 6, label: '6' },
  { value: 7, label: '7' },
  { value: 8, label: '8' },
  { value: 9, label: '9' },
  { value: 10, label: '10' },
  { value: 11, label: '11' },
  { value: 12, label: '12' }
])


const days = computed(() => {
  const dayList = []
  for (let day = 1; day <= 31; day++) {
    dayList.push(day)
  }
  return dayList
})


const loadProvinces = async () => {
  try {
    const response = await fetch('https://provinces.open-api.vn/api/p/')
    const data = await response.json()
    provinces.value = data
  } catch (error) {
    console.error('Error loading provinces:', error)

    provinces.value = [
      { code: '92', name: 'Thành phố Cần Thơ' },
      { code: '79', name: 'Thành phố Hồ Chí Minh' },
      { code: '01', name: 'Thành phố Hà Nội' },
      { code: '48', name: 'Thành phố Đà Nẵng' }
    ]
  }
}


const onProvinceChange = async () => {
  districts.value = []
  wards.value = []
  formData.district = null
  formData.ward = null
  
  if (!formData.province) return
  
  try {
    const response = await fetch(`https://provinces.open-api.vn/api/p/${formData.province.code}?depth=2`)
    const data = await response.json()
    districts.value = data.districts || []
  } catch (error) {
    console.error('Error loading districts:', error)
  }
}


const onDistrictChange = async () => {
  wards.value = []
  formData.ward = null
  
  if (!formData.district) return
  
  try {
    const response = await fetch(`https://provinces.open-api.vn/api/d/${formData.district.code}?depth=2`)
    const data = await response.json()
    wards.value = data.wards || []
  } catch (error) {
    console.error('Error loading wards:', error)
  }
}

const handleSubmit = async () => {
  loading.value = true
  
  try {
    // Simulate API call
    await new Promise(resolve => setTimeout(resolve, 1500))
    
    const updatedPatient = {
      ...formData,
      birthDate: `${formData.birthDay}/${formData.birthMonth}/${formData.birthYear}`,
      fullAddress: `${formData.address}, ${formData.ward?.name || ''}, ${formData.district?.name || ''}, ${formData.province?.name || ''}`
    }
    
    emit('update', updatedPatient)
  } catch (error) {
    console.error('Error updating patient:', error)
  } finally {
    loading.value = false
  }
}

onMounted(() => {
  loadProvinces()
  

  if (props.patient) {
    Object.assign(formData, props.patient)
  }
})
</script>

<style scoped>
.edit-patient-form {
  max-width: 1000px;
  margin: 0 auto;
}

.page-header {
  margin-bottom: 24px;
}

.breadcrumb {
  display: flex;
  align-items: center;
  gap: 8px;
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

.form-container {
  background: white;
  border-radius: 12px;
  padding: 32px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  border: 1px solid #e2e8f0;
}

.info-notice {
  background: #dbeafe;
  color: #1e40af;
  padding: 12px 16px;
  border-radius: 8px;
  margin-bottom: 32px;
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 14px;
}

.patient-form {
  display: flex;
  flex-direction: column;
  gap: 32px;
}

.form-section {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.section-header {
  margin-bottom: 8px;
}

.required-indicator {
  color: #ef4444;
  font-size: 14px;
  font-weight: 500;
}

.section-title {
  font-size: 18px;
  font-weight: 600;
  color: #1e293b;
  margin: 0;
  padding-bottom: 8px;
  border-bottom: 2px solid #e2e8f0;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 24px;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.form-label {
  font-weight: 500;
  color: #374151;
  font-size: 14px;
}

.required {
  color: #ef4444;
}

.form-input,
.form-select {
  padding: 12px 16px;
  border: 1px solid #d1d5db;
  border-radius: 8px;
  font-size: 14px;
  color: #374151;
  background: white;
  transition: border-color 0.2s, box-shadow 0.2s;
}

.form-input:focus,
.form-select:focus {
  outline: none;
  border-color: #22d3ee;
  box-shadow: 0 0 0 3px rgba(34, 211, 238, 0.1);
}

.form-select:disabled {
  background: #f9fafb;
  color: #9ca3af;
  cursor: not-allowed;
}

.date-inputs {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 12px;
}

.address-note {
  font-size: 12px;
  color: #ef4444;
  font-style: italic;
  margin-top: -4px;
}

.form-actions {
  display: flex;
  justify-content: flex-end;
  padding-top: 24px;
  border-top: 1px solid #e2e8f0;
}

.btn {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 12px 24px;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s;
}

.btn:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

.btn-primary {
  background: #22d3ee;
  color: white;
}

.btn-primary:hover:not(:disabled) {
  background: #06b6d4;
  transform: translateY(-1px);
}

@media (max-width: 768px) {
  .form-container {
    padding: 20px;
  }
  
  .form-row {
    grid-template-columns: 1fr;
    gap: 16px;
  }
  
  .date-inputs {
    grid-template-columns: 1fr 1fr 1fr;
  }
}
</style>