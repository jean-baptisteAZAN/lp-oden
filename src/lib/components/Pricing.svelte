<script lang="ts">
	import { contactPopup } from '$lib/utils/store';
	import { BadgeCheck } from 'lucide-svelte';

	let name = "";
	let price = 0;
	let index	= 0;
	const arr = [
		{
			name: "Starter",
			price: 249,
			options: [
				"250 utilisateurs",
				"1000 photos / mois",
				"Fonctionnalités de base (Décrite dans le bloc \"À quoi ça ressemble ? \")",
			],
		},
		{
			name: "Standard",
			price: 499,
			options: [
				"500 utilisateurs",
				"5000 photos&nbsp;/&nbsp;mois",
				"1 fonctionnalité personnalisé",
				"Charte graphique personnalisée",
				"Fonctionnalités de base (Décrite dans le bloc \"À quoi ça ressemble ? \")",
			],
		},
		{
			name: "Premium",
			price: 799,
			options: [
				"utilisateurs illimités",
				"30&nbsp000 photos&nbsp;/&nbsp;mois",
				"4 fonctionnalités personnalisées",
				"Charte graphique personnalisée",
				"Fonctionnalités de base (Décrite dans le bloc \"À quoi ça ressemble ? \")"
			],
		}
	];
</script>


<div class="w-full p-4 md:p-16 ">
	<div class="card p-3 md:p-10">
		<p class="h2 font-semibold text-center md:text-left">
			Nos formules
		</p>
		<div class="flex flex-col md:flex-row items-center">
			<div class="w-full md:w-[70%] flex flex-col items-center justify-center">
				<div class="w-full [&>.logo-item]:variant-filled logo-cloud grid-cols-1 lg:!grid-cols-3 gap-1">
					{#each arr as plan, i}
						<a on:click={() => index = i} class="logo-item">
							<span>{plan.name}</span>
						</a>
					{/each}
				</div>
				<div class="flex flex-col items-start justify-start w-full py-4">
					{#each arr[index].options as option}
						<div class="flex flex-row gap-2 items-center">
							<BadgeCheck class="variant-filled-primary rounded-token p-0.5"/>
							<span class="md:h4">
								{@html option}
							</span>
						</div>
					{/each}
				</div>
			</div>
			<div class="w-auto h-full flex flex-col gap-2 md:pl-10">
				<p class="font-semibold text-4xl">
					{arr[index].name}
				</p>
				<p >
					À partir de
				</p>
				<p class="h1 font-bold">
					{arr[index].price} € / ans
				</p>
				<button on:click={()=> contactPopup.set(true)} class="btn btn-hover variant-filled w-full">
					Demandez un devis
				</button>
				<blockquote class="blockquote">
					* Cette grille de prix sert de référence et peut varier en fonction de vos besoins et de vos choix de personnalisation.<br/>
					Elle nous permet de vous donner une idée du coût de votre application mobile.
				</blockquote>
			</div>
		</div>
	</div>
</div>
