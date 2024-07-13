<script>
	let textContent = '';

	function applyBold() {
		
	}

	function applyItalic() {
		
	}

	function applyUnderline() {
		
	}

	function applyStrikethrough() {
		
	}

	function alignLeft() {
		textarea.style.textAlign = 'left';
	}

	function alignRight() {
		textarea.style.textAlign = 'right';
	}

	function alignCenter() {
		textarea.style.textAlign = 'center';
	}

	function indentText() {
		const start = textarea.selectionStart;
		const end = textarea.selectionEnd;
		const selectedText = textContent.substring(start, end);
		const indentText = `\t${selectedText}`;
		textContent = textContent.substring(0, start) + indentText + textContent.substring(end);
	}

	function justifyText() {
		textarea.style.textAlign = 'justify';
	}

	function removeWord() {
		const words = textContent.split(' ');
		words.pop();
		textContent = words.join(' ');
	}
	function reverseWord() {
		const words = textContent.split(' ');
		if (words.length > 0) {
			const lastWord = words.pop();
			const reversedWord = lastWord.split('').reverse().join('');
			words.push(reversedWord);
			textContent = words.join(' ');
		}
	}
	function sortWord() {
    const words = textContent.split(' ');
    if (words.length > 0) {
        words.sort((a, b) => a.localeCompare(b));
        textContent = words.join(' ');
    }
}

	function copyText() {
		navigator.clipboard.writeText(textContent);
	}
</script>

<style>
	textarea {
		width: 100%;
		height: 200px;
		padding: 10px;
		background-color: #4a5568;
		color: white;
		border: none;
		border-radius: 8px;
		resize: none;
		font-size: 16px;
		margin-bottom: 20px;
	}
	
	button {
		background-color: #3182ce;
		color: white;
		border: none;
		padding: 10px 20px;
		border-radius: 8px;
		cursor: pointer;
		transition: background-color 0.3s;
	}
	
	button:hover {
		background-color: #2b6cb0;
	}
	
	.flex {
		display: flex;
		flex-wrap: wrap;
		gap: 10px;
	}
</style>

<div class="bg-gray-900 text-white flex flex-col items-center py-8 h-auto">
	<header class="mb-8">
		<h1 class="text-3xl font-bold">Text Toolkit</h1>
	</header>
	<div class="relative card w-full lg:w-2/3 mx-auto max-w-screen-xl p-6 bg-gray-800 shadow-md rounded-lg">
		<textarea bind:value={textContent} id="textarea" class="w-full h-64 p-4 bg-gray-700 text-white rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-600" placeholder="Type your text here..."></textarea>
		<div class="flex space-x-4 items-start justify-between">
			<div class="flex flex-wrap gap-3">
				<button on:click={applyBold} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Bold</button>
				<button on:click={applyItalic} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Italic</button>
				<button on:click={applyUnderline} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Underline</button>
				<button on:click={applyStrikethrough} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Strikethrough</button>
				<button on:click={alignLeft} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Left Align</button>
				<button on:click={alignRight} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Right Align</button>
				<button on:click={alignCenter} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Center Align</button>
				<button on:click={indentText} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Tab</button>
				<button on:click={justifyText} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Justify</button>
				<button on:click={removeWord} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Remove Word</button>
				<button on:click={reverseWord} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Reverse Word</button>
				<button on:click={sortWord} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Sort Word</button>



				
				
			</div>
			<div>
				<button on:click={copyText} class="copy-button bg-gray-600 text-white px-4 py-3 rounded hover:bg-gray-500 duration-300">
					<!-- svelte-ignore a11y-missing-attribute -->
					<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABgAAAAYCAYAAADgdz34AAAAAXNSR0IArs4c6QAAALBJREFUSEvtldENgzAMRO82gU3aUZikozAKjMImVwUpqKGkNo74qchv7LzEOZ+JixcvPh8mQNIDwAigc15mATCQnFO8BzABSJAzayHZewFaA0nzMilOUhFvJu0TrGf8MaBVLbl01RJJalKLB9CklhvwJf9af/z65NAfVBpvJvksrCLasQeAY7OLAiyP2rzoBtRc9rNEEavY1OIBpKn1OjG9CrWYAGuQRPfNiRY9OOe9ARWQrBm2wE6mAAAAAElFTkSuQmCC" />
				</button>
			</div>
		</div>
	</div>
</div>
