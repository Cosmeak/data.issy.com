<script lang="ts">
	import Map from '$lib/Leaflet/Map.svelte';
	import Marker from '$lib/Leaflet/Marker.svelte';
	import Popup from '$lib/Leaflet/Popup.svelte';
	import type { LatLngExpression } from 'leaflet';

	export let data;

	let globalData = {
		childs: 0,
		youngs: 0,
		adults: 0,
		seniors: 0,
		handicaps: 0,
		total: data.data.length
	};

	data.data.forEach((item) => {
		if (item.enfants == 'Oui') globalData.childs += 1;
		if (item.jeunes == 'Oui') globalData.youngs += 1;
		if (item.adultes == 'Oui') globalData.adults += 1;
		if (item.seniors == 'Oui') globalData.seniors += 1;
		if (item.sport_handicap == 'Oui') globalData.handicaps += 1;
	});

	const initialView: LatLngExpression = [48.816669, 2.26667];
	const initialZoom: number = 14;
</script>

<svelte:head>
	<title>Associations Sportives</title>
</svelte:head>

<section
	class="w-screen h-section bg-hero bg-no-repeat bg-contain bg-bottom bg-blue-light relative flex flex-col items-center justify-center space-y-8"
>
	<img src="/assets/space.svg" alt="" class="absolute top-0 left-0 max-h-4xl" />
	<h1 class="text-blue-dark text-6xl text-center">Associations Sportives</h1>

	<div class="grid grid-cols-5 gap-4 w-full max-w-6xl">
		<div
			class="flex flex-col items-center justify-center bg-blue-dark text-white p-12 space-y-8 rounded-tl-4xl rounded-br-4xl aspect-square mt-20"
		>
			<p class="text-3xl">Enfants</p>
			<p class="text-4xl">{globalData.childs}</p>
		</div>
		<div
			class="flex flex-col items-center justify-center bg-blue-dark text-white p-12 space-y-8 rounded-tl-4xl rounded-br-4xl aspect-square mt-10"
		>
			<p class="text-3xl">Jeunes</p>
			<p class="text-4xl">{globalData.youngs}</p>
		</div>
		<div
			class="flex flex-col items-center justify-center bg-blue-dark text-white p-12 space-y-8 rounded-4xl aspect-square"
		>
			<p class="text-3xl">Total</p>
			<p class="text-4xl">{globalData.total}</p>
		</div>
		<div
			class="flex flex-col items-center justify-center bg-blue-dark text-white p-12 space-y-8 rounded-tr-4xl rounded-bl-4xl aspect-square mt-10"
		>
			<p class="text-3xl">Seniors</p>
			<p class="text-4xl">{globalData.seniors}</p>
		</div>
		<div
			class="flex flex-col items-center justify-center bg-blue-dark text-white p-12 space-y-8 rounded-tr-4xl rounded-bl-4xl aspect-square mt-20"
		>
			<p class="text-3xl">Handicapés</p>
			<p class="text-4xl">{globalData.handicaps}</p>
		</div>
	</div>

	<p class="text-center max-w-4xl text-lightgray-dark font-semibold">
		Bienvenue sur le site de l'Association Sportive d'Issy-les-Moulineaux, votre référence en
		matière de dynamisme et d'esprit sportif au cœur de notre ville. Dédiée à la promotion du sport
		et au bien-être de nos citoyens, notre association s'engage à offrir une expérience sportive
		unique, accessible à tous.
	</p>
	<img src="/assets/troph.svg" alt="" class="absolute bottom-0 right-0 max-h-2xl" />
	<div class="absolute bottom-0 right-1/2">
		<svg
			width="184"
			height="129"
			viewBox="0 0 184 129"
			fill="none"
			xmlns="http://www.w3.org/2000/svg"
		>
			<path
				d="M9.42666 34.057C8.4177 34.2469 7.48275 34.2532 6.6218 34.0761C5.76085 33.8989 5.02755 33.5349 4.42191 32.9841C3.82937 32.4308 3.43492 31.7045 3.23858 30.8053L6.81579 30.1322C6.96437 30.6333 7.21524 30.9931 7.5684 31.2116C7.91909 31.417 8.33685 31.474 8.82167 31.3828C9.3196 31.2891 9.69174 31.1037 9.9381 30.8267C10.182 30.5366 10.2657 30.1885 10.1893 29.7823C10.1252 29.4416 9.95422 29.182 9.67644 29.0037C9.41177 28.8228 9.09552 28.6924 8.72771 28.6124C8.37301 28.5299 7.87046 28.4549 7.22009 28.3873C6.27728 28.2798 5.49826 28.1415 4.88304 27.9723C4.26781 27.8032 3.70655 27.4882 3.19925 27.0274C2.69195 26.5666 2.35693 25.9038 2.19419 25.039C1.95254 23.7549 2.22908 22.6649 3.0238 21.7692C3.81606 20.8603 4.95908 20.2653 6.45286 19.9842C7.97285 19.6982 9.26705 19.8346 10.3355 20.3933C11.4014 20.9389 12.0892 21.8542 12.3988 23.1391L8.76267 23.8233C8.65262 23.3827 8.42349 23.0663 8.07526 22.8741C7.72457 22.6687 7.31336 22.6104 6.84164 22.6992C6.43544 22.7756 6.12881 22.9486 5.92177 23.2182C5.71226 23.4747 5.64572 23.8061 5.72216 24.2123C5.80599 24.6578 6.08099 24.9656 6.54715 25.1357C7.0133 25.3057 7.71902 25.4511 8.66429 25.5717C9.61204 25.7054 10.387 25.858 10.9891 26.0296C11.6043 26.1988 12.1643 26.5072 12.6692 26.9549C13.174 27.4026 13.5041 28.0392 13.6594 28.8647C13.8074 29.6509 13.7387 30.4032 13.4533 31.1217C13.181 31.8378 12.7006 32.4573 12.0121 32.9803C11.3237 33.5033 10.4618 33.8622 9.42666 34.057ZM25.7742 24.9772C25.8334 25.2917 25.8753 25.623 25.9001 25.9711L18.2936 27.4025C18.4743 28.074 18.7891 28.5574 19.2382 28.8528C19.6978 29.1326 20.2094 29.2195 20.7728 29.1135C21.6115 28.9557 22.128 28.4922 22.3224 27.7229L25.8996 27.0498C25.8518 27.805 25.6397 28.5165 25.2634 29.1843C24.9002 29.8496 24.389 30.4138 23.73 30.877C23.0709 31.3402 22.2959 31.6557 21.4049 31.8233C20.3304 32.0255 19.3307 31.9762 18.4058 31.6754C17.4809 31.3746 16.7024 30.8427 16.0704 30.0798C15.4384 29.3168 15.0152 28.3654 14.8007 27.2254C14.5861 26.0854 14.628 25.0464 14.9264 24.1084C15.2378 23.1679 15.7697 22.3894 16.522 21.773C17.2743 21.1566 18.1943 20.746 19.2819 20.5414C20.3432 20.3416 21.3286 20.3869 22.2379 20.677C23.1473 20.9672 23.9089 21.4819 24.5229 22.2211C25.15 22.9578 25.5671 23.8766 25.7742 24.9772ZM22.1681 24.74C22.0596 24.1635 21.7768 23.7418 21.3196 23.4751C20.8623 23.2084 20.3389 23.1305 19.7493 23.2415C19.1858 23.3475 18.7384 23.6013 18.4069 24.0029C18.0886 24.402 17.9402 24.9115 17.9619 25.5315L22.1681 24.74ZM37.8858 22.6981C37.945 23.0126 37.987 23.3439 38.0118 23.6919L30.4053 25.1233C30.5859 25.7948 30.9008 26.2783 31.3498 26.5737C31.8095 26.8535 32.321 26.9404 32.8845 26.8344C33.7231 26.6765 34.2396 26.213 34.4341 25.4438L38.0113 24.7706C37.9634 25.5259 37.7514 26.2373 37.375 26.9051C37.0118 27.5704 36.5007 28.1347 35.8416 28.5979C35.1826 29.0611 34.4075 29.3765 33.5165 29.5442C32.442 29.7464 31.4423 29.6971 30.5174 29.3963C29.5925 29.0955 28.8141 28.5636 28.1821 27.8006C27.5501 27.0377 27.1268 26.0862 26.9123 24.9462C26.6978 23.8062 26.7397 22.7672 27.038 21.8292C27.3495 20.8887 27.8814 20.1103 28.6337 19.4938C29.386 18.8774 30.3059 18.4669 31.3935 18.2622C32.4549 18.0625 33.4402 18.1077 34.3496 18.3979C35.2589 18.6881 36.0206 19.2028 36.6345 19.942C37.2616 20.6787 37.6787 21.5974 37.8858 22.6981ZM34.2798 22.4609C34.1713 21.8843 33.8884 21.4627 33.4312 21.196C32.974 20.9293 32.4506 20.8514 31.8609 20.9624C31.2975 21.0684 30.85 21.3222 30.5186 21.7237C30.2002 22.1228 30.0519 22.6324 30.0736 23.2524L34.2798 22.4609ZM56.7977 13.5224C58.1604 13.266 59.3191 13.4753 60.2737 14.1504C61.2415 14.8231 61.8635 15.8932 62.1396 17.3607L63.3454 23.7683L60.004 24.397L58.8833 18.4416C58.7502 17.734 58.4579 17.226 58.0064 16.9175C57.5655 16.5934 57.0175 16.493 56.3623 16.6163C55.7071 16.7396 55.2265 17.0335 54.9205 17.4982C54.6251 17.9472 54.544 18.5255 54.6772 19.2331L55.7978 25.1886L52.4565 25.8173L51.3358 19.8618C51.2027 19.1543 50.9103 18.6462 50.4588 18.3377C50.018 18.0137 49.4699 17.9133 48.8148 18.0366C48.1596 18.1599 47.679 18.4538 47.373 18.9184C47.0776 19.3675 46.9965 19.9458 47.1296 20.6534L48.2503 26.6088L44.8893 27.2413L42.8255 16.2738L46.1865 15.6413L46.4454 17.0172C46.6998 16.4944 47.0775 16.0503 47.5785 15.6846C48.0771 15.3059 48.6736 15.0512 49.3681 14.9205C50.1936 14.7652 50.9606 14.804 51.6693 15.037C52.391 15.2675 52.997 15.6758 53.4872 16.2619C53.7537 15.5876 54.1789 14.9989 54.7625 14.4956C55.3462 13.9923 56.0246 13.6679 56.7977 13.5224ZM70.718 22.5437C69.6435 22.7459 68.6307 22.6991 67.6796 22.4032C66.7415 22.1049 65.9434 21.5767 65.2852 20.8187C64.6401 20.0582 64.2103 19.1079 63.9958 17.9679C63.7837 16.8411 63.8465 15.8049 64.1842 14.8595C64.5194 13.901 65.0762 13.111 65.8548 12.4897C66.6333 11.8683 67.5598 11.4565 68.6343 11.2543C69.7087 11.0522 70.7215 11.099 71.6726 11.3949C72.6238 11.6908 73.4297 12.2243 74.0903 12.9954C74.7485 13.7534 75.1837 14.6958 75.3957 15.8227C75.6078 16.9496 75.5397 17.9936 75.1914 18.9545C74.8537 19.9 74.2891 20.6846 73.4975 21.3084C72.7189 21.9298 71.7924 22.3415 70.718 22.5437ZM70.1706 19.6348C70.8126 19.514 71.312 19.1758 71.6688 18.6202C72.0386 18.0622 72.1409 17.3442 71.9757 16.4663C71.8105 15.5884 71.4608 14.9555 70.9265 14.5676C70.4053 14.1772 69.8237 14.0425 69.1817 14.1633C68.5265 14.2866 68.0271 14.6248 67.6834 15.1779C67.3373 15.7178 67.2481 16.4334 67.4158 17.3244C67.581 18.2023 67.9176 18.8377 68.4257 19.2305C68.9469 19.6208 69.5285 19.7556 70.1706 19.6348ZM79.8519 11.1989C80.1315 10.5222 80.5341 9.95798 81.0597 9.50634C81.5828 9.04159 82.2046 8.74141 82.9253 8.60579L83.5948 12.1633L82.671 12.3372C81.8324 12.495 81.2379 12.7968 80.8877 13.2426C80.5349 13.6753 80.4436 14.3437 80.6138 15.2478L81.5717 20.3385L78.2107 20.971L76.1469 10.0034L79.5079 9.37098L79.8519 11.1989ZM95.8912 11.7828C95.9504 12.0973 95.9924 12.4286 96.0172 12.7766L88.4107 14.208C88.5913 14.8795 88.9061 15.363 89.3552 15.6584C89.8148 15.9382 90.3264 16.0251 90.8898 15.919C91.7285 15.7612 92.245 15.2977 92.4394 14.5285L96.0166 13.8553C95.9688 14.6105 95.7567 15.322 95.3804 15.9898C95.0172 16.6551 94.506 17.2194 93.847 17.6826C93.1879 18.1458 92.4129 18.4612 91.5219 18.6289C90.4474 18.8311 89.4477 18.7818 88.5228 18.481C87.5979 18.1802 86.8194 17.6483 86.1874 16.8853C85.5554 16.1224 85.1322 15.1709 84.9177 14.0309C84.7031 12.8909 84.745 11.8519 85.0434 10.9139C85.3548 9.97342 85.8867 9.19496 86.639 8.57854C87.3913 7.96211 88.3113 7.55157 89.3989 7.34691C90.4602 7.14718 91.4456 7.19241 92.3549 7.48258C93.2643 7.77275 94.0259 8.28744 94.6399 9.02665C95.267 9.76339 95.6841 10.6821 95.8912 11.7828ZM92.2851 11.5456C92.1766 10.969 91.8938 10.5474 91.4366 10.2807C90.9794 10.014 90.4559 9.93609 89.8663 10.047C89.3028 10.1531 88.8554 10.4069 88.5239 10.8084C88.2056 11.2075 88.0572 11.7171 88.0789 12.3371L92.2851 11.5456Z"
				fill="#04437C"
			/>
			<path
				d="M54.7722 34.7764C55.2671 42.9412 59.7377 46.4969 67.4158 48.5195C74.6087 50.4142 82.3756 50.8766 89.7712 50.2603C97.6611 49.6028 104.972 46.5955 112.493 44.366C121.592 41.6688 130.803 39.0736 140.254 37.9831C149.745 36.888 160.843 35.9282 169.908 39.7239C179.212 43.6195 186.062 53.9544 180.414 63.6368C175.335 72.344 161.864 69.8427 153.844 74.1732C145.368 78.7506 141.437 88.8262 139.46 97.5974C137.349 106.964 139.429 115.682 139.429 124.931"
				stroke="#04437C"
				stroke-width="3"
				stroke-linecap="round"
			/>
			<path
				d="M133.932 118.884C134.67 120.976 137.644 126.354 139.979 127.007C141.931 127.554 146.523 120.292 147.675 118.884"
				stroke="#04437C"
				stroke-width="3"
				stroke-linecap="round"
			/>
		</svg>
	</div>
