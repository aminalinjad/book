<template>
  <div dir="rtl" class="site-shell" :class="{ dark: isDark }">
    <div class="ambient ambient-one" aria-hidden="true"></div>
    <div class="ambient ambient-two" aria-hidden="true"></div>
    <header class="header container">
      <a class="brand" href="#top" aria-label="بازگشت به بالای صفحه">
        <span class="brand-mark" aria-hidden="true"><span></span><span></span><span></span></span>
        <span><strong>ما فکر نمی‌کنیم، تصمیم می‌گیریم!</strong><small>کتابی از میثم کیهانی</small></span>
      </a>
      <nav class="nav" aria-label="دسترسی سریع"><a href="#about">معرفی کتاب</a><a href="#details" @click="activeTab = 1">مشخصات</a><a href="#details" @click="activeTab = 2">نویسنده</a></nav>
      <button class="theme-toggle" type="button" :aria-label="isDark ? 'فعال‌کردن حالت روشن' : 'فعال‌کردن حالت تیره'" @click="toggleTheme">
        <svg v-if="!isDark" viewBox="0 0 24 24" aria-hidden="true"><path d="M12 3V1m0 22v-2M3 12H1m22 0h-2M4.22 4.22 2.8 2.8m18.4 18.4-1.42-1.42M19.78 4.22 21.2 2.8M2.8 21.2l1.42-1.42M17 12a5 5 0 1 1-10 0 5 5 0 0 1 10 0Z"/></svg>
        <svg v-else viewBox="0 0 24 24" aria-hidden="true"><path d="M21 15.1A9 9 0 1 1 8.9 3a7 7 0 0 0 12.1 12.1Z"/></svg>
        <span>{{ isDark ? 'روشن' : 'تیره' }}</span>
      </button>
    </header>

    <main id="top" class="container">
      <section class="hero">
        <div class="hero-copy">
          <div class="eyebrow"><span class="eyebrow-dot"></span>کتاب تازه‌ای درباره تصمیم‌گیری و رفتار انسان</div>
          <p class="overline">نوشته‌ی میثم کیهانی</p>
          <h1>ما فکر نمی‌کنیم،<br><em>تصمیم می‌گیریم!</em></h1>
          <p class="lead">در تقاطع نئو مارکتینگ، روان‌شناسی تصمیم‌گیری و رفتار مصرف‌کننده؛ درباره‌ی اینکه انسان‌ها چگونه انتخاب می‌کنند، چه چیزی انتخاب‌هایشان را شکل می‌دهد و چگونه می‌توان بر این انتخاب‌ها اثر گذاشت.</p>
          <div class="price-card" aria-label="قیمت نسخه چاپی کتاب">
            <div class="price-block"><div><span class="price-label">قیمت نسخه چاپی</span><strong>۹۸۰,۰۰۰<small>تومان</small></strong></div></div>
          </div>
        </div>
        <div class="book-stage" aria-label="تصویر جلد کتاب ما فکر نمی‌کنیم، تصمیم می‌گیریم">
          <div class="orbit orbit-one"></div><div class="orbit orbit-two"></div>
          <div class="floating-note note-top">درباره رفتار انسان <span>✦</span></div>
          <div class="book-wrap"><img src="/images/maysam-book.png" alt="جلد کتاب ما فکر نمی‌کنیم، تصمیم می‌گیریم نوشته میثم کیهانی" width="1230" height="1278"></div>
          <div class="book-shadow"></div><div class="floating-note note-bottom"><span class="status-dot"></span> نوشته‌ی میثم کیهانی</div>
        </div>
      </section>

      <section class="trust-strip" aria-label="اطلاعات کوتاه کتاب">
        <article><span class="feature-icon"><svg viewBox="0 0 24 24"><path d="M4 4.5A2.5 2.5 0 0 1 6.5 2H20v17H6.5A2.5 2.5 0 0 0 4 21.5z"/><path d="M4 4.5v17"/></svg></span><div><strong>۲۶۱ صفحه</strong><small>تعداد صفحات کتاب</small></div></article>
        <article><span class="feature-icon"><svg viewBox="0 0 24 24"><path d="m12 2 3 3 4 .5.5 4 2.5 2.5-2.5 3 .5 4-4 .5-3 3-3-3-4-.5-.5-4L2 12l2.5-2.5-.5-4 4-.5 3-3Z"/><path d="m8.5 12 2 2 5-5"/></svg></span><div><strong>شابک</strong><small>۰-۳۹۶-۴۵۱-۶۲۲-۹۷۸</small></div></article>
        <article><span class="feature-icon"><svg viewBox="0 0 24 24"><path d="M12 21a9 9 0 1 0 0-18 9 9 0 0 0 0 18Z"/><path d="M8 12h8M12 8v8"/></svg></span><div><strong>شناسه مجوز</strong><small>۱۱۱۱۲۹۱-۱۲۲۸۶۱-۹</small></div></article>
      </section>

      <section id="about" class="details-section">
        <div class="section-heading"><p>یک نگاه نزدیک‌تر</p><h2>درباره کتاب<br>و نویسنده</h2></div>
        <div class="details-panel" id="details">
          <div class="tabs" role="tablist" aria-label="اطلاعات کتاب">
            <button v-for="(tab, index) in tabs" :key="tab.title" type="button" role="tab" :aria-selected="activeTab === index" :class="{ active: activeTab === index }" @click="activeTab = index">{{ tab.title }}</button>
          </div>
          <div class="tab-content">
            <Transition name="tab-fade" mode="out-in">
              <div :key="activeTab">
                <template v-if="activeTab === 0">
                  <p>در روزهایی نوشتن این کتاب را آغاز کردم که صدای جنگ، دوباره به خاورمیانه برگشته بود، روزهایی که مردم بیشتر از همیشه نگران بودند، نگران امنیت، آینده، پول، خانواده و فردا.
                    در همان روزها، چیزی ذهنم را بیشتر از خود جنگ ایران و آمریکا و اسرائیل درگیر کرده بود،
                    رفتار انسان‌ها.
                    شاید عجیب باشد که انسان، وسط روزهایی پر از اضطراب و ابهام، تصمیم به نوشتن کتاب بگیرد.
                    اما حقیقت این است که دقیقاً در همان روزها، بیشتر از هر زمان دیگری، رفتار واقعی انسان‌ها را دیدم.
                    دیدم که ترس چگونه تصمیم می‌سازد.
                    دیدم که امید چگونه منطق را تغییر می‌دهد.
                    دیدم که آدم‌ها چطور برای آرام شدن، خرید می‌کنند، ذخیره می‌کنند، فرار می‌کنند، انکار می‌کنند یا حتی وانمود می‌کنند همه‌چیز عادی است.</p>
                  <p>ما فکر می‌کنیم انتخاب‌هایمان حاصل فکر کردن و تصمیم‌گیری آگاهانه است؛ اما واقعیت پیچیده‌تر از این است.</p>
                  <p>ما هر روز انتخاب می‌کنیم؛ چه چیزی بخریم، به چه کسی اعتماد کنیم، روی چه چیزی کلیک کنیم و حتی برای چه چیزی پول بیشتری بپردازیم. اما پشت بسیاری از این انتخاب‌ها، سازوکارهایی وجود دارد که اغلب از آن‌ها آگاه نیستیم.</p>
                  <p>ما فکر نمی‌کنیم، تصمیم می‌گیریم به سراغ همین بخش پنهان رفتار انسان می‌رود؛ جایی که نئو مارکتینگ، روان‌شناسی تصمیم‌گیری و رفتار مصرف‌کننده به هم می‌رسند. این کتاب کمک می‌کند بفهمیم چرا آدم‌ها آن‌طور که فکر می‌کنیم انتخاب نمی‌کنند، چه عواملی تصمیم‌هایشان را شکل می‌دهد و چگونه می‌توان این شناخت را در بازاریابی و کسب‌وکار به کار گرفت.</p>
                  <p>اما این کتاب صرفا یک کتاب آکادمیک یا مجموعه‌ای از نظریه‌ها نیست. این کتاب حاصل بیش از ۲۰ سال تجربه‌ی نویسنده در حوزه‌ی بازاریابی و مواجهه با مسئله‌های واقعی کسب‌وکار است؛ تجربه‌ای که در کنار مفاهیم و یافته‌های علمی، با مثال‌های واقعی از کمپین‌های بازاریابی، تصمیم‌های برندها و رفتار مصرف‌کنندگان روایت شده است.</p>
                  <p>این کتاب در روزهایی نوشته شد که جنگ میان ایران، اسرائیل و آمریکا جریان داشت؛ روزهایی پر از ابهام، اضطراب و تصمیم‌های لحظه‌ای. شاید همین فضای متفاوت، بیش از همیشه این سؤال را پررنگ می‌کرد که انسان‌ها در شرایط عادی و بحرانی چگونه تصمیم می‌گیرند و چه عواملی انتخاب‌هایشان را شکل می‌دهد.</p>
                  <p>اگر با بازاریابی، برند، محصول، تجربه مشتری یا تصمیم‌های کسب‌وکار سروکار دارید، این کتاب قرار نیست فقط چیزی به دانسته‌هایتان اضافه کند؛ قرار است نگاهتان به رفتار آدم‌ها و تصمیم‌هایی که می‌گیرند را تغییر دهد.</p>
                </template>
                <template v-else-if="activeTab === 1"><dl class="spec-grid">
                  <div><dt>نویسنده</dt><dd>میثم کیهانی</dd></div><div><dt>تعداد صفحات</dt><dd>۲۶۱ صفحه</dd></div>
                  <div><dt>شابک</dt><dd>۰-۳۹۶-۴۵۱-۶۲۲-۹۷۸</dd></div><div><dt>شناسه مجوز</dt><dd>۱۱۱۱۲۹۱-۱۲۲۸۶۱-۹</dd></div>

                  <div><dt>ناشر</dt><dd>دیده بان قلم فرتاک</dd></div><div><dt>شماره کتابشناسی ملی</dt><dd>۱۰۶۴۱۵۲۲</dd></div>
                </dl></template>
                <template v-else>
                  <p>میثم کیهانی فعالیت حرفه‌ای خود را از سال ۱۳۸۳ با راه‌اندازی ناربلا، یکی از فروشگاه‌های اینترنتی نسل اول ایران، آغاز کرد. ناربلا یک فروشگاه تخصصی لوازم خانگی بود؛ در دورانی که هنوز مفهوم خرید اینترنتی برای بسیاری از مردم و حتی کسب‌وکارها ناشناخته بود. ناربلا در آن سال‌ها به بیش از ۸۰ فاکتور فروش آنلاین در روز رسید؛ تجربه‌ای که مسیر حرفه‌ای او را به دنیای دیجیتال، بازاریابی و رفتار مصرف‌کننده پیوند زد.</p>
                  <p>کیهانی در ادامه به‌عنوان مدیر دیجیتال مارکتینگ، مدیر بازاریابی و CMO در مجموعه‌هایی مانند پارس آنلاین، سفرمارکت و اوزون فعالیت کرده است؛ از بزرگ‌ترین ارائه‌دهندگان اینترنت ایران تا نخستین مارکت‌پلیس گردشگری ایران و یکی از نخستین PayFacهای ایران.</p>
                  <p>او همچنین در طول این سال‌ها با برندهایی مانند مزمز، HP، کاله، ترنج و مجموعه‌های مختلف دیگر به‌عنوان مشاور و متخصص بازاریابی همکاری داشته و در طراحی و اجرای کمپین‌های متعددی نقش داشته است؛ از کمپین «از قافله جا نمونی» و استفاده از اینفلوئنسرها در بیلبوردهای شهری، تا «خوب بودن مهم‌تره» و «جمعه نارنجی»؛ نخستین کمپین بلک‌فرایدی در صنعت گردشگری که به رکورد فروش تور در یک روز در ایران رسید.</p>
                  <p>اما مسیر حرفه‌ای او فقط به ایده‌های خلاقانه محدود نمی‌شود. ترکیب خلاقیت با داده، شناخت رفتار مخاطب و استفاده از شواهد برای تصمیم‌گیری بازاریابی، بخش مهمی از نگاه او به مارکتینگ است؛ نگاهی که تلاش می‌کند فاصله میان آنچه مردم درباره‌ی تصمیم‌هایشان می‌گویند و آنچه واقعاً انجام می‌دهند را کشف کند.</p>
                  <p>«ما فکر نمی‌کنیم، تصمیم می‌گیریم» حاصل همین مسیر است؛ بیش از دو دهه تجربه در مواجهه با آدم‌ها، برندها، داده‌ها، کمپین‌ها و تصمیم‌هایی که پشت هر انتخاب قرار دارند.</p>
                </template>
              </div>
            </Transition>
          </div>
        </div>
      </section>
    </main>
    <footer class="footer container">
      <a class="brand compact" href="#top"><span class="brand-mark"><span></span><span></span><span></span></span><strong>ما فکر نمی‌کنیم، تصمیم می‌گیریم!</strong></a>
      <p>نوشته‌ی میثم کیهانی</p>
    </footer>
  </div>
