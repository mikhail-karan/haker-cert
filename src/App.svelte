<script>
  import html2canvas from "html2canvas";
  console.log("The code is: Razelfrazel");
  let text = "";
  let accepted = false;
  let canvas;

  function submitCode() {
    if (text === "Razelfrazel") {
      accepted = true;
    }
  }
  function downloadCert() {
    html2canvas(canvas).then(function (canvas) {
      let a = document.createElement("a");
      a.href = canvas.toDataURL("image/png");
      a.download = "certificate.png";
      a.click();
    });
  }
</script>

<div
  class="w-full absolute bg-[#4aa1d9] flex flex-row items-center justify-between text-white p-2 shadow-md"
>
  <div class="flex flex-row items-center">
    <p class="flex xs:hidden ">Brought to you by</p>
    <a
      class="ml-2 underline hover:text-purple-600"
      href="https://www.htmlallthethings.com/">HTML All The Things</a
    >
  </div>
  <div class="flex flex-row text-2xl">
    <a
      class="flex items-center mr-3 hover:text-blue-600"
      href="https://github.com/mikhail-karan"><i class="lab la-github" /></a
    >
    <a
      class="flex items-center mr-3 hover:text-blue-600"
      href="https://discord.com/invite/jweMCx9"><i class="lab la-discord" /></a
    >
    <a
      class="flex items-center hover:text-blue-600"
      href="https://twitter.com/htmleverything"><i class="lab la-twitter" /></a
    >
  </div>
</div>
<main
  class="prose lg:prose-xl flex flex-col justify-center h-screen items-center"
>
  {#if !accepted}
    <h1>Are you a HTML Haker?</h1>
    <input
      bind:value={text}
      on:keydown={submitCode}
      type="text"
      placeholder="Enter the code"
      class="input text-xl text-white text-center"
    />
  {:else}
    <div bind:this={canvas} class="bg-base-100 p-8">
      <div class="card bordered bg-primary shadow-xl text-white">
        <div class="card-body">
          <h2 class="card-title text-white">
            Congratulations! 🏆
            <!-- <div class="badge mx-2 badge-secondary">NEW</div> -->
          </h2>
          <p class="text-xl">
            You're now offically a haker and have joined the ultra exclusive
            guild of the hake
          </p>
          <!-- <div class="justify-end card-actions">
            <button class="btn btn-secondary"></button>
          </div> -->
        </div>
      </div>
    </div>

    <button on:click={downloadCert} class="btn btn-secondary my-5"
      >Download Membership Card</button
    >
  {/if}
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
      Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  }

  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4rem;
    font-weight: 100;
    line-height: 1.1;
    margin: 2rem auto;
    max-width: 14rem;
  }

  h2 {
    color: #fff !important;
  }

  p {
    max-width: 14rem;
    margin: 1rem auto;
    line-height: 1.35;
  }

  @media (min-width: 480px) {
    h1 {
      max-width: none;
    }

    p {
      max-width: none;
    }
  }
</style>
