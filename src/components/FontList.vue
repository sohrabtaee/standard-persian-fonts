<template>
  <ul class="font-list">
    <li
      v-for="font in fonts"
      :key="font.nameEn"
      :class="font.nameEn.replace(/\s+/g, '-').toLowerCase()"
      class="panel"
    >
      <div class="panel-heading">
        <h3 class="panel-title">{{ font.nameFa }} ({{ font.nameEn }})</h3>
        <h3 class="panel-title" v-if="font.url">
          <a :href="font.url" target="_blank">صفحه سازنده</a>
        </h3>
      </div>
      <div class="panel-body">
        <div
          v-for="weight in font.weights"
          :key="weight"
          :class="weight"
          class="demo"
        >
          <p>
            یکی از مشکلاتی که در وب فارسی با آن مواجه هستیم، محدودیت فونت است.
            متاسفانه در وب فارسی ما محدود به سه فونت هستیم که بر روی تمامی سیستم
            ها نصب شده است. فونت arial, Tahoma و mono-type تنها فونتهایی هستند
            که می‌توانیم از آنها استفاده کنیم در حالی که برای زبان انگلیسی حداقل
            نزدیک به 10 فونت در دسترس است.
          </p>
          <div class="numbers">
            <p>1 2 3 4 5 6 7 8 9 0 - = ! @ # $ % ^ & * ( ) _ +</p>
            <p>۱ ۲ ۳ ۴ ۵ ۶ ۷ ۸ ۹ ۰ - = ! ٬ ٫ ریال ٪ × ، * ) ( ـ +</p>
          </div>
        </div>
      </div>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'font-list',
  props: {
    fonts: Array,
  },
}
</script>
