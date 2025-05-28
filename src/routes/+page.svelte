<script lang="ts">
  import { onMount } from "svelte";
  import "../app.css";

  let isScrolled = false;

  const handleScroll = () => {
    isScrolled = window.scrollY > 10; // you can tweak this threshold
  };

  onMount(() => {
    console.log("Component mounted");
    window.addEventListener("scroll", handleScroll);
    handleScroll(); // init state on mount
    return () => window.removeEventListener("scroll", handleScroll);
  });

  const scrollToSection = (id: string) => {
    const el = document.getElementById(id);
    if (el) el.scrollIntoView({ behavior: "smooth", block: "center" });
  };

  // For calculating the duration since December 2023
  const startDate = new Date("2023-12-01");
  const now = new Date();

  const diffInMonths =
    (now.getFullYear() - startDate.getFullYear()) * 12 +
    (now.getMonth() - startDate.getMonth());

  const years = Math.floor(diffInMonths / 12);
  const months = diffInMonths % 12;

  const duration =
    years > 0 && months > 0
      ? `${years} yr${years > 1 ? "s" : ""} ${months} mo${months > 1 ? "s" : ""}`
      : years > 0
        ? `${years} yr${years > 1 ? "s" : ""}`
        : `${months} mo${months > 1 ? "s" : ""}`;
</script>

<!-- NAVBAR -->
<nav class="fixed top-0 left-0 w-full text-white shadow z-50 transition-colors duration-300 {isScrolled ? 'bg-gray-900/90' : 'bg-gray-900'}">
  <div class="flex justify-center space-x-6 py-4 font-semibold">
    <button on:click={() => scrollToSection("experience")}>Experience</button>
    <button on:click={() => scrollToSection("skills")}>Skills</button>
    <button on:click={() => scrollToSection("projects")}>Projects</button>
    <button on:click={() => scrollToSection("contact")}>Contact</button>
  </div>
</nav>

<!-- Spacer -->
<div class="h-16"></div>

<!-- HOME -->
<section id="home" class="text-center py-20 px-6 bg-gray-100">
  <h1 class="text-4xl font-bold mb-2">Kaloyan Andreev</h1>
  <p class="text-xl text-gray-700">
    Full-stack Developer based in Varna, Bulgaria
  </p>
</section>

<!-- EXPERIENCE -->
<section id="experience" class="py-20 px-6 max-w-3xl mx-auto">
  <h2 class="text-3xl font-bold mb-6">Work Experience</h2>

  <h3 class="text-xl font-semibold">Full Stack Software Developer – BUL-AI</h3>
  <p class="italic text-sm mb-2">Dec 2023 – Present · {duration}</p>
  <ul class="list-disc list-inside text-gray-700 space-y-1">
    <li>
      Built and maintained responsive web applications using JavaScript, jQuery,
      SCSS, and HTML
    </li>
    <li>
      Developed UI components with Framework7, Bootstrap, SweetAlert2, and
      Select2
    </li>
    <li>Created hybrid mobile apps using Cordova for Android/iOS deployment</li>
    <li>Integrated MQTT and WebSockets for real-time data communication</li>
    <li>Handled backend development with PHP, AJAX, and MariaDB/SQL</li>
    <li>Implemented secure BORICA payment gateway integration</li>
    <li>Developed new Cordova-based mobile apps for internal business tools</li>
    <li>
      Created a marine planning web app with ship location tracking and route
      mapping using Leaflet.js
    </li>
  </ul>
</section>

