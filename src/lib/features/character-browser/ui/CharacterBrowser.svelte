<script lang="ts">
	import { CharacterList } from '$lib/features/character-list';
	import { CharacterSearch } from '$lib/features/character-search';
	import type { CharacterBrowserData } from '../model';

	export let data: CharacterBrowserData;
	export let onQueryChange: (value: string) => void;
</script>

<div class="main-container">
	<section class="hero">
		<div class="eyebrow">Actividad 3 · Desarrollo Frontend</div>
		
		<h1>Explorador de personajes: <span>Rick and Morty</span> para la Actividad 3.</h1>
		
		<p class="description">
			Implementación de arquitectura limpia (feature-first) conectando con la API oficial 
			para la gestión y búsqueda de personajes.
		</p>
	</section>

	<div class="panel">
		<CharacterSearch query={data.query} onQueryChange={onQueryChange} />

		<div class="meta">
			<p class="count">{data.total} personajes encontrados</p>
			{#if data.error}
				<p class="error">{data.error}</p>
			{/if}
		</div>

		{#if data.characters}
			<div class="list-wrapper">
				<CharacterList characters={data.characters} />
			</div>
		{/if}
	</div>
</div>

<style>
	.main-container {
		min-height: 100vh;
		background-color: #f8fafc;
		font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
	}

	section.hero {
		max-width: 960px;
		margin: 0 auto;
		padding: 4rem 1.25rem 1.5rem;
	}

	.eyebrow {
		display: inline-flex;
		padding: 0.4rem 0.8rem;
		border-radius: 6px;
		background: #1e293b;
		color: #4ecdc4;
		font-weight: 700;
		font-size: 0.7rem;
		text-transform: uppercase;
		margin-bottom: 1rem;
		letter-spacing: 0.05em;
	}

	h1 {
		max-width: 20ch;
		margin: 0.5rem 0 1.5rem;
		font-size: clamp(2.2rem, 7vw, 4rem);
		line-height: 1;
		color: #0f172a;
		letter-spacing: -0.03em;
	}

	h1 span {
		background: linear-gradient(120deg, #4ecdc4, #3b82f6);
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		display: inline-block;
	}

	.description {
		max-width: 60ch;
		margin: 0;
		color: #64748b;
		font-size: 1.1rem;
		line-height: 1.6;
		border-left: 4px solid #4ecdc4;
		padding-left: 1.5rem;
	}

	.panel {
		max-width: 960px;
		margin: 0 auto;
		padding: 2rem 1.25rem 4rem;
	}

	.meta {
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-top: 2rem;
		padding: 1rem 0;
		border-top: 1px solid #e2e8f0;
	}

	.count {
		font-size: 0.9rem;
		font-weight: 600;
		color: #94a3b8;
		margin: 0;
	}

	.list-wrapper {
		margin-top: 1rem;
	}

	/* Micro-interacción suave para las tarjetas */
	:global(.character-card) {
		transition: all 0.25s ease-out !important;
	}
	
	:global(.character-card:hover) {
		transform: translateY(-5px);
		filter: brightness(1.05);
	}

	.error {
		color: #ef4444;
		font-weight: bold;
	}
</style>