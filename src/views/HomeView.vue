<script setup>
import { ref } from 'vue'
import BentoCard from '../components/BentoCard.vue'
import HeroCard from '../components/cards/HeroCard.vue'
import MapCard from '../components/cards/MapCard.vue'
import TechStackCard from '../components/cards/TechStackCard.vue'
import SocialCard from '../components/cards/SocialCard.vue'
import EducationCard from '../components/cards/EducationCard.vue'
import StrengthsCard from '../components/cards/StrengthsCard.vue'
import HobbiesCard from '../components/cards/HobbiesCard.vue'
import PreferencesCard from '../components/cards/PreferencesCard.vue'
import EmailDialog from '../components/cards/EmailDialog.vue'

const profile = ref({
  name: "มานพ เวียนเทียน",
  nickname: "น๊อต",
  role: "Software Engineer",
  location: "บริษัท อินเทอร์เน็ตประเทศไทย จำกัด (มหาชน) สาขาขอนแก่น",
  bio: "Software Engineer หน้าใหม่ไฟแรงส์ มีใจรักในการเขียนโค้ด (มั้งนะ) พร้อมเรียนรู้ ลองของใหม่ และอัปสกิลตัวเองอยู่ตลอดเวลา",
  
  education: {
    degree: "วิทยาศาสตรบัณฑิต",
    major: "สาขาวิชาเทคโนโลยีสารสนเทศ (Information Technology)",
    university: "มหาวิทยาลัยขอนแก่น",
    year: "ปีที่จบการศึกษา 2026"
  },

  skills: [
    "Vue.js", "React", "Node.js", "Python",
    "Tailwind CSS", "MongoDB", "SQL", "Git"
  ],

  strengths: [
    "สนใจเทคโนโลยีใหม่ๆ",
    "มนุษย์สัมพันธ์ดี",
    "รับฟังความคิดเห็นที่แตกต่างเสมอ"
  ],
  weaknesses: [
    "ทำงานจนลืมดูเวลา",
    "นอนไม่หลับจนกว่าจะแก้บั๊คได้",
    "ไม่มีประสบการณ์กับโปรเจคใหญ่"
  ],
  hobbies: [
    "🎮 เล่นเกมวางแผน & FPS",
    "🏋️‍♂️ ออกกำลังกาย",
    "📚 อ่านนิยายสืบสวนสอบสวน",
    "😒 ดูแมนยูแพ้"
  ],
  favoriteTeams: [
    "Manchester United 😡"
  ],

  likes: [
    "ก๋วยเตี๋ยวคุณแม่",
    "นอนดึก ตื่นสายได้",
    "ตี๋น้อย บุฟเฟต์",
    "แมนยูชนะ"
  ],
  dislikes: [
    "ตื่นเช้า",
    "ลงแรงค์แล้วไฟดับ",
    "อากาศร้อนเกิ้น",
    "แมนยูแพ้"
  ],

  socials: {
    github: "https://github.com/manongmanop",
    email: "manotvt14@gmail.com"
  }
})
const showEmailDialog = ref(false)
</script>

<template>
  <div class="page-container">
    <div class="eldin-grid">
      <!-- แถว 1-2: Bio (2x2) + Location (1x1) + Social (1x1) -->
      <BentoCard class="col-span-2 row-span-2">
        <HeroCard 
          :name="profile.name" 
          :nickname="profile.nickname" 
          :role="profile.role" 
          :bio="profile.bio" 
        />
      </BentoCard>

      <BentoCard class="col-span-1">
        <MapCard :location="profile.location" />
      </BentoCard>

      <BentoCard class="col-span-1">
        <SocialCard 
        :socials="profile.socials" 
        @open-email="showEmailDialog = true"
        />
      </BentoCard>

      <!-- แถว 3: การศึกษา (1 ช่อง)  Tech Stack (2 ช่อง) -->
      <BentoCard class="col-span-1">
        <EducationCard :education="profile.education" />
      </BentoCard>

      <BentoCard class="col-span-2">
        <TechStackCard :skills="profile.skills" />
      </BentoCard>


      <!-- แถว 4: งานอดิเรกและทีมที่เชียร์ (2 ช่อง) + จุดแข็ง (1 ช่อง) -->
      <BentoCard class="col-span-1">
        <HobbiesCard 
          :hobbies="profile.hobbies" 
          :favoriteTeams="profile.favoriteTeams" 
        />
      </BentoCard>

      <BentoCard class="col-span-2">
        <StrengthsCard 
        :strengths="profile.strengths"
        :weaknesses="profile.weaknesses"
         />
      </BentoCard>

      <!-- แถว 5: สิ่งที่ชอบ vs ไม่ชอบ (กว้าง 3 ช่องเต็มแถว หรือ 2 ช่องตามชอบ) -->
      <BentoCard class="col-span-3">
        <PreferencesCard 
          :likes="profile.likes" 
          :dislikes="profile.dislikes" 
        />
      </BentoCard>
      <EmailDialog 
      :isOpen="showEmailDialog" 
      :recipientEmail="profile.socials.email"
      @close="showEmailDialog = false"
    />
    </div>
  </div>
</template>

<style scoped>
.page-container {
  width: 100%;
  max-width: 960px;
  margin: 0 auto;
}

.eldin-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: auto;
  gap: 1.25rem;
}

.col-span-1 { grid-column: span 1; }
.col-span-2 { grid-column: span 2; }
.col-span-3 { grid-column: span 3; }
.row-span-2 { grid-row: span 2; }

@media (max-width: 820px) {
  .eldin-grid {
    grid-template-columns: 1fr;
  }
  .col-span-1,
  .col-span-2,
  .col-span-3,
  .row-span-2 {
    grid-column: span 1;
    grid-row: span 1;
  }
}
</style>