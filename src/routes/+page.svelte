<div class="container">
	<div id="top-container">
		<img id="photo" src="/photo.jpg" alt="" />
		<div id="photo-blur"></div>
		<div id="slogan" style="font-size: 80px; align-content: center;">Engineering for the Community.</div>
	</div>
</div>

<style>
	#slogan {
        font-size: 100px;
		font-family: Rubik Mono One;
		color: white;
		-webkit-text-stroke: 4px black;
		text-shadow: 4px 4px 4px var(--blue);
		align-content: center;
    }

	#top-container {
		height: calc(100vh - 80px);
		margin: 0;
		display: flex;
	}

	#photo-blur {
		width: 100%;
		height: calc(100vh - 80px);
		position: absolute;
		backdrop-filter: blur(2px);
		z-index: -1;
	}

	#photo {
		width: 100%;
		height: calc(100vh - 80px);
		position: absolute;
		object-fit: cover;
		object-position: 0 100%;
		z-index: -2;
	}
</style>