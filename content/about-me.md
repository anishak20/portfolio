---

title: "About Me"
layout: "About Me"
url: "/about-me"

---

<!-- Typewriter animation -->
<div class="typewriter-container">
  <span id="typewriter-text" class="typewriter-text"></span>
</div>

<!-- Image + Text section -->
<div style="display: flex; flex-wrap: wrap; align-items: flex-start; gap: 2rem; margin-top: 2rem;">

  <!-- Left: Photo -->
  <div style="flex: 1 1 250px;">
    <img src="/home/anisha3.jpeg" alt="Anisha Khatri" style="max-width: 300px; width: 100%;">
  </div>

  <!-- Right: Text that flows *beside* the image -->
  <div style="flex: 1 1 300px; color: white; font-size: 0.9em;">
    <p>
      I have completed my Master’s degree in Physics from 
      <a href="https://physics.du.ac.in/" target="_blank">University of Delhi</a>, with a specialization in Astrophysics, General Relativity, and Cosmology. <br> <br>
      During this period, I worked as a project student in the <strong>Observational Astronomy Laboratory</strong> of the department, where I focused on the <strong>photometric study of the globular cluster NGC 4147</strong>. This work involved analysing an initial sample of <strong>2389 stars</strong> to identify extra-tidal stars in the cluster by applying a selection criterion based on proper motion filtering, membership probability analysis, and the stars positions on the color–magnitude diagram. 
    </p>
  </div>
</div>
<!-- Below image: Full width text continues here -->

<div style="color: white; font-size: 0.9em; margin-top: -2rem;">
  <p>

  This work was supervised by <a href= "http://people.du.ac.in/~trs/" target="_blank">Prof. T.R. Seshadri</a> and Dr. Sachin Pandey. For my Bachelor's degree at the University of Delhi, I pursued a B.Sc. (Honours) in Physics with a minor in Mathematics.<br>

   I'm broadly interested in **stellar populations in the milky way, galaxy formation & evolution, transients and data analysis** methods. I'm currently seeking research or Ph.D. opportunities to deepen my expertise and make meaningful contributions to the field.<br>

   Beyond academics, I enjoy doing art and graphic design, watching films across genres, running outdoors, and visiting historical places.<br><br><br>

   <!-- Contact Section -->
<!-- Contact Section -->
<div style="text-align: center; margin-top: 2rem;">

  <h2>Contact Me!</h2>
  <p style="color: white;">
    Email is the fastest way to reach me - feel free to drop a message if you’d like to chat about galaxies, science, or just say hi.
  </p>

  <div style="display: flex; justify-content: center; gap: 1.5rem; margin-top: 1rem;">
    <!-- Email -->
    <a href="mailto:khatri.anisha20@gmail.com" target="_blank" title="Email">
      <img src="https://cdn.jsdelivr.net/npm/simple-icons@v9/icons/maildotru.svg" alt="Email" style="width: 30px; filter: brightness(0) invert(1);">
    </a>
    <!-- LinkedIn -->
    <a href="https://www.linkedin.com/in/anishakhatri" target="_blank" title="LinkedIn">
      <img src="https://cdn.jsdelivr.net/npm/simple-icons@v9/icons/linkedin.svg" alt="LinkedIn" style="width: 30px; filter: brightness(0) invert(1);">
    </a>
    <!-- GitHub -->
    <a href="https://github.com/anishak20" target="_blank" title="GitHub">
      <img src="https://cdn.jsdelivr.net/npm/simple-icons@v9/icons/github.svg" alt="GitHub" style="width: 30px; filter: brightness(0) invert(1);">
    </a>
    <!-- Letterboxd -->
    <a href="https://letterboxd.com/anishatwentied/" target="_blank" title="Letterboxd">
      <img src="https://cdn.jsdelivr.net/npm/simple-icons@v9/icons/letterboxd.svg" alt="Letterboxd" style="width: 30px; filter: brightness(0) invert(1);">
    </a>


  </div>

</div>


<style>
.typewriter-container {
  font-family: monospace;
  font-size: 2em;
  color: white;
  margin-bottom: 1.5rem;
}

.typewriter-text::after {
  content: '|';
  animation: blink 0.8s infinite;
  color: white;
}

@keyframes blink {
  50% { opacity: 0; }
}
</style>

<script>
const textElement = document.getElementById('typewriter-text');
const messages = ["Hi, I'm Anisha!", "Glad to have you here :)"];
let messageIndex = 0;
let charIndex = 0;
let typing = true;

function type() {
  const currentText = messages[messageIndex];
  
  if (typing) {
    if (charIndex < currentText.length) {
      textElement.textContent += currentText.charAt(charIndex);
      charIndex++;
      setTimeout(type, 150); // Typing speed
    } else {
      typing = false;
      setTimeout(type, 1000); // Pause before deleting
    }
  } else {
    if (charIndex > 0) {
      textElement.textContent = currentText.substring(0, charIndex - 1);
      charIndex--;
      setTimeout(type, 80); // Deleting speed
    } else {
      typing = true;
      messageIndex = (messageIndex + 1) % messages.length;
      setTimeout(type, 400); // Pause before next typing
    }
  }
}

type();
</script>
