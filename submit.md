---
layout: default
title: 投稿
permalink: /submit/
---

<section class="submit-hero">
  <div class="submit-hero-inner">
    <div class="submit-label">投稿</div>
    <h1>写下你的故事</h1>
    <p>不需要注册任何账号，不需要会编程。<br>填完表单点提交，我们会审阅后发布。</p>
  </div>
</section>

<section class="submit-form-section">
  <div class="submit-form-inner">

    <form id="story-form" class="story-form" action="https://formspree.io/f/FORM_ID" method="POST">
      <input type="hidden" name="_subject" value="新投稿：少女心事">
      <input type="hidden" name="_captcha" value="true">

      <div class="form-group">
        <label for="story-title">故事标题</label>
        <input type="text" id="story-title" name="title" placeholder="给你的故事起个名字" required>
      </div>

      <div class="form-row">
        <div class="form-group">
          <label for="story-author">笔名</label>
          <input type="text" id="story-author" name="author" placeholder="你想被怎么称呼" required>
        </div>
        <div class="form-group">
          <label for="story-email">邮箱（可选，用于联系你）</label>
          <input type="email" id="story-email" name="_replyto" placeholder="不会公开">
        </div>
      </div>

      <div class="form-group">
        <label>主题标签</label>
        <div class="tag-checkboxes">
          <label class="tag-check"><input type="checkbox" name="tags" value="智识"><span>智识</span></label>
          <label class="tag-check"><input type="checkbox" name="tags" value="友谊"><span>友谊</span></label>
          <label class="tag-check"><input type="checkbox" name="tags" value="野心"><span>野心</span></label>
          <label class="tag-check"><input type="checkbox" name="tags" value="竞争"><span>竞争</span></label>
          <label class="tag-check"><input type="checkbox" name="tags" value="贫穷"><span>贫穷</span></label>
          <label class="tag-check"><input type="checkbox" name="tags" value="身体"><span>身体</span></label>
          <label class="tag-check"><input type="checkbox" name="tags" value="家庭"><span>家庭</span></label>
          <label class="tag-check"><input type="checkbox" name="tags" value="成长"><span>成长</span></label>
        </div>
      </div>

      <div class="form-group">
        <label for="story-content">故事正文</label>
        <div class="textarea-wrap">
          <textarea id="story-content" name="content" rows="20" placeholder="在这里写你的故事。不需要华丽的文笔，真实就好。" required></textarea>
          <div class="char-count"><span id="char-num">0</span> 字</div>
        </div>
      </div>

      <div class="form-agreement">
        <label class="agreement-check">
          <input type="checkbox" required>
          <span>提交即表示我同意将出版权授予本项目，保留署名权，知悉所有收入全部捐赠。</span>
        </label>
      </div>

      <div class="form-actions">
        <button type="submit" class="btn-submit" id="submit-btn">提交故事</button>
        <span class="form-hint">审稿只看真诚与尊重，不评判文笔</span>
      </div>
    </form>

    <div id="success-msg" class="success-message" style="display:none;">
      <div class="success-icon">&#10003;</div>
      <h2>投稿已收到</h2>
      <p>感谢你写下自己的故事。我们会尽快审阅，通过后将发布在网站上。</p>
      <a href="{{ '/' | relative_url }}" class="btn-outline btn-back">回到首页</a>
    </div>

  </div>
</section>

<script>
// 字数统计
var ta = document.getElementById('story-content');
var counter = document.getElementById('char-num');
ta.addEventListener('input', function() {
  counter.textContent = ta.value.length;
});

// AJAX 提交
var form = document.getElementById('story-form');
form.addEventListener('submit', function(e) {
  e.preventDefault();
  var btn = document.getElementById('submit-btn');
  btn.textContent = '提交中…';
  btn.disabled = true;

  var data = new FormData(form);

  fetch(form.action, {
    method: 'POST',
    body: data,
    headers: { 'Accept': 'application/json' }
  }).then(function(res) {
    if (res.ok) {
      form.style.display = 'none';
      document.getElementById('success-msg').style.display = 'block';
      window.scrollTo({ top: 0, behavior: 'smooth' });
    } else {
      btn.textContent = '提交失败，请重试';
      btn.disabled = false;
    }
  }).catch(function() {
    btn.textContent = '网络错误，请重试';
    btn.disabled = false;
  });
});
</script>
