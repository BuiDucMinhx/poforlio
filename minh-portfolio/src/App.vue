<script setup>
</script>

<template>
  <div class="container">
    <header class="hero">
      <h1>Minh Java BE Dev (có 1 chút hiểu biết về vuejs, solidity).</h1>
      <p class="sub">
        Scale từ sự đơn giản.<br />
      </p>
    </header>

    <section class="divider"></section>

<section class="section">
  <h3>Triết lý code của mình</h3>

  <div class="work-item">
    <p>
      - Mỗi ngày mình vẫn luôn cố gắng commit 1 thứ gì đó có ý nghĩa dù mình đã thất nghiệp trong 1 thời gian dài, có thể là 1 thuật toán nào đó hay hay trong Cracking the code interview, hoặc 1 update nào đó có ý nghĩa cho dự án mà mình tâm huyết, mình ko biết liệu sẽ đi đến đâu nhưng mình nghĩ đó là niềm vui mỗi ngày của mình, mình nghĩ bản thân mình reasoning khá tốt thay vì chỉ ngồi gõ code, mình thường ngồi cả ngày để reasoning và code 1 vài dòng nhỏ nhưng ý nghĩa, mình thích việc trade ra vấn đề và suy nghĩ triết lý hay ý nghĩa của mỗi dòng code, tại sao nó tồn tại thay vì cố gắng commit hay sửa code nhiều để tỏ ra mình bận rộn. Đối vs mình cái khó nhất là làm sao code thêm để bổ sung vốn tri thức cho dự án mà ko làm ảnh hưởng cái cũ vì tích lũy tri thức mới hình thành pattern, nếu ko tích lũy thì ko thể hình thành pattern mà chỉ là những đoạn code rời rạc dư thừa, over engineer, best practice giáo điều, ko phải best practice thực sự.
    </p>
    <p>
      - Mỗi ngày phải tạo đc 1 commit có ý nghĩa : 1 thuật toán work đúng, update code project phải có ý đồ rõ ràng và giải quyết pain thực sự.
    </p>

    </div>

    <div class="work-item">
      <h4>Phong cách code : Simplify : Giảm nhiễu – Tăng nhất quán – Tích lũy pattern.</h4>

      <ul class="rule-list">
        <li>1. Giữ mọi thứ đơn giản, ko over engineer nếu ko cần thiết.</li>
        <li>1. Readable first, Chỉ optimize khi đã chốt đc spec with high readable.</li>
        <li>2. Chỉ optimize nếu load test có số liệu về tail latency, ko tối ưu mù nếu ko có số liệu</li>
        <li>3. Reafactor code theo flow data, anti clean code, anti các thể loại pattern phá flow vì best practive giáo điều thường gây tách hàm, phá flow logic code, call stack sâu, allocation thừa, nhảy hàm phức tạp mà ít giá trị kĩ thuật, refactor phải đảm bảo rõ flow, ko tách hàm vô nghĩa.</li>
        <li>4. Query : hạn viết native, thuần JPA nhất nếu có thể, chỉ viết nếu thực sự cần (mình cảm thấy luôn có cách để ko cần viết và chứng minh performance tương đương).</li>
        <li>5. Khi có 1 requiment chưa rõ spec : Viết abtract và implement theo 2 hướng
          <br />- SpecImplement : SpecImplement viết trước theo hướng readable càng rõ flow thể hiện đúng requiment càng tốt, có thể mapping trực tiếp từ requiment, tối ưu readable theo hướng : bỏ code thừa tối ưu cho flow logic.
          <br />- OptimizeImplement: Phát triển theo spec, Tối ưu theo hướng peformance, ban đầu giống spec, sau đó dựa trên spec update dần bằng các thuật toán và chứng minh bằng số liệu nhanh hơn bao nhiêu khi so vs spec.
        </li>
        <li>6. Viết Api theo use case, tổ chức code theo use case, 1 file access data chỉ phục vụ duy nhất 1 bussiness, đây chính là quy tắc đơn trách nhiệm thực sự.</li>
        <li>7. Ko đánh index bừa nếu ko đo explain đc query, có thể đánh theo quy tắc nếu chứng minh đc số liệu (mình rất rất ít đánh index)</li>
        <li>8. Optimic Lock + retry + version: ko dùng nếu ko chứng minh đc giá trị, retry để đảm bảo consistency luôn nặng hơn lock thường.</li>
        <li>9. Với các case chưa pass : luôn fix bằng cách : ít thay đối nhất để bảo toàn toàn bộ flow bussiness đã có và đảm bảo sau khi fix các case cũ ko bị phá, chỉ reafator lại để thống nhất flow khi đã rõ toàn bộ ý đồ của flow cũ.</li>
        <li>10. Tôn trọng kĩ thuật thay vì buzzword nghe sang nhưng ko có giá trị.</li>
        <li>11. Các loại stream, lamba, Optional… hạn chế dùng vì jit khó inline, nếu dùng nên có số liệu khi đo vs cách viết thông thường.</li>
        <li>12. Thuật toán : chỉ dùng để optimize, ko viết cho đẹp. nếu framework đã hỗ trợ thì nên dùng framework để readable first.</li>
        <li>13. Thread : Executor dùng chung cho toàn app để quản lí core, chỉ dùng nếu thực sự cần vì thread luôn có queue ảnh hưởng đến tail latency</li>
        <li>14. Dùng primitive để hạn chế allocation nhất có thể.</li>
        <li>15. Hiện app mình chỉ xài caffein thay vì redis cho cahce, SSE thay vì kafka cho queue, mình đang rất muốn scale để xem ngưỡng nào là cần đổi stack. (scale khi status > thresh hold).</li>
        <li>16. Viết unit test với mục đích duy nhất : khóa invariant bussiness chứ ko phải để tăng coverage, nếu invariant mình có thể encode bằng comment hoặc khả năng đọc đc implicit trong code mình có thể bỏ viết test.</li>
        <li>17. Tư duy onwership : dev nên chịu trách nhiệm cho toàn bộ code của mình ở phần outcome chỉ như thế dev mới viết code 1 cách đàng hoàng, nếu ko được chịu trách nhiệm thì trực giác kĩ thuật của họ sẽ bị mài mòn theo năm tháng .</li>
      </ul>
    </div>
  </section>

    <section class="divider"></section>

    <section class="section">
      <h3>Engineering Style</h3>

      <div class="work-item">
        <h4>Simplify</h4>
        <ul>
          <li>Giảm nhiễu – Tăng nhất quán – Tích lũy pattern.</li>
          <li>Thuật toán để tối ưu, không để khoe.</li>
          <li>Tôn trọng kỹ thuật hơn buzzword.</li>
          <li>Thread và allocation luôn có giá phải trả.</li>
        </ul>
      </div>

      <div class="work-item">
        <h4>Scaling Mindset</h4>
        <ul>
          <li>Chỉ đổi stack khi metrics vượt threshold.</li>
          <li>Caffeine trước Redis.</li>
          <li>SSE trước Kafka.</li>
          <li>Scale dựa trên dữ liệu, không dựa trên hype.</li>
        </ul>
      </div>
    </section>

    <section class="divider"></section>

    <section class="section">
      <h3>Contact</h3>
      <p>Nếu bạn tin tưởng vào mindset của mình, hãy liên hệ.</p>
      <a href="mailto:minh@email.com">minhbd33@email.com</a>
    </section>
    <section class="image-section">
      <p>Phong cách commit : </p>
      <img src="/images/git-1.png" alt="Git log 1">
      <img src="/images/git-2.png" alt="Git log 2">
    </section>

  </div>
