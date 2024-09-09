<script lang="ts">
	import { BadgeCheck } from 'lucide-svelte';
	import { contactPopup } from '$lib/utils/store';
</script>

<div class="container mx-auto max-w-screen-lg pt-40">
	<div class=" flex flex-row items-center justify-center">
		<div class="space-y-4 md:col-span-6 p-4 md:w-1/2">
			<h1 class="text-3xl md:text-5xl font-bold">
				La première appli mobile <span class="relative px-1 md:px-3 bg-surface-300-600-token"
					>100%</span
				> dédiée pour les étudiants
			</h1>
			<p class="max-w-xl opacity-60">
				Nous développons des applications sur mobile pour les écoles et les associations étudiantes.
				Notre objectif est de vous aider à gérer vos associations étudiantes et de faciliter la vie
				étudiante.
			</p>
			<ul class="list-items">
				<li>
					<span><BadgeCheck class="variant-filled-primary rounded-token p-0.5" /></span>
					<span>
						<b>Notre promesse</b> – Simplifiez la vie de votre campus avec une application unique et
						personnalisée !
					</span>
				</li>
				<li>
					<span><BadgeCheck class="variant-filled-primary rounded-token p-0.5" /></span>
					<span>
						<b>Un seul canal pour toute l'école</b> - L'application mobile dédiée à votre école : toutes
						vos associations à portée de main.
					</span>
				</li>
				<li>
					<span><BadgeCheck class="variant-filled-primary rounded-token p-0.5" /></span>
					<span>
						<b>Connectez vos étudiants. Dynamisez votre campus.</b>
					</span>
				</li>
			</ul>
			<div class="flex flex-wrap gap-4">
				<button
					on:click={() => contactPopup.set(true)}
					class="btn md:btn-lg w-full md:w-fit variant-filled-primary"
				>
					Nous contacter
				</button>
				<a href="#how_it_works" class=" w-full md:w-fit">
					<button class="btn md:btn-lg w-full md:w-fit variant-filled-surface">
						Comment ça marche ?
					</button>
				</a>
			</div>
		</div>
		<img src="/HeroPhone.png" alt="design components" class="hidden md:block w-1/2 pl-40" />
	</div>
</div>

<style>
	.list-items li {
		display: flex;
		gap: 16px;
		padding: 12px 0px;
	}
</style>
