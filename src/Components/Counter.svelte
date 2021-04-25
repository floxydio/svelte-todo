<script>
	let number = 0;

	$: if ( number >= 7) {
		alert('Sudah 7');
	}
 
	function addnumbers() {
		number += 1;
	}
	function numNumbers() {
		number -= 1;
	}
</script>

<style>
	.container {
		text-align: center;
		font-size:30px;
	}
	.container button {
		width: 100px;
		height: 40px;
		font-size: 20px;
		background-color: black;
		color: white;
	}
</style>

<div class="container">
	<h3>Counter</h3>
	<button on:click={addnumbers}>
	+
	</button>
	<button on:click={numNumbers}>
		-
		</button>
	<p>{number}</p>
</div>