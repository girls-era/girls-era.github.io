---
layout: default
title: 投稿
permalink: /submit/
---

<section class="submit-hero">
  <div class="submit-hero-inner">
    <h1>投稿故事</h1>
    <p>写下你的少女心事，不需要会用 Git。</p>
  </div>
</section>

<section class="submit-form-section">
  <div class="submit-form-inner">
    <form id="story-form" class="story-form">
      <div class="form-group">
        <label for="story-title">故事标题</label>
        <input type="text" id="story-title" placeholder="给你的故事起个名字" required>
      </div>

      <div class="form-group">
        <label for="story-author">你的笔名</label>
        <input type="text" id="story-author" placeholder="可以是任何你喜欢的名字" required>
      </div>

      <div class="form-group">
        <label>主题标签（可多选）</label>
        <div class="tag-checkboxes">
          <label class="tag-check"><input type="checkbox" name="tags" value="智识"> 智识</label>
          <label class="tag-check"><input type="checkbox" name="tags" value="友谊"> 友谊</label>
          <label class="tag-check"><input type="checkbox" name="tags" value="野心"> 野心</label>
          <label class="tag-check"><input type="checkbox" name="tags" value="竞争"> 竞争</label>
          <label class="tag-check"><input type="checkbox" name="tags" value="贫穷"> 贫穷</label>
          <label class="tag-check"><input type="checkbox" name="tags" value="身体"> 身体</label>
          <label class="tag-check"><input type="checkbox" name="tags" value="家庭"> 家庭</label>
          <label class="tag-check"><input type="checkbox" name="tags" value="成长"> 成长</label>
        </div>
      </div>

      <div class="form-group">
        <label for="story-content">故事正文</label>
        <textarea id="story-content" rows="16" placeholder="在这里写你的故事。&#10;&#10;不需要华丽的文笔，真实就好。&#10;段落之间空一行。&#10;可以用 --- 分隔场景。" required></textarea>
      </div>

      <div class="form-group form-note">
        <p>点击「提交」会跳转到 GitHub 创建一条投稿。你需要一个 GitHub 账号（免费注册）。<br>我们会审阅后发布，审稿只看真诚与尊重，不评判文笔。</p>
        <p>提交即表示你同意：将出版权授予本项目、保留署名权、知悉所有收入全部捐赠。</p>
      </div>

      <button type="submit" class="btn-primary btn-submit">提交故事</button>
    </form>
  </div>
</section>

<script>
document.getElementById('story-form').addEventListener('submit', function(e) {
  e.preventDefault();

  var title = document.getElementById('story-title').value.trim();
  var author = document.getElementById('story-author').value.trim();
  var content = document.getElementById('story-content').value.trim();

  var tags = [];
  document.querySelectorAll('input[name="tags"]:checked').forEach(function(cb) {
    tags.push(cb.value);
  });

  var body = '### 故事标题\n\n' + title +
    '\n\n### 笔名\n\n' + author +
    '\n\n### 主题标签\n\n' + (tags.length > 0 ? tags.join(', ') : '未选择') +
    '\n\n### 故事正文\n\n' + content +
    '\n\n---\n*通过网站投稿表单提交*';

  var url = 'https://github.com/girls-era/girls-era.github.io/issues/new' +
    '?template=story-submission.yml' +
    '&title=' + encodeURIComponent('故事投稿：' + title) +
    '&story-title=' + encodeURIComponent(title) +
    '&author=' + encodeURIComponent(author) +
    '&tags=' + encodeURIComponent(tags.join(', ')) +
    '&content=' + encodeURIComponent(content);

  if (url.length > 8000) {
    url = 'https://github.com/girls-era/girls-era.github.io/issues/new' +
      '?labels=故事投稿' +
      '&title=' + encodeURIComponent('故事投稿：' + title) +
      '&body=' + encodeURIComponent(body);
  }

  window.open(url, '_blank');
});
</script>
