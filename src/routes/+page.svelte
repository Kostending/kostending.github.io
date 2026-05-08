<script>
	import VideoEmbed from '$lib/VideoEmbed.svelte';

	// Replace with your actual YouTube embed URL:
	// https://www.youtube.com/embed/YOUR_VIDEO_ID
	const videoUrl = 'https://www.youtube.com/embed/dQw4w9WgXcQ';

	const title = 'Tillykke med mors dag';

	const message =
		'Skriv din personlige besked her. Fortæl hende, hvad hun betyder for dig og jeres drenge.';
</script>

<div class="h-screen bg-[#FAF7F2] flex items-center justify-center px-8 py-6">
	<div class="flex gap-8 w-full items-stretch" style="max-width: 1300px; height: 80vh;">

		<!-- Left column: Video — this is the emotional centrepiece of the page -->
		<div class="flex-[55] min-w-0">
			<VideoEmbed url={videoUrl} />
		</div>

		<!-- Right column: personal message card -->
		<div
			class="flex-[45] min-w-0 flex flex-col justify-between bg-[#FFFDF9] rounded-2xl shadow-lg px-10 py-10"
		>
			<h1
				class="text-4xl font-semibold text-[#C27A5E] leading-snug"
				style="font-family: 'Playfair Display', serif;"
			>
				{title}
			</h1>

			<p
				class="text-[#3D2B1F] text-xl leading-relaxed"
				style="font-family: 'Inter', sans-serif; font-weight: 300;"
			>
				{message}
			</p>

			<div class="flex gap-4">
				<img
					src="/kids-1.svg"
					alt="Barn 1"
					class="w-1/2 aspect-square rounded-xl object-cover"
				/>
				<img
					src="/kids-2.svg"
					alt="Barn 2"
					class="w-1/2 aspect-square rounded-xl object-cover"
				/>
			</div>
		</div>
	</div>
</div>
