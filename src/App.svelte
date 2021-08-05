<script>
	import Book from "./Book.svelte";
	import Button from "./Button.svelte";
	let title = "";
	let price = 0;
	let description = "";
	function setTitle(event) {
		title = event.target.value;
	}

	let books = [];

	function addBook() {
		const newBook = {
			title: title,
			price: price,
			description: description,
		};
		books = books.concat(newBook);
	}
</script>

<section>
	<div>
		<label for="title">Title</label>
		<input type="text" id="title" value={title} on:input={setTitle} />
	</div>
	<div>
		<label for="price">Price</label>
		<input type="number" id="price" bind:value={price} />
	</div>
	<div>
		<label for="description">Description</label>
		<textarea rows="3" id="description" bind:value={description} />
	</div>
</section>
<Button on:click={addBook}>ADD Book</Button>
{#if books.length === 0}
	<p>No books in stock.</p>
{:else}
	{#each books as book}
		<Book
			bookTitle={book.title}
			bookPrice={book.price}
			bookDescription={book.description}
		/>
	{/each}
{/if}

<style>
	h1 {
		color: purple;
	}
	section {
		margin: auto;
		width: 30rem;
	}
	label,
	input,
	textarea {
		width: 100%;
	}
</style>
