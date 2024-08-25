<script>
	import HeroSection from '$lib/components/HeroSection.svelte';
	import Features from '$lib/components/Features.svelte';
	import HowItWorks from '$lib/components/HowItWorks.svelte';
	import HowItLooks from '$lib/components/HowItLooks.svelte';
	import Pricing from '$lib/components/Pricing.svelte';
	import { contactPopup } from '$lib/utils/store';
</script>

<HeroSection />
<Features />
<HowItWorks />
<HowItLooks />
<Pricing />
<div class="flex flex-col items-center justify-center p-20 gap-10">
	<div class="space-y-5 text-center">
		<h1 class="h1">Alors ? Convaincu ?</h1>
		<p class="h3">
			Rejoignez-nous dès maintenant et crée le premier espace digital 100% à l'image de votre école
		</p>
	</div>
	<button
		on:click={() => contactPopup.set(true)}
		class="btn btn-hover variant-filled text-4xl hover:"
	>
		Contactez-nous
	</button>
</div>
