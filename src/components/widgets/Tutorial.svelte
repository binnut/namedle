<script lang="ts">
	import { COLS, ROWS } from "../../utils";

	import { Tile } from "../board";
	export let visible: boolean;
</script>

<h3>how to play</h3>
<div>Guess the <s>WORDLE</s><strong>NAME</strong> in {ROWS} tries.</div>
<div>Each guess must be a valid {COLS} letter name or shorter. In case of a shorter name, fill in with "*" at the end. Hit the enter button to submit.</div>
<div>
	After each guess, the color of the tiles will change to show how close your guess was to the
	word.
</div>
<div class:complete={visible} class="examples">
	<div><strong>Examples</strong></div>
	<div class="row">
		<Tile value="a" state="🟩" />
		<Tile value="n" state="🔳" />
		<Tile value="n" state="🔳" />
		<Tile value="a" state="🔳" />
		<Tile value="*" state="🔳" />
	</div>
	<div>The letter <strong>E</strong> is in the name and in the correct spot.</div>
	<div class="row">
		<Tile value="a" state="🔳" />
		<Tile value="l" state="🟨" />
		<Tile value="b" state="🔳" />
		<Tile value="i" state="🔳" />
		<Tile value="n" state="🔳" />
	</div>
	<div>The letter <strong>L</strong> is in the name but in the wrong spot.</div>
	<div class="row">
		<Tile value="e" state="🔳" />
		<Tile value="l" state="🔳" />
		<Tile value="i" state="🔳" />
		<Tile value="a" state="⬛" />
		<Tile value="s" state="🔳" />
	</div>
	<div>The letter <strong>A</strong> is not in the name in any spot.</div>
</div>
<div>
	This is based on a recreation of the original <a
		href="https://www.nytimes.com/games/wordle/"
		target="_blank"
		rel="noreferrer">Wordle</a
	>
	by Josh Wardle with additional modes and features, allowing you to play infinite wordles. Switch
	to infinite mode to play an unlimited number of times.
	<br /><br />
	Open the settings menu to see some of the additional features.
	<br />
	Based on version Written with Svelte, in Typescript by
	<a href="https://github.com/MikhaD" target="_blank" rel="noreferrer">MikhaD</a>.
	Edited for use as baby name reveal by 
	<a href="https://github.com/binnut" target="_blank" rel="noreferrer">Binnut</a>.

</div>

<style lang="scss">
	div {
		margin: 14px 0;
	}
	.examples {
		border-top: 1px solid var(--border-primary);
		border-bottom: 1px solid var(--border-primary);
		:global(.row > *) {
			height: 100%;
			aspect-ratio: 1;
		}
		&:not(.complete) :global(.row .back) {
			transition-delay: 0.3s;
		}
	}
	.row {
		height: 40px;
		display: flex;
		gap: 4px;
	}
</style>