<section id="skills" class="py-20 px-6 bg-gray-50 max-w-3xl mx-auto">
  <h2 class="text-3xl font-bold mb-8 text-center">Skills</h2>
  <div class="grid sm:grid-cols-3 gap-10 text-gray-700">
    <div>
      <h3 class="font-semibold text-lg mb-4 border-b-2 border-gray-300 pb-2">
        Backend
      </h3>
      <div class="flex flex-wrap gap-3">
        {#each ["PHP", "SQL", "MariaDB", "C++"] as skill}
          <span
            class="bg-blue-100 text-blue-800 text-sm font-medium px-3 py-1 rounded-full cursor-default
                   hover:bg-blue-800 hover:text-blue-100 transition-colors duration-300"
            >{skill}</span
          >
        {/each}
      </div>
    </div>
    <div>
      <h3 class="font-semibold text-lg mb-4 border-b-2 border-gray-300 pb-2">
        Frontend
      </h3>
      <div class="flex flex-wrap gap-3">
        {#each ["JavaScript (ES6)", "React", "Svelte", "jQuery", "AJAX", "HTML5", "CSS/SCSS", "Framework7", "Bootstrap", "Select2", "SweetAlert2", "Leaflet", "jQuery UI"] as skill}
          <span
            class="bg-green-100 text-green-800 text-sm font-medium px-3 py-1 rounded-full cursor-default
                   hover:bg-green-800 hover:text-green-100 transition-colors duration-300"
            >{skill}</span
          >
        {/each}
      </div>
    </div>
    <div>
      <h3 class="font-semibold text-lg mb-4 border-b-2 border-gray-300 pb-2">
        Other Technologies
      </h3>
      <div class="flex flex-wrap gap-3">
        {#each ["Cordova", "WebSockets", "MQTT", "Notepad"] as skill}
          <span
            class="bg-purple-100 text-purple-800 text-sm font-medium px-3 py-1 rounded-full cursor-default
                   hover:bg-purple-800 hover:text-purple-100 transition-colors duration-300"
            >{skill}</span
          >
        {/each}
      </div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects" class="py-20 px-6 max-w-3xl mx-auto">
  <h2 class="text-3xl font-bold mb-4">Projects & Learning</h2>

  <h3 class="text-xl font-semibold mb-1">React Practice Projects</h3>
  <p class="text-gray-700 mb-4 indent-3">
    Building small to medium React apps to master component-based architecture,
    hooks, state management, and routing. Examples include to-do lists, weather
    apps, and interactive UI components.
  </p>

  <h3 class="text-xl font-semibold mb-1">Svelte & SvelteKit Homework</h3>
  <p class="text-gray-700 mb-4 indent-3">
    Actively exploring Svelte and SvelteKit by creating homework projects
    focused on reactivity, stores, server-side rendering, and transitions. This
    hands-on approach helps deepen understanding of modern frontend frameworks.
  </p>

  <h3 class="text-xl font-semibold mb-1">Additional Experience</h3>
  <p class="text-gray-700 indent-3">
    Well-versed in JavaScript ES6+, jQuery & AJAX for dynamic web apps, UI
    design with Bootstrap & Framework7, and real-time communication via MQTT.
    Experienced with mobile app development using Cordova and enhancing UX with
    SweetAlert2.
  </p>
</section>

<!-- CONTACT -->
<section id="contact" class="py-20 px-6 bg-gray-50 max-w-3xl mx-auto">
  <h2 class="text-3xl font-bold mb-4">Contact</h2>
  <ul class="space-y-2 text-gray-700">
    <li>
      Email: <a
        href="mailto:kaloyanand@gmail.com"
        class="text-blue-600 underline">kaloyanand@gmail.com</a
      >
    </li>
    <li>
      Phone: <a href="tel:+359899802330" class="text-blue-600 underline"
        >+359899802330</a
      >
    </li>
    <li>
      LinkedIn:
      <a
        href="https://linkedin.com/in/kaloyan-andreev-6a52a6220"
        class="text-blue-600 underline"
        target="_blank"
        rel="noopener noreferrer"
      >
        linkedin.com/in/kaloyan-andreev
      </a>
    </li>
    <li>
      GitHub:
      <a
        href="https://github.com/KaloyanAnd"
        class="text-blue-600 underline"
        target="_blank"
        rel="noopener noreferrer"
      >
        github.com/KaloyanAnd
      </a>
    </li>
    <li>Location: Varna, Bulgaria</li>
  </ul>
</section>
<footer class="bg-gray-900 text-gray-300 py-6 text-center mt-12">
  <p>
    &copy; {new Date().getFullYear()} Kaloyan Andreev. All rights reserved.
  </p>
  <p class="mt-2">
    Contact:
    <a href="mailto:kaloyanand@gmail.com" class="text-blue-500 hover:underline">
      kaloyanand@gmail.com
    </a>
  </p>
</footer>
