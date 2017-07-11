<template>
    <div id="app">
        <div class="container" v-cloak>
            <div class="row">
                <div class="col-sm-7 col-md-8 col-lg-9">
                    <div class="panel panel-default" v-for="font in filteredFonts" :key="font.nameEn"
                         :class="font.nameEn | slug">
                        <div class="panel-heading clearfix">
                            <h3 class="pull-right panel-title">{{font.nameFa}}</h3>
                            <h3 class="pull-left panel-title">{{font.nameEn}}</h3>
                        </div>
                        <div class="row">
                            <div :class="font.weights.length > 1 ? 'col-lg-6' : 'col-xs-12'"
                                 v-for="weight in font.weights">
                                <div class="panel-body" :class="weight">
                                    <p>یکی از مشکلاتی که در وب فارسی با آن مواجه هستیم، محدودیت فونت است. متاسفانه
                                        در وب
                                        فارسی ما
                                        محدود به سه فونت هستیم
                                        که بر روی تمامی سیستم ها نصب شده است. فونت arial, Tahoma و mono-type تنها
                                        فونتهایی هستند که
                                        می‌توانیم از آنها
                                        استفاده کنیم در حالی که برای زبان انگلیسی حداقل نزدیک به 10 فونت در دسترس
                                        است.</p>
                                    <div class="numbers">
                                        <p>1 2 3 4 5 6 7 8 9 0 - = ! @ # $ % ^ & * ( ) _ +</p>
                                        <p>۱ ۲ ۳ ۴ ۵ ۶ ۷ ۸ ۹ ۰ - = ! ٬ ٫ ریال ٪ × ، * ) ( ـ +</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="col-sm-5 col-md-4 col-lg-3">
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h4 class="panel-title">فیلتر</h4>
                        </div>
                        <div class="panel-body">
                            <label>بر اساس نوع فونت</label>
                            <div class="checkbox">
                                <label>
                                    <input type="checkbox" value="sans-serif"
                                           @click="filter" v-model="filters.types"> لبه گرد (sans-serif)
                                </label>
                            </div>
                            <div class="checkbox">
                                <label>
                                    <input type="checkbox" value="serif"
                                           @click="filter" v-model="filters.types"> لبه تیز (serif)
                                </label>
                            </div>
                        </div>
                        <div class="panel-body">
                            <label>بر اساس وزن فونت</label>
                            <div class="checkbox" v-for="weight in weights">
                                <label>
                                    <input type="checkbox" :value="weight | slug"
                                           @click="filter" v-model="filters.weights"> {{weight}}
                                </label>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

    import Includes from 'lodash/includes';
    import Difference from 'lodash/difference';

    export default {
        name: 'app',
        data () {
            return {
                weights: ['Ultra light', 'Light', 'Normal', 'Medium', 'Bold'],
                filters: {
                    types: [],
                    weights: []
                },
                filteredFonts: [],
                fonts: [
                    {
                        nameFa: 'بی‌بی‌سی نسیم',
                        nameEn: 'BBC Nassim',
                        type: 'serif',
                        weights: ['normal', 'bold']
                    },
                    {
                        nameFa: 'دروید نسخ',
                        nameEn: 'Droid Naskh',
                        type: 'serif',
                        weights: ['normal', 'bold']
                    },
                    {
                        nameFa: 'گندم',
                        nameEn: 'Gandom',
                        type: 'serif',
                        weights: ['normal', 'bold']
                    },
                    {
                        nameFa: 'گنج نامه سنس',
                        nameEn: 'Ganj Nameh Sans',
                        type: 'sans-serif',
                        weights: ['normal']
                    },
                    {
                        nameFa: 'ایران سنس',
                        nameEn: 'Iran Sans',
                        type: 'sans-serif',
                        weights: ['ultra-light', 'light', 'normal', 'medium', 'bold']
                    },
                    {
                        nameFa: 'میلاد آزاد',
                        nameEn: 'Milad Azad',
                        type: 'serif',
                        weights: ['normal']
                    },
                    {
                        nameFa: 'پرستو',
                        nameEn: 'Parastoo',
                        type: 'serif',
                        weights: ['normal', 'bold']
                    },
                    {
                        nameFa: 'ساحل',
                        nameEn: 'Sahel',
                        type: 'sans-serif',
                        weights: ['normal', 'bold']
                    },
                    {
                        nameFa: 'صمیم',
                        nameEn: 'Samim',
                        type: 'sans-serif',
                        weights: ['normal', 'bold']
                    },
                    {
                        nameFa: 'شبنم',
                        nameEn: 'Shabnam',
                        type: 'sans-serif',
                        weights: ['normal', 'bold']
                    },
                    {
                        nameFa: 'وزیر',
                        nameEn: 'Vazir',
                        type: 'sans-serif',
                        weights: ['ultra-light', 'normal', 'medium', 'bold']
                    },
                    {
                        nameFa: 'ویژه آزاد',
                        nameEn: 'Vizheh Azad',
                        type: 'serif',
                        weights: ['normal']
                    },
                    {
                        nameFa: 'زیرو سنس',
                        nameEn: 'Xero Sans',
                        type: 'sans-serif',
                        weights: ['normal']
                    }
                ]
            }
        },
        mounted() {
            this.filteredFonts = this.fonts;
        },
        methods: {
            filter () {
                this.filteredFonts = this.fonts;
                if (this.filters.types.length) {
                    this.filteredFonts = this.filteredFonts.filter(font => Includes(this.filters.types, font.type));
                }
                if (this.filters.weights.length) {
                    this.filteredFonts = this.filteredFonts.filter(font => !Difference(this.filters.weights, font.weights).length);
                }
            }
        },
        filters: {
            slug(value) {
                return value.replace(/\s+/g, '-').toLowerCase();
            }
        }
    }

</script>

<style>

    html {
        font-size: 16px;
    }

    body {
        direction: rtl;
        font-family: IRANSans, sans-serif;
        font-size: 1rem;
    }

    .numbers {
        text-align: center;
        direction: ltr;
    }

    [v-cloak] {
        display: none;
    }

    #app {
        padding-top: 3em;
    }

    .panel {
        margin-bottom: 3em;
    }

    .ultra-light {
        font-weight: 200;
    }

    .light {
        font-weight: 300;
    }

    .medium {
        font-weight: 500;
    }

    .bold {
        font-weight: 700;
    }

    .italic {
        font-style: italic;
    }

</style>