</template>

<script setup>
const activeTab = ref(0)
const isDark = ref(false)
const tabs = [{ title: 'درباره کتاب' }, { title: 'مشخصات' }, { title: 'نویسنده' }]
const toggleTheme = () => {
  isDark.value = !isDark.value
  localStorage.setItem('book-theme', isDark.value ? 'dark' : 'light')
}
onMounted(() => {
  const storedTheme = localStorage.getItem('book-theme')
  isDark.value = storedTheme ? storedTheme === 'dark' : window.matchMedia('(prefers-color-scheme: dark)').matches
})
useHead({
  titleTemplate: '%s',
  htmlAttrs: { lang: 'fa', dir: 'rtl' },
  title: 'کتاب ما فکر نمی‌کنیم، تصمیم می‌گیریم! | میثم کیهانی',
  meta: [
    { name: 'description', content: 'معرفی و مشخصات کتاب ما فکر نمی‌کنیم، تصمیم می‌گیریم! نوشته‌ی میثم کیهانی؛ درباره نئو مارکتینگ، روان‌شناسی تصمیم‌گیری و رفتار مصرف‌کننده.' },
    { name: 'theme-color', content: '#f4f0e8' },
    { property: 'og:title', content: 'ما فکر نمی‌کنیم، تصمیم می‌گیریم! | میثم کیهانی' },
    { property: 'og:type', content: 'book' },
    { property: 'og:image', content: '/images/maysam-book.png' }
  ]
})
</script>



