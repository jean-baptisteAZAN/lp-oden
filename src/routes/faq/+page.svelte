<script lang="ts">
	import { Accordion, AccordionItem } from '@skeletonlabs/skeleton'

	interface FAQ {
		icon: string;
		question: string;
		text: string;
	}
	const faqs: FAQ[] = [
		{
			icon: "🎓",
			question: "Qu'est-ce que cette application offre aux associations étudiantes ?",
			text: "Notre application fournit une plateforme centralisée où chaque association peut créer et gérer son propre espace. Les associations peuvent publier des événements 📅, interagir avec les étudiants via des sondages 📊, et communiquer rapidement avec l'ensemble du campus."
		},
		{
			icon: "🎨",
			question: "L'application est-elle personnalisable pour chaque école ?",
			text: "Oui, l'application est hautement personnalisable. Nous proposons plusieurs formules de base que nous adaptons selon les besoins spécifiques de votre école, en intégrant les couleurs, le logo, et les fonctionnalités requises pour refléter l'identité de votre établissement."
		},
		{
			icon: "📱",
			question: "Comment les étudiants peuvent-ils accéder à l'application ?",
			text: "L'application est disponible en téléchargement sur l'App Store et Google Play. Une fois installée, les étudiants peuvent se connecter avec leurs identifiants scolaires ou s'inscrire directement via l'application."
		},
		{
			icon: "🎉",
			question: "Comment puis-je créer un événement pour mon association ?",
			text: "Créer un événement est simple et rapide. Depuis votre espace association, il suffit de cliquer sur 'Créer un événement', de remplir les détails pertinents comme la date, le lieu, et la description, puis de publier. L'événement sera visible pour tous les étudiants de l'école."
		},
		{
			icon: "🔒",
			question: "L'application est-elle sécurisée ?",
			text: "Absolument. Nous utilisons des protocoles de sécurité avancés pour protéger toutes les données des utilisateurs et des associations. Les informations personnelles et les communications sont chiffrées pour garantir la confidentialité."
		},
		{
			icon: "🛠️",
			question: "Que se passe-t-il si nous rencontrons un problème avec l'application ?",
			text: "Notre équipe de support est disponible à tout moment pour vous aider. Vous pouvez nous contacter directement via l'application ou par email. Nous nous engageons à résoudre tout problème dans les plus brefs délais."
		},
		{
			icon: "⏳",
			question: "Combien de temps faut-il pour mettre l'application en ligne après validation ?",
			text: "Une fois que toutes les personnalisations et modifications sont validées, l'application peut être mise en ligne sous quelques jours. Nous vous tiendrons informé de chaque étape jusqu'à la disponibilité de l'application sur les stores."
		},
		{
			icon: "🗳️",
			question: "Quels types de sondages peuvent être créés dans l'application ?",
			text: "Vous pouvez créer des sondages pour obtenir des retours rapides sur n'importe quel sujet, qu'il s'agisse d'organiser des événements, de recueillir des avis sur une décision à prendre, ou de simplement engager votre communauté étudiante. Les résultats sont visibles en temps réel."
		},
		{
			icon: "🚀",
			question: "L'application peut-elle évoluer avec les besoins de notre école ?",
			text: "Oui, l'application est conçue pour évoluer avec vous. Nous offrons des mises à jour régulières et pouvons ajouter de nouvelles fonctionnalités ou adapter les existantes en fonction des besoins changeants de votre école."
		},
		{
			icon: "💰",
			question: "Y a-t-il des frais supplémentaires pour les mises à jour futures ?",
			text: "Cela dépend du plan choisi. Certaines mises à jour, comme les correctifs de sécurité, sont incluses. Pour des fonctionnalités ou des personnalisations supplémentaires, des frais peuvent s'appliquer. Nous vous fournirons toujours un devis avant d'entreprendre toute modification majeure."
		}
	];
</script>

	<div class="text-center mb-10 text-3xl font-bold pt-20">
		Questions fréquentes
	</div>
	<div class="flex items-center justify-center px-5 md:px-80">
		<Accordion spacing="space-y-3" autocollapse>
			{#each faqs as item}
				<AccordionItem
					class="bg-surface-50-900-token rounded-container-token p-2 border border-surface-300-600-token"
				>
					<svelte:fragment slot="lead">
						{item.icon}
					</svelte:fragment>
					<svelte:fragment slot="summary">{item.question}</svelte:fragment>
					<svelte:fragment slot="content">{item.text}</svelte:fragment>
				</AccordionItem>
			{/each}
		</Accordion>
	</div>
