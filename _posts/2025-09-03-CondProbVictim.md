---
layout: post
title: เหยื่อคุกคามทางเพศกับการแต่งตัว
date: 2025-09-03 10:00:00
description:  กับดักความคิด&Conditional probability
tags: misc thai math
categories: posts
thumbnail: assets/img/posts/2025-09-03-CondProbVictim/CondStatVictim.004.jpeg
---
บทความนี้เป็นการนำเสนอเรื่องกับดักความคิดและความน่าจะเป็นแบบมีเงื่อนไข (Conditional Probability) ในบริบทของการคุกคามทางเพศและการแต่งตัว

ออกตัวก่อนนะครับว่าไม่ได้มีเจตนาโทษเหยื่อ หากแต่ต้องการอธิบายว่าทำไมการคิดแบบนี้จึงไม่สมเหตุสมผล เพราะไม่อยากให้สังคมติดกับดักความคิดแบบผิดๆ

---
ช่วงหลังมานี้ผมเห็นหลายคนในกระแสDont tell me how to dress มักจะอ้างเหตุผลประมาณว่า
- “มีการสำรวจสถิติคนถูกข่มขืนแล้วพบว่าเหยื่อที่แต่งตัวมิดชิดมีเท่าๆกับเหยื่อที่แต่งตัวโป๊”

- “แต่งตัวแบบไหนก็มีสิทธิ์โดนหมด”

- “ดังนั้นแต่งตัวแบบไหนก็เสี่ยงเท่ากัน”

# จริงหรอ?
แม้เบื้องต้นจะฟังดูสมเหตุสมผล แต่ความจริงแล้วนี่อาจจะเป็นตรรกะวิบัติอีกอย่างหนึ่งก็ได้ ทั้งนี้ทั้งนั้นแม้ผมจะเห็นด้วยกับสถิติที่ยกมาและถูกต้องแน่นอนว่าแต่งตัวแบบไหนก็มีสิทธิ์เป็นเหยื่อได้

แต่การสรุปว่าการแต่งตัวแบบไหนก็เสี่ยงเท่ากันแบบนั้นถูกต้องจริงหรือ?

## เฉลย: ไม่เสมอไป

ใช่หรือไม่ก็ได้ ขึ้นอยู่กับประชากรทั้งหมด โดยในทางคณิตศาสตร์เราอธิบายได้ดังนี้

<div class="row mt-3">
    <div class="col-11 mx-auto mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/posts/2025-09-03-CondProbVictim/CondStatVictim.004.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

<div class="row mt-3">
    <div class="col-11 mx-auto mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/posts/2025-09-03-CondProbVictim/CondStatVictim.005.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

<div class="row mt-3">
    <div class="col-11 mx-auto mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/posts/2025-09-03-CondProbVictim/CondStatVictim.006.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

<div class="row mt-3">
    <div class="col-11 mx-auto mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/posts/2025-09-03-CondProbVictim/CondStatVictim.007.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

<div class="row mt-3">
    <div class="col-11 mx-auto mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/posts/2025-09-03-CondProbVictim/CondStatVictim.008.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

<div class="row mt-3">
    <div class="col-11 mx-auto mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/posts/2025-09-03-CondProbVictim/CondStatVictim.009.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

คณิตศาสตร์เบื้องหลังความน่าจะเป็นในโพสต์นี้คือ Bayes' theorem สำหรับผู้สนใจผมแนะนำคลิปวิดีโอของช่อง[3Blue1Brown](https://youtu.be/HZGCoVF3YvM)อธิบายไว้ดีมากครับ