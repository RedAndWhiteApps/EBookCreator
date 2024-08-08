<script>
    import Page from './Page.svelte';
  
    let pages = [
      { id: 1, image: 'https://via.placeholder.com/200', text: 'This is the text for page 1.' },
      { id: 2, image: 'https://via.placeholder.com/200', text: 'This is the text for page 2.' },
      { id: 3, image: 'https://via.placeholder.com/200', text: 'This is the text for page 3.' },
      { id: 4, image: 'https://via.placeholder.com/200', text: 'This is the text for page 4.' }
    ];
  
    let currentIndex = 0;
  
    function nextPage() {
      if (currentIndex < pages.length - 2) {
        currentIndex += 2;
      }
    }
  
    function prevPage() {
      if (currentIndex > 0) {
        currentIndex -= 2;
      }
    }
  
    function goToPage(index) {
      currentIndex = index;
    }
  </script>
  
  <main class="book">
    <div class="pages">
      <Page content={pages[currentIndex]} onTextChange={(text) => pages[currentIndex].text = text} />
      {#if currentIndex + 1 < pages.length}
        <Page content={pages[currentIndex + 1]} onTextChange={(text) => pages[currentIndex + 1].text = text} />
      {/if}
    </div>
  
    <nav class="pagination">
      <button on:click={prevPage} disabled={currentIndex === 0}>&lt;</button>
      {#each pages as page, index}
        {#if index % 2 === 0}
          <button
            class:selected={index === currentIndex}
            on:click={() => goToPage(index)}>
            {index / 2 + 1}
          </button>
        {/if}
      {/each}
      <button on:click={nextPage} disabled={currentIndex >= pages.length - 2}>&gt;</button>
    </nav>
  </main>
  
  <style>
    .book {
      display: flex;
      flex-direction: column;
      align-items: center;
      height: 100vh;
      padding: 20px;
      background-color: #f7f7f7;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    }
  
    .pages {
      display: flex;
      justify-content: center;
      width: 100%;
      flex-grow: 1;
    }
  
    .pagination {
      display: flex;
      justify-content: center;
      gap: 8px;
      margin-top: 20px;
    }
  
    button {
      padding: 5px 10px;
      border: none;
      background-color: #ddd;
      cursor: pointer;
      border-radius: 5px;
      transition: background-color 0.3s;
    }
  
    button:hover {
      background-color: #ccc;
    }
  
    button:disabled {
      background-color: #eee;
      cursor: not-allowed;
    }
  
    button.selected {
      background-color: #aaa;
    }
  </style>
  