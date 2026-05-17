---
layout: single
author_profile: true
title: ""
classes: wide
---

<div align="center">
  <h1>
    <span id="typing"></span>
    <span class="cursor">|</span>
  </h1>
</div>

<style>
.cursor {
  overflow: hidden; /* Hide text not yet "typed" */
  border-right: .15em solid orange; /* The cursor */
  white-space: nowrap; /* Keep text on one line */
  width: 0;
  animation: 
    typing 3.5s steps(30, end) forwards,
    blink-caret .75s step-end infinite;
}

@keyframes blink {
  from { width: 0 }
  to { width: 100% }
}

@keyframes blink-caret {
  from, to { border-color: transparent }
  50% { border-color: orange; }
}

</style>

<script>
document.addEventListener("DOMContentLoaded", function () {

  const text = "Welcome to my Portfolio";
  let i = 0;

  function typeWriter() {
    if (i < text.length) {
      document.getElementById("typing").innerHTML += text.charAt(i);
      i++;
      setTimeout(typeWriter, 70);
    }
  }

  typeWriter();

});
</script>


Feel free to check around in the navigation bar to know more about my professional journey.
<h3> Brief description about me; </h3>
An ambitious telecommunications engineering graduate driven by a passion for continuous learning and growth. I bring a blend of technical expertise, problem-solving skills, and a deep understanding of the field. With rigorous coursework and hands-on experience in both telecom and information systems, I am committed to creating innovative, efficient communication solutions. I recognize the value of diverse perspectives in a team setting and I am confident in my ability to contribute to effective solutions through collaborative efforts.

<blockquote> I embrace change. Change is one of the major constant things in life.</blockquote>