</template>

<style>
:root {
  --text: #111;
  --muted: #666;
  --border: #ddd;
  --bg: #f7f7f7;
}
body {
  text-align: left;
}

.container,
.philosophy-section,
.work-item {
  text-align: left;
}

body {
  margin: 0;
  background: var(--bg);
  font-family: "Inter", system-ui, sans-serif;
  color: var(--text);
}

.container {
  max-width: 720px;
  margin: 80px auto;
  padding: 0 20px;
}

.hero h1 {
  font-size: 32px;
  font-weight: 600;
  margin-bottom: 20px;
}

.hero h2 {
  font-size: 28px;
  font-weight: 400;
  margin-bottom: 20px;
}

.sub {
  color: var(--muted);
  font-size: 18px;
  line-height: 1.6;
}

.section {
  margin: 60px 0;
}

h3 {
  font-size: 20px;
  margin-bottom: 30px;
}

.philosophy {
  list-style: none;
  padding: 0;
}

.philosophy li {
  margin-bottom: 15px;
  font-size: 16px;
}

.philosophy span {
  display: inline-block;
  width: 40px;
  color: var(--muted);
}

.work-item {
  margin-bottom: 30px;
}

.work-item h4 {
  margin-bottom: 10px;
}

.work-item ul {
  padding-left: 0;
  margin-left: 0;
  color: var(--text);
}

.divider {
  height: 1px;
  background: var(--border);
  margin: 60px 0;
}

a {
  color: var(--text);
  text-decoration: underline;
}
.rule-list {
  list-style: none;
  padding-left: 0;
  margin-top: 20px;
}

.rule-list li {
  margin-bottom: 28px;
  line-height: 1.75;
  color: var(--text);
}

.rule-list li br {
  display: block;
  margin-top: 6px;
}

.philosophy-section ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.philosophy-section ul li {
  margin: 24px 0;
  line-height: 1.75;
  padding: 0;
}
.image-section img {
  width: 100%;
  max-width: 900px;
  display: block;
  margin: 32px 0;
}
</style>