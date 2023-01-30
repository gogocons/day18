<script lang="ts">
  import { onMount } from "svelte";

  type NFT = {
    name: string;
    description: string;
  };

  let nfts: NFT[] = [];

  function nft(name: string, description: string) {
    this.name = name;
    this.description = description;
  }

  let number = 1;

  function makeNewNft() {
    nfts.push(new nft("RUGGY BOIZ", `NFT NUMBER ${number}, GOING QUICK!`));
    number = number + 1;
    nfts = nfts;
  }

  onMount(() => {
    setInterval(makeNewNft, 250);
  });
</script>

<div class="nfts">
  {#each nfts as nft}
    <div class="nft">
      <h2>{nft.name}</h2>
      <p>{nft.description}</p>
    </div>
  {:else}
    <p>Mints not done, not even started...</p>
  {/each}
</div>

<style>
  .nfts {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    grid-gap: 8px;
  }

  .nft {
    border: 2px solid red;
    border-radius: 5px;
  }
</style>
