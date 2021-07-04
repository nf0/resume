<script lang="ts">
  import { onMount } from "svelte"

  import Tailwind from "./Tailwind.svelte"
  import Intro from "./Intro.svelte"
  import Work from "./Work.svelte"

  const introData = {
    name: "Satawat Khanthahom",
    nickname: "Bee",
    phone: "",
    email: "nfo@pm.me",
    github: "nf0",
    linkedin: "satawat-khanthahom-541377169",
    location: "Chiang Mai, Thailand",
    website: "nf0.cc",
  }

  const workExperiences = [
    {
      position: "Part-time Software Developer",
      company: "Magic Box Asia",
      url: "https://www.magicboxasia.com/",
      years: ["April 2021", "July 2021"],
    },
    {
      position: "Software Developer",
      company: "20Scoops CNX",
      url: "https://20scoopscnx.com/",
      years: ["April 2020", "October 2020"],
    },
    {
      position: "Part-time IT Project Coordinator",
      company: "Kaltura (Singapore)",
      url: "https://corp.kaltura.com/",
      years: ["October 2019", "March 2020"],
      details: [
        "Performed risk management to minimize project risks.",
        
        "Coordinated with internal and external various teams to achieve project goals.",
      ],
    },
    {
      position: "Software Developer",
      company: "SeedThemes",
      url: "https://seedthemes.com/",
      years: ["November 2018", "2019"],
      details: [
        "Implemented features, functions, themes for WordPress based websites",
        "Managed and updated CMS functionalities ",
        "Managed multilingual, membership and eCommerce (WooCommerce) websites",
      ],
    },
    {
      position: "Part-Time Web Developer & IT Support",
      company: "UD Town",
      url: "https://www.goudtown.com",
      years: ["2012", "2013"],
      details: [
        "Implemented internal websites",
        "Managed and maintained network, server, and PC health for staffs",
        "Monitored and maintained all levels of network security internally and externally",
        "Identified, diagnosed, and resolved network problems"
      ],
    },
  ]

  const projects = [
    {
      name: "",
      details:
        "",
      url: "",
    },
  ]

  const interests = [
    "Areas : Coding, Productivity",
    "Games : Music games, FPS",
    "Music : EDM, Indie, Ambient, Downtempo ",
    "DJ : Scratching, Club Mixing ",
  ]

  const fullVersionLink = "https://manassarn-resume.vercel.app"
  const sourceLink = "https://github.com/narze/resume"

  let kofiReady = false
  let mounted = false

  onMount(() => {
    // The payment-form is ready.
    mounted = true
    if (kofiReady) {
      loadKofiWidget()
    }
  })

  function kofiLoaded() {
    // The external Kofi javascript is ready.
    kofiReady = true
    if (mounted) {
      loadKofiWidget()
    }
  }

  function loadKofiWidget() {
    window.kofiWidgetOverlay!.draw(
      "narze",
      {
        type: "floating-chat",
        "floating-chat.donateButton.text": "Support me",
        "floating-chat.donateButton.background-color": "#00b9fe",
        "floating-chat.donateButton.text-color": "#fff",
      },
      "kofiContainer"
    )
  }
</script>

<svelte:head>
  <script
    type="text/javascript"
    src="https://storage.ko-fi.com/cdn/scripts/overlay-widget.js"
    on:load={kofiLoaded}></script>
</svelte:head>

<Tailwind />

<header
  class="web-only text-center p-4 sm:p-6 bg-green-400 text-white w-screen"
>
  <h1 class="text-4xl">Resumette</h1>
  <p>
    Printer-friendly standard résumé, any HTML tags with <code>web-only</code> CSS
    class will be hidden on print.
  </p>
  (<a href={sourceLink} target="_blank" rel="noopener">Source</a>)
</header>