</section>

<section
	class="max-w-screen-2xl mx-auto w-screen min-h-section relative justify-center flex flex-col space-y-8 my-8"
>
	<div class="w-full px-32 space-y-8">
		<div class="w-fit border-b-4 border-blue-dark">
			<h2 class="text-blue-dark text-2xl">Ou trouver nos associations sportives ?</h2>
		</div>
		<div class="w-full h-[800px] mt-4 mb-6">
			<Map view={initialView} zoom={initialZoom}>
				{#each data.data as asso}
					{#if asso.localisation}
						<Marker latLng={[asso.localisation.lat, asso.localisation.lon]} width={40} height={40}>
							<Popup>
								<h2 class="text-lg">{asso.nom_association}</h2>
								<div class="flex flex-col gap-1 mt-1">
									<span><i class="fa-solid fa-location-pin mr-1" /> {asso.adresse}</span>
									<span><i class="fa-solid fa-envelope mr-1" /> {asso.email}</span>
									<span><i class="fa-solid fa-phone mr-1" /> {asso.telephone}</span>
								</div>
							</Popup>
						</Marker>
					{/if}
				{/each}
			</Map>
		</div>
		<div class="w-full">
			<h2 class="text-blue-dark text-2xl font-bold">Infos complémentaires</h2>
			<div class="flex items-end w-full">
				<div class="w-full relative hoverShow">
					<div
						class="hoverElement hidden absolute w-full h-full z-10 bg-[#ffffffe6] items-center justify-center"
					>
						<a href="/" class="border border-blue-dark p-2 flex items-center space-x-4 bg-white">
							<p class="text-blue-dark">Voir images</p>
							<svg
								width="15"
								height="14"
								viewBox="0 0 15 14"
								fill="none"
								xmlns="http://www.w3.org/2000/svg"
							>
								<path
									d="M1 11.4V4.9C1 4.18203 1.58203 3.6 2.3 3.6H2.625C3.03418 3.6 3.41949 3.40735 3.665 3.08L5.108 1.156C5.18165 1.0578 5.29725 1 5.42 1H9.58C9.70278 1 9.81835 1.0578 9.892 1.156L11.335 3.08C11.5805 3.40735 11.9658 3.6 12.375 3.6H12.7C13.418 3.6 14 4.18203 14 4.9V11.4C14 12.118 13.418 12.7 12.7 12.7H2.3C1.58203 12.7 1 12.118 1 11.4Z"
									stroke="#04437C"
									stroke-linecap="round"
									stroke-linejoin="round"
								/>
								<path
									d="M7.50002 10.1C8.93594 10.1 10.1 8.93594 10.1 7.50002C10.1 6.06411 8.93594 4.90002 7.50002 4.90002C6.06408 4.90002 4.90002 6.06411 4.90002 7.50002C4.90002 8.93594 6.06408 10.1 7.50002 10.1Z"
									stroke="#04437C"
									stroke-linecap="round"
									stroke-linejoin="round"
								/>
							</svg>
						</a>
					</div>
					<div class="absolute border-y border-blue-dark w-full h-full"></div>
					<div class="absolute border-half-left w-full h-full"></div>
					<div class="absolute border-half-right w-full h-full"></div>
					<p class="p-8 font-bold">
						Lorem ipsum dolor sit, amet consectetur adipisicing elit. Harum, magni? Nisi, ullam! Cum
						amet, officia voluptas accusamus, nisi ab aut placeat animi odio, aspernatur sit dolor.
						Nulla consectetur aspernatur laboriosam?
					</p>
				</div>
				<a href="/" class="flex items-center gap-20 p-2 bg-blue-dark min-w-48 h-fit self-end">
					<p class="text-white">Contacer</p>
					<svg
						width="15"
						height="15"
						viewBox="0 0 15 15"
						fill="none"
						xmlns="http://www.w3.org/2000/svg"
					>
						<path d="M14 1L1 14M14 1H3M14 1V6V12" stroke="white" />
					</svg>
				</a>
			</div>
		</div>
	</div>
</section>

<style>
	.border-half-left:after {
		content: '';
		position: absolute;
		left: 0;
		bottom: 0;
		height: 50%;
		max-height: 50px;
		width: 1px;
		border-left: 1px solid #04437c;
	}
	.border-half-right:after {
		content: '';
		position: absolute;
		right: 0;
		top: 0;
		height: 50%;
		max-height: 50px;
		width: 1px;
		border-right: 1px solid #04437c;
	}

	.hoverShow:hover .hoverElement {
		display: flex;
		transition: all .5s ease-in-out;
	}
</style>
