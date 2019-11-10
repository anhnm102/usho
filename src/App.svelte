<script>
	let url = ''
	let customUrl = ''
	let shortened = ''

	async function shorten(e) {
		console.log(url)
		const rs = await (await fetch('https://usho.ml/api/url/shorten', {
			body: JSON.stringify({shortUrl: customUrl, longUrl: url}),
			headers: {
				'Accept': 'application/json',
      			'Content-Type': 'application/json'
			},
			method: 'POST',
		})).json()
		shortened = rs.shortUrl
	}

</script>

<style>
</style>


<form on:submit|preventDefault={shorten}>
	<input bind:value={url} placeholder="Enter url here">
	<input bind:value={customUrl} placeholder="your custom url (optional)">
	<br>
	<button type="submit">Shorten</button>
</form>
<div>Your shortened url is: {shortened}</div>