<template>
  <div class="container">
    <h2>ระบบตัดเกรด</h2>

    <div class="form-group">
        <label>
            กรอกคะแนน
        </label>
        <input 
        type="text"
        v-model="score"
        placeholder="กรอกคะแนน 0-100"
        >

        <button @click="calculateGrade">
            คำนวณเกรด
        </button>
    </div>

    <p v-if="error" class="error">
      {{ error }}
    </p>

    <div v-if="grade !== null" class="result">
      <h3>คะแนน: {{ score }}</h3>
      <h2>เกรดที่ได้รับ: {{ grade }}</h2>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return {
      score: "",
      grade: null,
      error: ""
    };
  },
  methods: {
    calculateGrade() {
      this.error = "";
      this.grade = null;

      if (this.score.trim() === ""){
        this.error = "กรุณากรอกคะแนน";
        return;
      }

      const scoreNumber = Number(this.score);
      const pattern =  /^(100|[1-9]?[0-9])$/;

      if (!pattern.test(this.score.trim())) {
        this.error = "กรุณากรอกเฉพาะตัวเลข 0-100 เท่านั้น";
        return;
      }

      if (!Number.isFinite(scoreNumber)) {
        this.error = "กรุณากรอกตัวเลขเท่านั้น";
        return;
      }

      if (scoreNumber < 0 || scoreNumber > 100) {
        this.error = "คะแนนต้องอยู่ระหว่าง 0-100";
        return;
      }

      if (scoreNumber >= 80) {
        this.grade = "A";
      } else if (scoreNumber >= 70) {
        this.grade = "B";
      } else if (scoreNumber >= 60) {
        this.grade = "C";
    }else if (scoreNumber >= 50) {
        this.grade = "D";
  }else {
        this.grade = "F";
  }
    }
  }
};
</script>

<style>
.container {
  max-width: 400px;
  margin: 50px auto;
  padding: 25px;
  text-align: center;
  border: 1px solid #ddd;
  border-radius: 12px;
  font-family: Arial, Helvetica, sans-serif;
}

.form-group{
  display: flex;
  flex-direction: column;
  gap: 12px;
  text-align: left;
  }
input {
  padding: 12px;
  border: 1px solid #aaa;
  border-radius: 6px;
  font-size: 16px;
  color: white;
}

button {
  padding: 12px;
  background: #2563eb;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}

button:hover {
  background: #1d4ed8;
}

.error {
  color: red;
  margin-top: 15px;
  background: #fee2e2;
  border-radius: 8px;
  color: #166534;
}
</style>