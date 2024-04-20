<script>
	import { onMount,afterUpdate } from  'svelte';
	import { tweened } from 'svelte/motion';
	import { cubicOut } from 'svelte/easing';
	import Message from './Message.svelte'
    import { writable } from 'svelte/store';
		
	let name = 'Shashwatik Sinha';
	let opacity = 0;
	
	function isMobileDevice() {
		var aspectRatio = window.innerHeight / window.innerWidth;
		var threshold = 0.70;
		console.log(aspectRatio);
		return aspectRatio > threshold;
	}
	
	let fontSize = tweened(0, {
		duration: 3000,
		easing : cubicOut
	});

	onMount(() => {
		if(isMobileDevice()) {
			fontSize.set(6,{ duration: 0});
		}
	});
	

	afterUpdate(() => {
		setTimeout(()=>{
			opacity = 1;
			fontSize.set(6);
		},500);
	});

</script>
<div class="flex-container" style="opacity : {opacity}">
    <p class="name" style="font-size: {$fontSize + 'em'}">{name}</p>
    <div class="links">
            <a class = "link wiggle" href="/shashwatik_resume.pdf" target="_blank" rel="noopener noreferrer">Resume</a>
            <a class = "link wiggle" href="https://blog.shashwatik.me" target="_blank" rel="noopener noreferrer">Blog</a>
            <a class = "link wiggle" href="/projects" target="_blank" rel="noopener noreferrer">Projects</a>
            <a class = "link wiggle" href="https://github.com/shash236" target="_blank" rel="noopener noreferrer">Github</a>
            <a class = "link wiggle" href="https://www.linkedin.com/in/shashwatik-sinha/" target="_blank" rel="noopener noreferrer">LinkedIn</a>
            <a class = "link wiggle" href="https://codeforces.com/profile/shash236" target="_blank" rel="noopener noreferrer">Codeforces</a>
            <a class = "link wiggle" href="https://leetcode.com/sinha23/" target="_blank" rel="noopener noreferrer">Leetcode</a>
            <a class = "link wiggle" href="https://cses.fi/problemset/user/226488/" target="_blank" rel="noopener noreferrer">CSES</a>
    </div>
    <Message />
</div>

<style>
	.flex-container {
	    display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		user-select: none;
		padding: 3em;
		text-align: center;
        color: white;
	}

	.name:hover {
		font-weight: 700;
	}
	
 
	.links {
		display: flex;
		flex-flow: row wrap;
		font-size: 2.15em;
		justify-content: center;
		align-items: center;
	}

	.link {
		padding-right : 1.5em;
		text-decoration: none;
		color: inherit;
	}

	@keyframes wiggle {
	    0% { transform: rotate(0deg); }
	   30% { transform: rotate(0deg); }
	   50% { transform: rotate(5deg); }
	   55% { transform: rotate(-5deg); }
       65% { transform: rotate(5deg); }
       75% { transform: rotate(-5deg); }
	  100% { transform: rotate(0deg); }
	}

	.wiggle:hover {
	  display: inline-block;
	  animation: wiggle 0.7s infinite;
	}
	
</style>

												 
