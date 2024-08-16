<script>
	import { onMount } from 'svelte';
	import { ProgressBar } from '@skeletonlabs/skeleton';

	const wording = [
		{ title: 'Fil d\'actualité', desc: 'Le fil d\'actualité est une section centrale où tous les événements créés par chaque association sont rassemblés et affichés en temps réel.<br/> C’est ici que les utilisateurs peuvent consulter les dernières actualités des associations, telles que les annonces d\'événements à venir, et interagir directement en répondant aux sondages créés par ces associations.<br/> Ce fil d\'actualité permet de rester informé en un coup d\'œil de tout ce qui se passe au sein de l\'école, en favorisant l\'engagement des membres.' },
		{ title: 'Calendrier', desc: 'Le calendrier est un outil essentiel qui permet de visualiser de manière claire et organisée tous les événements planifiés au sein de l\'école. Il offre une vue d\'ensemble des activités et permet également de filtrer les événements selon les associations. Ainsi, que vous cherchiez à voir tous les événements de l\'école ou simplement ceux d\'une association spécifique, le calendrier offre une interface intuitive pour rester à jour et planifier votre participation.' },
		{ title: 'Espace avec toutes les associations', desc: 'Cet espace regroupe l\'ensemble des associations présentes au sein de l\'école. Il s’agit d’une sorte de répertoire interactif où chaque association est présentée avec ses objectifs, ses membres principaux, et ses activités récentes. Cet espace permet aux utilisateurs de découvrir les différentes associations, de comprendre leur rôle, et d’adhérer à celles qui correspondent à leurs centres d’intérêt.' },
		{ title: 'Espace dédié par association', desc: 'Chaque association dispose de son propre espace dédié, un environnement personnalisé où sont rassemblées toutes les informations pertinentes. Cet espace inclut la liste des membres, les événements planifiés, les sondages en cours, et les partenariats établis. C\'est un lieu où les membres de l\'association peuvent collaborer, partager des idées, et organiser des activités de manière centralisée et efficace.' },
		{ title: 'Messagerie instantanée', desc: 'La messagerie instantanée permet aux membres de communiquer en temps réel. Cet outil est conçu pour faciliter les échanges rapides entre les utilisateurs, qu\'il s\'agisse de discussions informelles, de coordination d\'événements, ou de réponses immédiates à des questions. Grâce à cette fonctionnalité, la collaboration au sein de l\'école est fluidifiée, renforçant ainsi la dynamique de communauté.' }
	];

	let currentIndex = 0;
	let currdeg = 0;
	let interval;
	const slideInterval = 5000;

	onMount(() => {
		startAutoSlide();
		return () => {
			clearInterval(interval);
		};
	});

	function startAutoSlide() {
		interval = setInterval(() => {
			rotateToIndex((currentIndex + 1) % wording.length);
		}, slideInterval);
	}

	function rotateToIndex(index) {
		const totalItems = wording.length;
		const anglePerItem = 360 / totalItems;
		currdeg = -index * anglePerItem;
		currentIndex = index;

		const carousel = document.querySelector('.carousel');
		const items = document.querySelectorAll('.item');
		carousel.style.transform = `rotateY(${currdeg}deg)`;
		items.forEach(item => {
			item.style.transform = `rotateY(${-currdeg}deg)`;
		});
	}
</script>

<h2 class="h2 text-center -mt-10 mb-20 md:-mt-20 md:mb-40">
	À quoi ça ressemble ?
</h2>

<div class="flex flex-col xl:flex-row px-8 md:px-20 xl:px-40 w-full">
	<div class="w-full xl:w-1/2 flex flex-col">
		<h3 class="text-3xl text-center md:text-left">
			{wording[currentIndex].title}
		</h3>
		<p class="xl:pr-20 text-2xl text-center md:text-left">
			{@html wording[currentIndex].desc}
		</p>
	</div>
	<div class="md:hidden flex flex-row items-center justify-center mt-10">
		<button on:click={() => rotateToIndex(currentIndex + 1)} class="btn variant-filled w-80">
			{wording[(currentIndex + 1)].title}
		</button>
	</div>
	<div class="hidden md:flex flex-col items-center justify-center w-full xl:w-1/2 lg:mt-20 2xl:mt-0">
		<div class="container">
			<div class="carousel">
				<div class="a">
					<img alt="Fil d'actualité" class="item" src="/features/4.png"/>
				</div>
				<div class="b">
					<img alt="Calendrier" class="item" src="/features/2.png"/>
				</div>
				<div class="c">
					<img alt="Espace avec toutes les associations" class="item" src="/features/3.png"/>
				</div>
				<div class="d">
					<img alt="Espace dédié par association" class="item" src="/features/1.png"/>
				</div>
				<div class="e">
					<img alt="Messagerie instantanée" class="item" src="/features/5.png"/>
				</div>
			</div>
		</div>
		<div class="flex flex-row items-center justify-center gap-5 mt-10">
			{#each Array(wording.length) as _, i}
				{#if i === currentIndex}
						<div class="w-20">
							<ProgressBar value={$interval} max={slideInterval} />
						</div>
				{:else}
					<button
						class="dot"
						on:click={() => rotateToIndex(i)}
						aria-label="Navigate to slide {i + 1}">
						•
					</button>
				{/if}
			{/each}
		</div>
	</div>
</div>

<style>
    .container {
        margin: 0 auto;
        width: 50rem;
        height: 30rem;
        position: relative;
				perspective: 1000px;
    }
		@media (max-width: 1324px) {
			.container {
					width: 35rem;
					height: 24rem;
					position: relative;
					perspective: 2000px;
      }
    }

    .carousel {
        height: 100%;
        width: 100%;
        position: absolute;
        transform-style: preserve-3d;
        transition: transform 1s;
    }
    .carousel div {
        transform-style: preserve-3d;
    }

    .item {
        display: block;
        position: absolute;
        transition: transform 1s;
    }

    .a {
        transform: rotateY(0deg) translateZ(250px);
    }
    .b {
        transform: rotateY(72deg) translateZ(250px) rotateY(-72deg);
    }
    .c {
        transform: rotateY(144deg) translateZ(250px) rotateY(-144deg);
    }
    .d {
        transform: rotateY(216deg) translateZ(250px) rotateY(-216deg);
    }
    .e {
        transform: rotateY(288deg) translateZ(250px) rotateY(-288deg);
    }

    .dot {
        font-size: 2rem;
        cursor: pointer;
        background: none;
        border: none;
        outline: none;
        padding: 0;
        transition: color 0.3s;
    }

    @keyframes progressBarAnimation {
        from {
            height: 0%;
        }
        to {
            height: 100%;
        }
    }
</style>
