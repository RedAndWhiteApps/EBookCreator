<script>
  export let content;
  export let onTextChange;

  function handleTextChange(event) {
    onTextChange(event.target.innerText);
  }
</script>

<div class="page">
  <img src={content.image} alt={`Image for page ${content.id}`}>
  <p contenteditable="true" on:input={handleTextChange}>{content.text}</p>
</div>

<style>
  .page {
    padding: 20px;
    flex: 1;
    background-color: #fff;
    border: 1px solid #ccc;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    margin: 10px;
    border-radius: 5px;
    text-align: center;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  img {
    max-width: 100%;
    height: auto;
    margin-bottom: 15px;
  }

  p {
    font-size: 1.2em;
    line-height: 1.5;
    outline: none;
    flex: 1;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0;
  }
</style>
