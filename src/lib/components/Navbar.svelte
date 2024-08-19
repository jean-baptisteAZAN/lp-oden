<script lang="ts">
	import { LightSwitch } from '@skeletonlabs/skeleton';
	import { PhoneCall, Mailbox, Linkedin } from 'lucide-svelte';
	import { contactPopup } from '$lib/utils/store';

	function handleOutsideClick(event: MouseEvent) {
		const popupCard = document.querySelector('.card');
		if (popupCard && !popupCard.contains(event.target as Node)) {
			contactPopup.set(false);
		}
	}
</script>

<nav class="flex flex-row items-center justify-between p-3 left-0 top-0 right-0 mx-auto fixed backdrop-blur-lg z-50">
	<LightSwitch class="hidden md:block"/>
	<div class="flex flex-row">
		<a class="btn" href="/">
			<button type="button" class="bg-initial hover:scale-110 transition-all hover:underline duration-300">Accueil</button>
		</a>
		<a  class="btn" href="/faq">
			<button type="button" class="btn bg-initial hover:scale-110 transition-all hover:underline duration-300">FAQ</button>
		</a>
		<!-- Calendly badge widget begin -->
		<link href="https://assets.calendly.com/assets/external/widget.css" rel="stylesheet">
		<script src="https://assets.calendly.com/assets/external/widget.js" type="text/javascript" async></script>
		<script type="text/javascript">window.onload = function() { Calendly.initBadgeWidget({ url: 'https://calendly.com/jbazan-pro/30min?primary_color=e18fd5', text: 'Réserver une démo', color: '#f0a8dd', textColor: '#ffffff', branding: undefined }); }</script>
		<!-- Calendly badge widget end -->
		<button on:click={()=> contactPopup.set(true)} type="button" class="btn btn-md md:btn-lg variant-filled">
			Nous contacter
		</button>
	</div>
</nav>

{#if $contactPopup}
	<div on:click={handleOutsideClick} class="popup fixed inset-0 flex items-center justify-center bg-black bg-opacity-70 z-50">
		<div class="card p-5">
			<h2 class="h2 mb-5">Contactez-nous</h2>
			<div class="logo-cloud grid-cols-1 lg:!grid-cols-3 gap-1 [&>.logo-item]:variant-filled-primary">
				<a class="logo-item p-5" href="https://www.linkedin.com/company/oden-tech/" target="_blank">
					<span><Linkedin/></span>
					<span>Linkedin</span>
				</a>
				<a class="logo-item p-5" href="tel:+33642239623" target="_blank">
					<span><PhoneCall/></span>
					<span>Par téléphone</span>
				</a>
				<a class="logo-item p-5" href="mailto:jbazan.pro@gmail.com" target="_blank">
					<span><Mailbox/></span>
					<span>Par Mail</span>
				</a>
			</div>
		</div>
	</div>
{/if}
