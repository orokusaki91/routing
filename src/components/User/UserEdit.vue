<template>
    <div>
    	<h3>Edit the User</h3>
    	<p>Locale: {{ $route.query.locale }}</p>
    	<p>Search: {{ $route.query.q }}</p>

		<hr>
		<button class="btn btn-primary" @click="confirmed = true">Confirm To Leave Instantly</button>

    	<div style="height: 700px;"></div>
    	<p id="data">Some Extra Data</p>
    </div>
</template>

<script>
	export default {
		data() {
			return {
				confirmed: false
			}
		},
		beforeRouteLeave(to, from, next) {
			if (!this.confirmed) {
				if (!confirm('Are you sure?')) {
					return next(false);
				}
			}

			next();
		}
	}
</script>