<main class="text-center p-4 m-0 md:m-8 xl:mx-auto max-w-screen-xl">
  <Intro {...introData} />

  <section>
    <h2 class="text-2xl print:text-4xl uppercase text-left">
      Technologies and Languages
    </h2>
    <hr />
    <ul class="text-left list-disc pl-8">
      <li>
        <span class="w-28 inline-block">Languages:</span>
        <span>
          PHP, JavaScript, SQL (proficient).
        </span>
      </li>
      <li>
        <span class="w-28 inline-block">Frameworks:</span>
        <span>
         VueJS, Svelte, TailwindCSS, Bootstrap 
        </span>
      </li>
      <li>
        <span class="w-28 inline-block">Tools:</span>
        <span>
          Git, Docker, Kubernetes, Fish
        </span>
      </li>
      <li>
        <span class="w-28 inline-block">Other:</span>
        <span>
          AWS, GCP, Firebase, Vercel, DigitalOcean, Github Actions,CircleCI, CloudFlare
        </span>
      </li>
    </ul>
  </section>
  <section>
    <h2 class="text-2xl print:text-4xl uppercase text-left">Education</h2>
    <hr />

    <ul class="text-left list-disc pl-8">
      <li>
        <strong>B.Sc. Information Technology</strong>, Chiang Mai Rajabhat University,
        TH.
      </li>
    </ul>
  </section>
  <section>
    <h2 class="text-2xl print:text-4xl uppercase text-left">Work Experience</h2>
    <hr />

    {#each workExperiences as exp}
      <Work {...exp} />
    {/each}
  </section>
  <!-- 
  <section>
    <h2 class="text-2xl print:text-4xl uppercase text-left">Projects</h2>
    <hr />

    <ul class="text-left list-disc pl-8">
      {#each projects as project}
        <li>
          <strong>{project.name}</strong>
          - {project.details}
          <a href="https://{project.url}" target="_blank" rel="noreferrer"
            ><strong>{project.url}</strong></a
          >
        </li>
      {/each}
    </ul>
  </section>
  -->
  <section>
    <h2 class="text-2xl print:text-4xl uppercase text-left">Interests</h2>
    <hr />

    <ul class="text-left list-disc pl-8">
      {#each interests as interest}
        <li>
          {interest}
        </li>
      {/each}
    </ul>
  </section>

  <!--
  <img
    width="100"
    height="100"
    src={logo}
    alt="Svelte Logo"
    class="inline-block"
  />
  <h1
    class="text-6xl uppercase font-thin leading-tight my-8 mx-auto max-w-xs sm:max-w-xs"
  >
    Hello Vite!
  </h1>

  <Counter id="0" />

  <p class="max-w-xs sm:max-w-none my-4 mx-auto leading-5">
    Visit <a class="text-blue-600 underline" href="https://svelte.dev"
      >svelte.dev</a
    > to learn how to build Svelte apps.
  </p>

  <p class="max-w-xs sm:max-w-none my-4 mx-auto leading-5">
    Check out <a href="https://github.com/sveltejs/kit#readme">SvelteKit</a> for
    the officially supported framework, also powered by Vite!
  </p>
  -->
  <footer class="print-only">
    (See <a href={fullVersionLink} target="_blank" rel="noopener"
      >full version</a
    >
    or <a href={sourceLink} target="_blank" rel="noopener">source</a>)
  </footer>

  <div id="kofiContainer" class="web-only" />
</main>

<style>
  a {
    text-decoration: underline;
  }

  section {
    @apply my-4;
  }

  section h2 {
    @apply font-semibold;
  }

  section hr {
    @apply mt-0 mb-2;
    border-color: darkgrey;
  }

  .print-only {
    display: none;
  }

  .web-only {
    display: inherit;
  }

  @media print {
    * {
      @apply text-xs;
    }

    .print-only {
      display: inherit;
    }

    .web-only {
      display: none;
    }

    ul {
      @apply pl-6;
    }

    section {
      @apply my-2;
    }

    section hr {
      @apply mt-0 mb-1;
    }

    body,
    main {
      margin: 0 0;
      padding: 0;
    }
  }
</style>
