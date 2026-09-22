<script setup>
import { ref } from 'vue'

// 预约表单数据
const form = ref({ name: '', phone: '', course: '' })
const submitted = ref(false)

function submitForm() {
  // 目前先做"假提交"，点了显示成功提示；以后接后端再真正发送
  if (form.value.name && form.value.phone) {
    submitted.value = true
  }
}

</script>

<template>
  <div class="page">

    <!-- 顶部导航 -->
    <header class="nav">
      <div class="logo">燃力健身</div>
      <nav>
        <a href="#courses">课程</a>
        <a href="#coaches">教练</a>
        <a href="#price">价格</a>
        <a href="#contact">联系我们</a>
      </nav>
    </header>

    <!-- 首屏 Hero -->
    <!-- <section class="hero">
    </section> -->
    <section class="hero" style="background-image:url('/hero.jpg'); background-size:cover; background-position:center;">
      <h1>把坚持，练成习惯</h1>
      <p>县城首家主打科学减脂与力量训练的小型健身工作室<br />私教为主，人少不打挤。</p>
      <a class="btn" href="#contact">免费预约体验课</a>
    </section>

    <!-- 课程 -->
    <section id="courses" class="section">
      <h2>我们的课程</h2>
      <div class="cards">
        <div class="card">
          <h3>减脂塑形</h3>
          <p>训后快碳+高蛋白，科学掉秤不反弹</p>
        </div>
        <div class="card">
          <h3>力量增肌</h3>
          <p>分部位循环，动作标准优先，稳扎稳打</p>
        </div>
        <div class="card">
          <h3>产后 / 体态</h3>
          <p>安全恢复，循序渐进，找回身体状态</p>
        </div>
      </div>
    </section>

        <!-- 教练 -->
    <section id="coaches" class="section">
      <h2>我们的教练</h2>
      <div class="cards">
        <div class="card coach">
          <div class="pic">李教练</div>
          <h3>李教练</h3>
          <p>十年力量训练经验，专精科学增肌与分部位循环安排，动作抠到标准。</p>
        </div>
        <div class="card coach">
          <div class="pic">王教练</div>
          <h3>王教练</h3>
          <p>减脂塑形专家，擅长运动+营养搭配，帮学员科学掉秤不反弹。</p>
        </div>
      </div>
    </section>

    <!-- 价格 -->
    <section id="price" class="section">
      <h2>价格</h2>
      <div class="cards">
        <div class="card"><h3>体验课</h3><p>9.9 元/次</p><p>先试后买，感受私教</p></div>
        <div class="card"><h3>月卡</h3><p>899 元</p><p>一对一私教 15 次</p></div>
        <div class="card"><h3>季卡</h3><p>1299 元</p><p>一对一私教 40 次</p></div>
      </div>
    </section>

    <!-- 联系/预约 -->
    <section id="contact" class="section">
      <h2>免费预约体验课</h2>
      <form @submit.prevent="submitForm">
        <input v-model="form.name" placeholder="你的名字" />
        <input v-model="form.phone" placeholder="手机号" />
        <select v-model="form.course">
          <option value="">想了解哪门课？</option>
          <option>减脂塑形</option>
          <option>力量增肌</option>
          <option>产后 / 体态</option>
        </select>
        <button type="submit">提交预约</button>
      </form>
      <p v-if="submitted" class="ok">✅ 预约成功！我们会尽快联系你。</p>
    </section>

    <!-- 页脚 -->
    <footer>
      <p>燃力健身工作室 · 地址待填 · 营业时间 9:00-21:00</p>
    </footer>

  </div>
</template>

<style scoped>
* { margin:0; padding:0; box-sizing:border-box; }
body { font-family: system-ui, sans-serif; color:#222; }
.page { min-height:100vh; }

.nav { display:flex; justify-content:space-between; align-items:center; padding:18px 40px; background:#111; color:#fff; position:sticky; top:0; }
.logo { font-weight:700; font-size:20px; color:#ff6b35; }
.nav nav a { color:#ddd; margin-left:24px; text-decoration:none; }
.nav nav a:hover { color:#ff6b35; }

.hero { text-align:center; padding:120px 20px; background:#1a1a1a; color:#fff; }
.hero h1 { font-size:52px; margin-bottom:18px; color:#bbb; }
.hero p { font-size:18px; color:#bbb; line-height:1.8; margin-bottom:30px; }
.btn { display:inline-block; background:#ff6b35; color:#fff; padding:14px 32px; text-decoration:none; border-radius:6px; font-weight:600; }
.btn:hover { background:#ff8250; }

.section { padding:70px 40px; text-align:center; }
.section h2 { font-size:32px; margin-bottom:40px; }
.cards { display:flex; gap:24px; justify-content:center; flex-wrap:wrap; }
.card { border:1px solid #eee; border-radius:10px; padding:30px; width:240px; box-shadow:0 4px 12px rgba(0,0,0,.06); }
.card h3 { margin-bottom:12px; color:#ff6b35; }
.card p { color:#555; line-height:1.6; }

/**#price .section h2 {}**/
form { max-width:360px; margin:0 auto; display:flex; flex-direction:column; gap:14px; }
input, select, button { padding:12px; font-size:16px; border:1px solid #ccc; border-radius:6px; }
button { background:#ff6b35; color:#fff; border:none; cursor:pointer; font-weight:600; }
button:hover { background:#ff8250; }
.ok { margin-top:16px; color:#2e7d32; font-weight:600; }
.coach .pic { width:90px; height:90px; border-radius:50%; background:#ff6b35; color:#fff; display:flex; align-items:center; justify-content:center; font-size:18px; font-weight:600; margin:0 auto 16px; }

footer { background:#111; color:#777; text-align:center; padding:20px; }
</style>