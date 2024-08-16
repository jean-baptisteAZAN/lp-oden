<script>
	import { Lightbulb, Cog, Smartphone } from 'lucide-svelte';
</script>

<div class="flex flex-col xl:flex-row items-center justify-center w-screen p-5 md:p-20 gap-5 md:gap-20 text-center">
	<div class="flex flex-col xl:w-1/3 items-center justify-center gap-8 card card-hover p-10">
		<Lightbulb size="80"/>
		<h3 class="h3">
			Facilitez la création d'événements
		</h3>
		<p>
			Créez et gérez vos événements associatifs en quelques clics. Informez et mobilisez toute votre école en un instant.
		</p>
	</div>
	<div class="flex flex-col xl:w-1/3 items-center justify-center gap-8 card card-hover p-10">
		<Cog size="80"/>
		<h3 class="h3">
			Personnalisez vos fonctionnalités
		</h3>
		<p>
			Choisissez les options qui conviennent le mieux à votre école et personnalisez l'application selon vos besoins spécifiques.
		</p>
	</div>
	<div class="flex flex-col xl:w-1/3 items-center justify-center gap-8 card card-hover p-10">
		<Smartphone size="80"/>
		<h3 class="h3">
			Accessible partout, à tout moment
		</h3>
		<p>
			Emportez votre école avec vous. Votre application est disponible sur tous les appareils, pour une accessibilité totale.
		</p>
	</div>
</div>
