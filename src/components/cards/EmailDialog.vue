<script setup>
import { ref, defineProps, defineEmits } from 'vue'

defineProps({
  isOpen: Boolean,
  recipientEmail: String
})

const emit = defineEmits(['close'])

const form = ref({
  name: '',
  senderEmail: '',
  subject: '',
  message: ''
})

const isSending = ref(false)
const isSuccess = ref(false)

const handleSend = () => {
  isSending.value = true

  // จำลองการส่งอีเมลอัตโนมัติ (ใช้เวลา 1.2 วินาที)
  setTimeout(() => {
    isSending.value = false
    isSuccess.value = true

    // แสดงหน้าส่งสำเร็จ 1.8 วินาที แล้วปิด Dialog อัตโนมัติ
    setTimeout(() => {
      resetAndClose()
    }, 1800)
  }, 1200)
}

const resetAndClose = () => {
  form.value = { name: '', senderEmail: '', subject: '', message: '' }
  isSuccess.value = false
  isSending.value = false
  emit('close')
}
</script>

<template>
  <!-- แสดงทับบนหน้า Home เมื่อ isOpen เป็น true -->
  <div v-if="isOpen" class="dialog-overlay" @click.self="resetAndClose">
    <div class="dialog-box">
      <!-- หน้าจอแจ้งเตือนเมื่อส่งสำเร็จ -->
      <div v-if="isSuccess" class="success-state">
        <div class="check-icon">✅</div>
        <h3>ส่งอีเมลเรียบร้อยแล้ว!</h3>
        <p>ข้อความของคุณถูกส่งไปยัง {{ recipientEmail }} เรียบร้อย</p>
      </div>

      <!-- หน้าจอฟอร์มกรอกอีเมลปกติ -->
      <template v-else>
        <div class="dialog-header">
          <div>
            <h3 class="dialog-title">✉️ ส่งข้อความด่วน</h3>
            <p class="dialog-sub">ถึง: <span>{{ recipientEmail }}</span></p>
          </div>
          <button type="button" class="close-btn" @click="resetAndClose">✕</button>
        </div>

        <form @submit.prevent="handleSend" class="dialog-form">
          <div class="form-row">
            <div class="input-field">
              <label>ชื่อของคุณ</label>
              <input v-model="form.name" type="text" placeholder="ระบุชื่อ..." required />
            </div>
            <div class="input-field">
              <label>อีเมลติดต่อกลับ</label>
              <input v-model="form.senderEmail" type="email" placeholder="name@example.com" required />
            </div>
          </div>

          <div class="input-field">
            <label>หัวข้อเรื่อง</label>
            <input v-model="form.subject" type="text" placeholder="เช่น ติดต่องาน / พูดคุยแลกเปลี่ยน" required />
          </div>

          <div class="input-field">
            <label>รายละเอียดข้อความ</label>
            <textarea v-model="form.message" rows="4" placeholder="พิมพ์ข้อความของคุณที่นี่..." required></textarea>
          </div>

          <div class="dialog-actions">
            <button type="button" class="btn-cancel" @click="resetAndClose">ยกเลิก</button>
            <button type="submit" class="btn-send" :disabled="isSending">
              <span v-if="isSending">กำลังส่งข้อความ...</span>
              <span v-else>ส่งอีเมลทันที 🚀</span>
            </button>
          </div>
        </form>
      </template>
    </div>
  </div>
</template>

<style scoped>
.dialog-overlay {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.75);
  backdrop-filter: blur(8px);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9999;
  padding: 1rem;
  animation: fadeIn 0.2s ease;
}

.dialog-box {
  background: #18181b;
  border: 1px solid rgba(255, 255, 255, 0.14);
  border-radius: 24px;
  width: 100%;
  max-width: 480px;
  padding: 1.75rem;
  color: #f4f4f5;
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.7);
  animation: popIn 0.25s cubic-bezier(0.16, 1, 0.3, 1);
}

.dialog-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 1.25rem;
}

.dialog-title {
  margin: 0 0 0.25rem 0;
  font-size: 1.2rem;
  font-weight: 700;
}

.dialog-sub {
  margin: 0;
  font-size: 0.85rem;
  color: #a1a1aa;
}

.dialog-sub span {
  color: #4ade80;
  font-weight: 500;
}

.close-btn {
  background: rgba(255, 255, 255, 0.06);
  border: none;
  color: #a1a1aa;
  width: 32px;
  height: 32px;
  border-radius: 50%;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s;
}

.close-btn:hover {
  background: rgba(239, 68, 68, 0.2);
  color: #f87171;
}

.dialog-form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.85rem;
}

.input-field {
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
}

.input-field label {
  font-size: 0.8rem;
  color: #d4d4d8;
  font-weight: 500;
}

.input-field input,
.input-field textarea {
  background: #09090b;
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 12px;
  padding: 0.7rem 0.9rem;
  color: #ffffff;
  font-size: 0.9rem;
  font-family: inherit;
  outline: none;
  transition: border-color 0.2s;
}

.input-field input:focus,
.input-field textarea:focus {
  border-color: #22c55e;
}

.dialog-actions {
  display: flex;
  justify-content: flex-end;
  gap: 0.75rem;
  margin-top: 0.5rem;
}

.btn-cancel {
  background: transparent;
  border: 1px solid rgba(255, 255, 255, 0.15);
  color: #a1a1aa;
  padding: 0.65rem 1.15rem;
  border-radius: 12px;
  cursor: pointer;
  font-weight: 500;
}

.btn-cancel:hover {
  background: rgba(255, 255, 255, 0.06);
  color: #ffffff;
}

.btn-send {
  background: #22c55e;
  border: none;
  color: #ffffff;
  padding: 0.65rem 1.35rem;
  border-radius: 12px;
  cursor: pointer;
  font-weight: 600;
  transition: background 0.2s;
}

.btn-send:hover:not(:disabled) {
  background: #16a34a;
}

.btn-send:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

/* สถานะเมื่อส่งสำเร็จ */
.success-state {
  text-align: center;
  padding: 2rem 1rem;
}

.check-icon {
  font-size: 3rem;
  margin-bottom: 0.75rem;
}

.success-state h3 {
  margin: 0 0 0.5rem 0;
  color: #4ade80;
}

.success-state p {
  margin: 0;
  color: #a1a1aa;
  font-size: 0.9rem;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes popIn {
  from { transform: scale(0.95) translateY(10px); opacity: 0; }
  to { transform: scale(1) translateY(0); opacity: 1; }
}

@media (max-width: 520px) {
  .form-row {
    grid-template-columns: 1fr;
  }
}
</style>