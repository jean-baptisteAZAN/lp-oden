<script>
	import { onMount, onDestroy } from "svelte";
	import { gsap } from "gsap";
	import { ScrollTrigger } from "gsap/dist/ScrollTrigger";

	gsap.registerPlugin(ScrollTrigger);

	let myST;

	onMount(() => {
		const container = document.querySelector(".our-work");
		const slides = gsap.utils.toArray(".carousel__item");
		const tl = gsap.timeline();

		myST = ScrollTrigger.create({
			animation: tl,
			id: "st",
			trigger: container,
			start: "top top",
			end: "+=" + container.clientHeight * (slides.length - 1),
			pin: container,
			scrub: true,
			snap: {
				snapTo: 1 / (slides.length - 1)
			},
			markers: false
		});

		gsap.set(slides, {
			xPercent: 0,
			yPercent: 100,
			scale: 0.5,
			opacity: 0
		});

		slides.forEach((slide, i) => {
			const previousSlide = slides[i - 1];
			if (previousSlide) {
				tl.to(slide, { opacity: 1, yPercent: 0, scale: 1 }, 0.5 * (i - 1))
					.to(previousSlide, { opacity: 0, yPercent: -100, scale: 0.5 }, "<");
			} else {
				gsap.to(slide, { yPercent: 0, opacity: 1, scale: 1, duration: 0 });
			}
		});
	});

	onDestroy(() => {
		if (myST) {
			myST.kill();
		}
	});
</script>


<style>
    section {
        height: 100vh;
    }

    .our-work {
        display: flex;
        align-items: center;
        justify-content: center;
        background-position: center;
        background-size: cover;
        position: relative;
        overflow: hidden;
    }

    .carousel__slider {
        position: relative;
        width: 100%;
        min-height: 440px;
    }

		.carousel__item {
			width: 100%;
			min-height: 440px;
			padding: 24px;
			background: rgba(255, 255, 255, 0.1);
			border: 1px solid rgba(255, 255, 255, 0.2);
			border-radius: 16px;
			position: absolute;
			top: 0;
				left: 0;
				right: 0;
				margin: auto;
			opacity: 0;

    }
		@media (min-width: 1280px) {
			.carousel__item {
					width: 80%;
					min-height: 440px;
					padding: 48px;
					background: rgba(255, 255, 255, 0.1);
					border: 1px solid rgba(255, 255, 255, 0.2);
					border-radius: 16px;
					position: absolute;
					top: 0;
					left: 0;
					right: 0;
					margin: auto;
					opacity: 0;
			}

    }
</style>

<section class="our-work" id="how_it_works">
	<div class="container sticky">
		<h2 class="text-3xl xl:text-5xl text-center xl:mb-40 mb-20">
			Comment ça marche ?
		</h2>
		<div class="carousel__slider">
			<div class="carousel__item" id="our-work-1">
				<h2 class="h3 xl:h2">
					👋 On se rencontre ? - Établissement de vos besoins
				</h2>
				<h5 class="pr-20 mt-8">
					Tout commence par une discussion.<br/> Nous prenons le temps de comprendre vos besoins spécifiques et les particularités de votre école afin de créer une application qui vous ressemble.
				</h5>
				<h3 class="absolute bottom-5 right-5 h3">
					1/4
				</h3>
			</div>
			<div class="carousel__item" id="our-work-2">
				<h2 class="h3 xl:h2">
					🤔 Choisir la formule la plus adaptée
				</h2>
				<h5 class="h5 pr-20 mt-8">
					Explorez nos formules conçues pour répondre aux exigences variées des établissements. <br/>Chaque formule est une base que nous personnalisons pour refléter fidèlement l'identité de votre campus.
					<br/>L'application que nous allons concevoir ensemble sera unique, à l'image de votre école.
				</h5>
				<h3 class="absolute bottom-5 right-5 h3">
					2/4
				</h3>
			</div>
			<div class="carousel__item" id="our-work-3">
				<h2 class="h3 xl:h2">
					🤝 On fait le point régulièrement pendant que nous nous occupons du développement de l'application
				</h2>
				<h5 class="pr-20 mt-8">
					Pour correspondre à vos attentes, nous vous tenons informés de l'avancement du projet. <br/>Nous vous sollicitons régulièrement pour obtenir votre avis et vos retours.
					<br/>Le processus de développement prend en moyenne 2 semaines à 1 mois, selon la complexité de votre personnalisation.
					Dans ce laps de temps, nous mettons en place l'application, la rendons disponible sur l'App Store, et vous formons à son utilisation.
				</h5>
				<h3 class="absolute bottom-5 right-5 h3">
					3/4
				</h3>
			</div>
			<div class="carousel__item" id="our-work-4">
				<h2 class="h3 xl:h2">
					🚀 Lancez votre application
				</h2>
				<h5 class="pr-20 mt-8">
					Une fois que vous êtes satisfait de l'application, nous la lançons sur l'App Store. <br/>Vous pouvez alors la partager avec vos étudiants et commencer à profiter de ses avantages.<br/>
					Nous restons à votre disposition pour toute questions, modifications ou améliorations que vous souhaiteriez apporter à votre application.
					<br/>Nous sommes là pour vous accompagner dans la durée.
				</h5>
				<h3 class="absolute bottom-5 right-5 h3">
					4/4
				</h3>
			</div>
		</div>
	</div>
</section>
