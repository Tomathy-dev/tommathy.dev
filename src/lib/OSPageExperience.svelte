<script lang="ts">
    const technologies = [
        {
            img: "C.png",
            alt: "C programming Logo"
        },
        {
            img: "Java.png",
            alt: "Java Logo"
        },
        {
            img: "JavaScript.png",
            alt: "JavaScript Logo"
        },
        {
            img: "python.png",
            alt: "Python Logo"
        },
        {
            img: "svelte.png",
            alt: "Svelte Logo"
        },
        {
            img: "Prisma.jpg",
            alt: "Prisma ORM Logo"
        },
        {
            img: "git.png",
            alt: "Git Logo"
        },
        {
            img: "Figma.png",
            alt: "Figma Logo"
        }
    ]


</script>


<div class="w-full text-[wheat] flex justify-center items-center p-2 flex-col overflow-auto">
	<header class="w-full flex justify-center items-center p-2">
		<div class="flex justify-center items-center border-b-2 border-[wheat] w-[90%]">Experience</div>
	</header>
	<div class="w-full text-[wheat] flex justify-center items-center">
		<div class="path w-[90%] flex flex-col py-4 relative">
			<div id="first" class="path-work">
				<h2>EDGE International Lawyers (Present)</h2>
				<h3 class=" mb-3"><em>Software Developer</em></h3>
				<p class="content text-[wheat] text-lg">
					Working on a 2-man team to develop a web application for the Tax Representation
					Department, with the intent to manage client data.
				</p>
			</div>
			<div id="last" class="path-work">
				<h2>NTT Data (Summer 2023)</h2>
				<h3 class=" mb-3"><em>Data Science Internship</em></h3>
				<p class="content text-[wheat] text-lg">
					Conducted reasearch on energy consumption trends in Portugal, leveraging open source API's
					such as E-REDES and other data sources like PorData.
				</p>
			</div>
			<div>
				<p class="content text-2xl mb-4">Here are some of the technologies I use:</p>
				<div class="slider">
					<div class="slide-track flex flex-row">
						<div class="slide">
							<img src="C.png" alt="C programming Logo" height="100" width="100" />
						</div>
						<div class="slide">
							<img src="Java.png" alt="Java Logo" height="100" width="100" />
						</div>
						<div class="slide">
							<img src="JavaScript.png" alt="JavaScript Logo" height="100" width="100" />
						</div>
                        <div class="slide">
							<img src="python.png" alt="Python Logo" height="100" width="100" />
						</div>
						<div class="slide">
							<img src="svelte.png" alt="Svelte Logo" height="100" width="100" />
						</div>
						<div class="slide">
							<img src="Prisma.jpg" alt="Prisma ORM Logo" height="100" width="100" />
						</div>
						<div class="slide">
							<img src="git.png" alt="Git Logo" height="100" width="100" />
						</div>
						<div class="slide">
							<img src="Figma.png" alt="Figma Logo" height="100" width="100" />
						</div>
                        <!-- Repeat logos for carroussel effect -->
                        <div class="slide">
							<img src="C.png" alt="C programming Logo" height="100" width="100" />
						</div>
						<div class="slide">
							<img src="Java.png" alt="Java Logo" height="100" width="100" />
						</div>
						<div class="slide">
							<img src="JavaScript.png" alt="JavaScript Logo" height="100" width="100" />
						</div>
                        <div class="slide">
							<img src="python.png" alt="Python Logo" height="100" width="100" />
						</div>
						<div class="slide">
							<img src="svelte.png" alt="Svelte Logo" height="100" width="100" />
						</div>
						<div class="slide">
							<img src="Prisma.jpg" alt="Prisma ORM Logo" height="100" width="100" />
						</div>
						<div class="slide">
							<img src="git.png" alt="Git Logo" height="100" width="100" />
						</div>
						<div class="slide">
							<img src="Figma.png" alt="Figma Logo" height="100" width="100" />
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</div>

<style>
	.content {
		font-family: 'Mido', sans-serif;
	}

	header {
		font-family: 'Panchang', sans-serif;
		font-size: 4em;
		font-weight: 800;
	}

	h2 {
		font-family: 'Chillax', sans-serif;
		font-size: 2em;
		font-weight: 400;
	}

	#first::before {
		content: '';
		width: 5px;
		height: 50%;
		background-color: wheat;
		position: absolute;
		left: 5px;
		top: 50%;
	}

	.path-work::before {
		content: '';
		width: 5px;
		height: 100%;
		background-color: wheat;
		position: absolute;
		left: 5px;
		top: 0;
	}

	.path-work {
		padding-left: 50px;
		padding-top: 30px;
		padding-bottom: 30px;
		position: relative;
	}

	.path-work::after {
		content: '';
		width: 15px;
		height: 15px;
		border-radius: 50%;
		background-color: wheat;
		position: absolute;
		left: 0px;
		top: 50%;
		transform: translateY(-50%);
	}

	#last::before {
		content: '';
		width: 5px;
		height: 50%;
		background-color: wheat;
		position: absolute;
		left: 5px;
		top: 0;
	}

	@keyframes scroll {
		0% {
			transform: translateX(0);
		}
		100% {
			transform: translateX(calc(-250px * 7));
		}
	}

	.slider {
		margin: auto;
		overflow: hidden;
		position: relative;
		width: 100%;
        height: 100px;;
		display: flex;
		justify-content: center;
		align-items: center;
		border-radius: 8px;
	}

	.slide-track {
        position: absolute;
        width: 200%;
        height: 100%;
        left: 0;
        overflow: hidden;
	}
</style>
