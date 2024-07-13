<script>
  let textContent = '';
  let sorted = false;

  const applyItalic = () => {
    textContent = `<i>${textContent}</i>`;
  };

  const applyUnderline = () => {
    textContent = `<u>${textContent}</u>`;
  };

  const applyStrikethrough = () => {
    textContent = `<s>${textContent}</s>`;
  };

  const alignLeft = () => {
    textContent = `<div style="text-align: left;">${textContent}</div>`;
  };

  const alignRight = () => {
    textContent = `<div style="text-align: right;">${textContent}</div>`;
  };

  const alignCenter = () => {
    textContent = `<div style="text-align: center;">${textContent}</div>`;
  };

  const indentText = () => {
    textContent = `<div style="padding-left: 30px;">${textContent}</div>`;
  };

  const justifyText = () => {
    textContent = `<div style="text-align: justify;">${textContent}</div>`;
  };

  const removeWord = () => {
    // Example to remove the last word (adjust as needed)
    let words = textContent.split(' ');
    words.pop(); // Remove last word
    textContent = words.join(' ');
  };

  const reverseWords = () => {
    let words = textContent.split(' ');
    words = words.map(word => word.split('').reverse().join('')).join(' ');
    textContent = words;
  };

 const sortWords = () => {
  let words = textContent.split(' ');
  
  if (!sorted) {
    words.sort((a, b) => a.localeCompare(b, 'en', { sensitivity: 'base' }));
    sorted = true;
  } else {
    words.reverse();
    sorted = false;
  }
  
  textContent = words.join(' ');
};

  const splitText = () => {
    textContent = textContent.split('').join(' ');
  };

  const removeWhitespace = () => {
    textContent = textContent.replace(/\s+/g, '');
  };
  const copyText = () => {
  const textarea = document.createElement('textarea');
  textarea.value = textContent;
  document.body.appendChild(textarea);
  textarea.select();
  document.execCommand('copy');
  document.body.removeChild(textarea);

  // Display an alert after copying
  alert('Text copied to clipboard!');
};

</script>

<style>
</style>

<div class="bg-gray-900 text-white flex flex-col items-center py-8 h-auto">
  <header class="mb-8">
    <h1 class="text-3xl font-bold">Text Toolkit</h1>
  </header>

  <div class="relative card w-full lg:w-2/3 mx-auto max-w-screen-xl p-6 bg-gray-800 shadow-md rounded-lg">
    <textarea
      bind:value={textContent}
      class="w-full h-64 p-4 bg-gray-700 text-white rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-600"
      placeholder="Type your text here..."></textarea>
    <div class="flex space-x-4 items-start justify-between">
      <div class="flex flex-wrap gap-3">
        <button on:click={applyItalic} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Italic</button>
        <button on:click={applyUnderline} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Underline</button>
        <button on:click={applyStrikethrough} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Strikethrough</button>
        <button on:click={alignLeft} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Left Align</button>
        <button on:click={alignRight} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Right Align</button>
        <button on:click={alignCenter} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Center Align</button>
        <button on:click={indentText} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Indent</button>
        <button on:click={justifyText} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Justify</button>
        <button on:click={removeWord} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Remove Word</button>
        <button on:click={reverseWords} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Reverse Word</button>
        <button on:click={sortWords} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Sort Word</button>
        <button on:click={splitText} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Split Text</button>
        <button on:click={removeWhitespace} class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">Remove Whitespace</button>
      </div>
      <div>
        <button on:click={copyText} class="copy-button bg-gray-600 text-white p-2 rounded hover:bg-gray-500 duration-300 w-auto h-auto">
          <img width="60px"src="https://i.postimg.cc/x12588Zb/copy-regular-24.png" alt="">
        </button>
      </div>
    </div>
  </div>
</div>
