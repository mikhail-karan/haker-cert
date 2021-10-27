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

<main
  class="prose lg:prose-xl flex flex-col justify-center h-screen items-center"
>
  {#if !accepted}
    <h1>Are you a HTML Haker?</h1>
    <input
      bind:value={text}
      on:keydown={submitCode}
      type="text"
      placeholder="Whats the code?"
      class="input text-xl text-white"
    />
  {:else}
    <div bind:this={canvas} class="bg-base-100 p-8">
      <div
        
        class="card bordered bg-primary shadow-xl text-white"
      >
        <div class="card-body">
          <h2 class="card-title text-white">
            Congratulations! 🏆
            <!-- <div class="badge mx-2 badge-secondary">NEW</div> -->
          </h2>
          <p>
            You're now offically a haker and have joined the ultra exclusive guild
            of the hake
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

  img {
    height: 16rem;
    width: 16rem;
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
