<script lang="ts">
	import IconButton from '$lib/components/IconButton.svelte';
	import bot from '$lib/components/svg/Vector.svg';
	import chat from '$lib/components/svg/chat.svg';
	import menu from '$lib/components/svg/menu.svg';
	import logo from '$lib/components/svg/Header.svg';
	import PromptScroll from './PromptScroll.svelte';
	import world from '$lib/components/svg/icon-world.svg';
	import imgfile from '$lib/components/svg/icon-imgai.svg';
	import fileupload from '$lib/components/svg/icon-file.svg';
	import microphone from '$lib/components/svg/microphone.svg';
	import send from '$lib/components/svg/send.svg';
	import gpt from '$lib/components/svg/gpt.svg';
	import deepseek from '$lib/components/svg/deepseek.svg';
	import gemini from '$lib/components/svg/gemini.svg';
	import download_btn from '$lib/components/svg/download.svg';
	import down from '$lib/components/svg/dow.svg';

	import ImageOption from '$lib/components/ImageOption.svelte';
	import IconAction from '$lib/components/IconAction.svelte';

	import camera from '$lib/components/svg/camera.png';
	import photo from '$lib/components/svg/photo.png';
	import file from '$lib/components/svg/file.png';
	import paint from '$lib/components/svg/create_img.svg';
	import research from '$lib/components/svg/telescop.svg';

	let activeTool = '';
	let showImgModal = false;
	let showSidebar = false;

	function setTool(tool: string) {
		if (activeTool === tool) {
			activeTool = '';
			showImgModal = false;
		} else {
			activeTool = tool;
			showImgModal = tool === 'img';
		}
	}

	const questions = [
		'Kui palju maksab leib Hiiumaal?',
		'Mis on praami sõidugraafik?',
		'Kus on odavaim tankla Hiiumaal?'
	];
</script>

<div class="flex justify-center">
	<div class="mobile">
		<div class="flex justify-between">
			<IconButton icon={menu} alt="menu" onClick={() => setTool('menu')} />
			<img src={logo} alt="" />

			<IconButton icon={chat} alt="chat" onClick={() => setTool('chat')} />
		</div>
		<div class="flex flex-col">
			<PromptScroll />
			<div class="flex flex-col">
				<div class="flex flex-col rounded-xl bg-white p-2 shadow-md">
					<input
						type="text"
						placeholder="Küsi midagi..."
						class="w-full rounded-lg border border-gray-100 px-3 py-2 text-[16px] font-medium text-gray-800 placeholder-blue-500 outline-none"
					/>
	
					<div class="mt-2 flex justify-between">
						<div class="flex gap-2">
							<IconButton
								icon={world}
								alt="Web"
								active={activeTool === 'world'}
								onClick={() => setTool('world')}
							/>
							<IconButton
								icon={imgfile}
								alt="Image"
								active={activeTool === 'img'}
								onClick={() => setTool('img')}
							/>
							<IconButton
								icon={fileupload}
								alt="File"
								active={activeTool === 'file'}
								onClick={() => setTool('file')}
							/>
						</div>
						<div class="flex gap-2">
							<IconButton icon={microphone} alt="Mic" onClick={() => console.log('Mic clicked')} />
							<IconButton icon={send} alt="Send" onClick={() => console.log('Send clicked')} />
						</div>
					</div>
				</div>
			</div>
		</div>
		{#if showImgModal}
			<!-- Background overlay -->
			<div
				class="absolute inset-0 z-40 bg-black/20"
				on:click={() => {
					showImgModal = false;
					activeTool = '';
				}}
			></div>

			<!-- Modal box -->
			<div
				class="animate-slide-up absolute right-0 bottom-0 left-0 z-50 mx-auto w-full"
				on:click|stopPropagation
				style="width: 375px;"
			>
				<div class="rounded-t-xl bg-white p-4 shadow-lg">
					<!-- Drag indicator -->
					<div class="mx-auto mb-4 h-1.5 w-12 rounded-full bg-gray-300"></div>

					<!-- Top options -->
					<div class="mb-4 flex gap-2">
						<ImageOption icon={camera} label="Camera" />
						<ImageOption icon={photo} label="Photos" />
						<ImageOption icon={file} label="Files" />
					</div>

					<hr class="mb-4 border-gray-200" />

					<!-- Action items -->
					<ul class="space-y-3">
						<IconAction icon={paint} text="Create an image" />
						<IconAction icon={world} text="Search the web" />
						<IconAction icon={research} text="Run deep research" hint="• 15 min" />
					</ul>
				</div>
			</div>
		{/if}
	</div>
</div>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Nunito:ital,wght@0,200..1000;1,200..1000&display=swap');
	@import url('https://fonts.googleapis.com/css2?family=Source+Sans+3:ital,wght@0,200..900;1,200..900&display=swap');

	h1,
	span {
		font-family: 'Nunito', sans-serif;
	}
	p {
		font-family: 'Source Sans 3', sans-serif;
	}
	@keyframes slide-up {
		from {
			transform: translateY(100%);
			opacity: 0;
		}
		to {
			transform: translateY(0);
			opacity: 1;
		}
	}
	.animate-slide-up {
		animation: slide-up 0.3s ease-out forwards;
	}

	.mobile {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		width: 375px;
		height: 100vh;
		padding: 22px;
		background-color: #f9fafe;
	}
</style>
