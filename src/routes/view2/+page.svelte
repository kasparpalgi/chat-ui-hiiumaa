<script lang="ts">
	//deisgn 1
	import IconButton from '$lib/components/IconButton.svelte';
	import bot from '$lib/components/svg/Vector.svg';
	import chat from '$lib/components/svg/chat.svg';
	import menu from '$lib/components/svg/menu.svg';
	import logo from '$lib/components/svg/Header.svg';

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
	let activeTool = '';

	function setTool(tool: string) {
		if (activeTool === tool) {
			activeTool = '';
		} else {
			activeTool = tool;
		}
	}

	let email = '';
	let phone = '';
	let kordamine = '';
	const options = ['1 Korda', '2 Korda', '3 Korda', '4 Korda'];

	import QuestionButton from '$lib/components/QuestionButton.svelte';

	const questions = [
		'Kui palju maksab leib Hiiumaal?',
		'Mis on praami sõidugraafik?',
		'Kus on odavaim tankla Hiiumaal?'
	];

	function handleQuestionClick(text: string) {
		console.log('Clicked question:', text);
		// You can trigger AI response logic here
	}
</script>

<div class="flex justify-center">
	<div class="flex justify-center">
		<div class="mobile">
			<div class="flex flex-col items-center rounded-2xl">
				<img src={bot} alt="" />
				<h1 class="text-2xl font-bold text-blue-600">Hiiuma Ai</h1>
				<p class="w-md text-center font-medium text-gray-600">
					Tere! Millest te täna rääkida <br /> tahaksite?
				</p>
			</div>

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

			<div class="mt-5 flex flex-col items-center">
				<div class="mx-auto w-full max-w-md space-y-3">
					{#each questions as question}
						<QuestionButton text={question} onClick={() => handleQuestionClick(question)} />
					{/each}
				</div>
			</div>

			<div class="mt-5 flex flex-col items-center">
				<h1 class="text-2xl font-bold text-blue-600">Tasuta rakendused</h1>
				<p class="w-md text-center font-medium text-gray-600">
					Neil kolmel rakendusel on tasuta limiidid, <br /> mis lähtestatakse iga kuu ja töötavad
					<br /> suurepäraselt eesti keeles.
				</p>
				<div class="mt-5 flex justify-between" style="width: 100%">
					<div class="flex flex-col text-center">
						<img src={gpt} alt="" />
						<p>ChatGPT</p>
					</div>
					<div class="flex flex-col text-center">
						<img src={deepseek} alt="" />
						<p>Deepseek</p>
					</div>
					<div class="flex flex-col text-center">
						<img src={gemini} alt="" />
						<p>Gemini</p>
					</div>
				</div>
			</div>

			<div class="mt-8 flex flex-col rounded-xl bg-white p-4 shadow-md">
				<div class="flex flex-col items-center rounded-2xl">
					<h1 class="text-center text-2xl font-bold text-blue-600">
						Jagatud ChatGPT <br /> PRO Konto
					</h1>
					<p class="w-md text-center font-medium text-gray-600">Sisesta oma andmed ja saa kutse</p>
				</div>

				<div class="mt-3 flex flex-col items-center">
					<div class="mx-auto w-full max-w-md space-y-5">
						<!-- Email -->
						<div>
							<label class="mb-1 block text-sm font-semibold text-gray-700">
								Meil<span class="text-red-500">*</span>
							</label>
							<input
								type="email"
								bind:value={email}
								placeholder="nina@email.com"
								class="w-full rounded-md border border-gray-300 px-4 py-2 text-sm focus:ring-2 focus:ring-blue-400 focus:outline-none"
							/>
						</div>

						<!-- Phone -->
						<div>
							<label class="mb-1 block text-sm font-semibold text-gray-700">
								Telefoninumber<span class="text-red-500">*</span>
							</label>
							<input
								type="tel"
								bind:value={phone}
								placeholder="324 123 4567"
								class="w-full rounded-md border border-gray-300 px-4 py-2 text-sm text-gray-400 focus:ring-2 focus:ring-blue-400 focus:outline-none"
							/>
						</div>
					</div>

					<p class="mt-4 text-sm font-medium text-gray-600">
						Annan nöusoleku, et minu e-posti aadressi ja telefoninumbrit kasutatkase, et saata mulle
						meeldetuletusi hääletamise kohta. Millise sagedusega soovid meeldetuletusi saada?
					</p>
					<div class="mx-auto mt-5 w-full max-w-md space-y-6">
						<!-- Dropdown Field -->
						<div>
							<label class="mb-1 block text-sm font-semibold text-gray-700">
								kordamine<span class="text-red-500">*</span>
							</label>
							<div class="relative">
								<select
									bind:value={kordamine}
									class="w-full appearance-none rounded-md border border-gray-300 px-4 py-2 text-sm font-medium focus:ring-2 focus:ring-blue-400 focus:outline-none"
								>
									<option disabled selected value="">Select</option>
									{#each options as option}
										<option>{option}</option>
									{/each}
								</select>
								<div class="pointer-events-none absolute inset-y-0 right-0 flex items-center pr-3">
									<svg
										class="h-4 w-4 text-gray-500"
										fill="none"
										stroke="currentColor"
										stroke-width="2"
										viewBox="0 0 24 24"
									>
										<path stroke-linecap="round" stroke-linejoin="round" d="M19 9l-7 7-7-7" />
									</svg>
								</div>
							</div>
						</div>

						<!-- Submit Button -->
						<button
							class="flex w-full items-center justify-center gap-2 rounded-md bg-[#306FC7] py-3 font-semibold text-white hover:bg-blue-700"
						>
							Esita
							<svg
								class="h-5 w-5"
								fill="none"
								stroke="currentColor"
								stroke-width="2"
								viewBox="0 0 24 24"
							>
								<path stroke-linecap="round" stroke-linejoin="round" d="M17 8l4 4m0 0l-4 4m4-4H3" />
							</svg>
						</button>
					</div>
				</div>
			</div>
		</div>
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

	.mobile {
		width: 375px;
		padding: 22px;
		background-color: #f9fafe;
	}
</style>
