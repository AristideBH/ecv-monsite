<script>
	import ContactBtn from '$lib/components/items/ContactBtn.svelte';
	import DataNumber from '$lib/components/items/DataNumber.svelte';
	import PanelWrapper from '$lib/components/items/PanelWrapper.svelte';
	import ViewMore from '$lib/components/items/ViewMore.svelte';
	import ObjectiveCard from '$lib/components/items/ObjectiveCard.svelte';

	import { t } from '$lib/i18n';
	import { news } from '$lib/news';
	import { objectives } from '$lib/objectives';
</script>

<svelte:head>
	<title>Mi2 | {$t('homepage.title')}</title>
</svelte:head>

<!-- # HERO -->
<section id="hero">
	<video autoplay loop muted>
		<source src="/hero.mp4" type="video/mp4" />
	</video>

	<div class="container">
		<hgroup>
			<h1>{$t('homepage.title')}</h1>
			<h2>{@html $t('homepage.welcome', { name: 'Guillaume' })}</h2>
		</hgroup>
		<ContactBtn />
	</div>

	<ViewMore />
</section>

<!-- # PRODUCTS -->
<section id="products" class="container">
	<span class="grid">
		<code class="3D--wrapper">3D Object</code>

		<div>
			<h2>Des produits innovants, naturels, et non-nocifs</h2>
			<p>
				Lorem, ipsum dolor sit amet consectetur adipisicing elit. Placeat facilis sequi explicabo
				magnam, sit qui nostrum adipisci alias excepturi suscipit similique cum ipsam dolor possimus
				iste, fugit culpa ab nulla!
			</p>
		</div>
	</span>
</section>

<!-- # RSE -->
<section id="rse" class="container">
	<h2>M2i Group annonce ses objectifs</h2>
	<p>
		Lorem ipsum dolor sit, amet consectetur adipisicing elit. Incidunt, fugit ab expedita accusamus
		non voluptatum ea, ratione autem repudiandae cupiditate aliquam. Laboriosam, saepe ipsa qui
		neque similique magnam quam veritatis?
	</p>

	<div class="autoGrid">
		{#each objectives as objective}
			<ObjectiveCard {...objective} />
		{/each}
	</div>
</section>

<!-- # DATA -->
<section id="data">
	<div class="container flex:col">
		<div class="title flex:col">
			<h2>Quelques chiffres</h2>
			<p>
				Lorem ipsum dolor sit amet, consectetur adipisicing elit. Temporibus eaque velit veniam
				animi maiores vitae, suscipit impedit, distinctio ab dolorem repudiandae illum totam
				recusandae laborum! Minima officia voluptatibus amet corporis?
			</p>
		</div>
		<ul class="autoGrid">
			<DataNumber options={{ data: 9000, ico: '/picto/1.png', subtitle: 'text 1' }} />
			<DataNumber options={{ data: 30, ico: '/picto/2.png', subtitle: 'text 2' }} />
			<DataNumber options={{ data: 600, ico: '/picto/2.png', subtitle: 'text 3' }} />
		</ul>
		<a href="/" class="mx:auto" role="button"> d??couvrir le reste</a>
	</div>
</section>

<!-- # NEWS -->
<section id="news" class="container">
	<span class="flex:col">
		<h2>Actualit??s</h2>
		<PanelWrapper {news} />
		<a class="mx:auto" role="button" href="/">Voir toutes les actus</a>
	</span>
</section>

<style lang="scss">
	#hero {
		position: relative;
		overflow: hidden;
		height: 100vh;
		display: flex;
		align-items: center;
		margin-top: calc(var(--header-height) * -1);

		video {
			width: 100%;
			height: 100%;
			object-fit: cover;
			position: absolute;
			top: 0;
		}

		.container {
			z-index: 3;
			position: relative;
			* {
				--color: var(--primary-inverse);
			}
		}
	}

	#products .grid {
		--grid-spacing-horizontal: 3rem;
		--grid-spacing-vertical: 1.5rem;
	}

	#data {
		padding-block: 4rem;
		background-color: var(--code-background-color);

		.title {
			align-items: center;
			text-align: center;
			padding-bottom: 1rem;

			p {
				max-width: max(640px, 65vh);
			}
		}
	}
</style>
