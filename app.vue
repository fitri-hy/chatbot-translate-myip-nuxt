<template>
	<div class="bg-slate-100">
	  <div class="flex gap-2 items-center justify-center max-w-3xl m-auto">
		<div class="flex gap-4 flex-col items-center pl-2">
			<button class="bg-white shadow rounded-lg p-3" tabindex="1" @click="currentTab = 'tab1'">
				<svg width="30" height="30" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
				  <image xlink:href="http://hytech-icons.vercel.app/icons/pro/regular/robot.svg" width="24" height="24"/>
				</svg>
			</button>
			<button class="bg-white shadow rounded-lg p-3" tabindex="2" @click="currentTab = 'tab2'">
				<svg width="30" height="30" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
				  <image xlink:href="http://hytech-icons.vercel.app/icons/pro/regular/language.svg" width="24" height="24"/>
				</svg>
			</button>
			<button class="bg-white shadow rounded-lg p-3" tabindex="3" @click="currentTab = 'tab3'">
				<svg width="30" height="30" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
				  <image xlink:href="http://hytech-icons.vercel.app/icons/pro/ionicons/git-network-sharp.svg" width="24" height="24"/>
				</svg>
			</button>
			<a href="https://github.com/fitri-hy" class="bg-white shadow rounded-lg p-3">
				<svg width="30" height="30" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
				  <image xlink:href="http://hytech-icons.vercel.app/icons/pro/brands/github.svg" width="24" height="24"/>
				</svg>
			</a>
			<a href="https://hy-tech.my.id/" class="bg-white shadow rounded-lg p-3">
				<svg width="30" height="30" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
				  <image xlink:href="http://hytech-icons.vercel.app/icons/pro/business/global-fill.svg" width="24" height="24"/>
				</svg>
			</a>
			<button class="bg-white shadow rounded-lg p-3" tabindex="4" @click="currentTab = 'tab4'">
				<svg width="30" height="30" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
				  <image xlink:href="http://hytech-icons.vercel.app/icons/pro/sharp-solid/circle-info.svg" width="24" height="24"/>
				</svg>
			</button>
		</div>
		<div v-if="currentTab === 'tab1'" class="w-full h-screen py-4">
			<h2 class="absolute font-bold text-xl bg-blue-500 px-4 py-1 text-white" style="border-top-left-radius: 10px 10px;">Chatbot AI</h2>
			<div class="bg-white h-full px-4 py-6 rounded-lg overflow-y-auto w-full max-w-screen-md mx-auto">
				<div v-for="(message, index) in CHATBOTmessages" :key="index" class="mb-14">
					<div :class="{ 'flex justify-end': message.isUser, 'flex justify-start': !message.isUser }">
						<div :class="{ 'text-right text-gray-800 bg-gray-100 shadow px-4 py-2 rounded-lg rounded-br-none': message.isUser, 'text-left shadow text-gray-600 bg-gray-200 px-4 py-2 rounded-lg rounded-bl-none': !message.isUser }" class="rounded-lg max-w-sm">
							{{ message.text }}
						</div>
					</div>
				</div>
				<div class="absolute bottom-9 left-1/2 transform -translate-x-1/2 gap-2 inline-flex items-center justify-between w-full rounded-3xl px-4 max-w-xl mx-auto ml-8">
					<input v-model="CHATBOTinputMessage" @keyup.enter="ChatbotAI" placeholder="Ketik pertanyaan Anda di sini..." class="w-full p-3 bg-gray-100 focus:outline-none border rounded-lg" />
					<button @click="ChatbotAI" class="px-4 py-2 bg-blue-500 text-white rounded-lg hover:bg-blue-600 focus:outline-none">Ask</button>
				</div>
			</div>
		</div>
		<div v-else-if="currentTab === 'tab2'" class="w-full h-screen py-4">
			<h2 class="absolute font-bold text-xl bg-blue-500 px-4 py-1 text-white" style="border-top-left-radius: 10px 10px;">Translate</h2>
			<div class="flex flex-col justify-center gap-4 h-full bg-white px-4 pt-12 pb-4 rounded-lg overflow-y-auto w-full">
				<textarea class="w-full bg-gray-100 p-3 rounded-lg h-full" v-model="TRANSLATEquery" placeholder="Masukkan teks"></textarea>
				<div class="flex gap-4 justify-between">
					<select v-model="TRANSLATEtargetLanguage" class="px-4 py-2 rounded-lg">
						<option value="en">Inggris</option>
						<option value="id">Indonesia</option>
						<option value="ar">Arab</option>
						<option value="zh">Cina (Mandarin)</option>
						<option value="fr">Perancis</option>
						<option value="de">Jerman</option>
						<option value="hi">Hindi</option>
						<option value="it">Italia</option>
						<option value="ja">Jepang</option>
						<option value="ko">Korea</option>
						<option value="ms">Melayu</option>
						<option value="pt">Portugis</option>
						<option value="ru">Rusia</option>
						<option value="es">Spanyol</option>
						<option value="th">Thai</option>
						<option value="tr">Turki</option>
						<option value="vi">Vietnam</option>
						<option value="af">Afrikaans</option>
						<option value="sq">Albania</option>
						<option value="am">Amharik</option>
						<option value="hy">Armenia</option>
						<option value="az">Azerbaijan</option>
						<option value="eu">Basque</option>
						<option value="bn">Benggala</option>
						<option value="bs">Bosnia</option>
						<option value="bg">Bulgaria</option>
						<option value="ca">Catalan</option>
						<option value="hr">Kroasia</option>
						<option value="cs">Ceko</option>
						<option value="da">Denmark</option>
						<option value="nl">Belanda</option>
						<option value="eo">Esperanto</option>
						<option value="et">Estonia</option>
					</select>
					<button @click="Translate" class="px-4 py-2 bg-blue-500 hover:bg-blue-600 rounded-lg text-white">Translate</button>
				</div>
				<textarea class="w-full bg-gray-100 p-3 rounded-lg h-full" readonly>{{ TRANSLATEtranslatedText }}</textarea>
			</div>
		</div>
		  <div v-else-if="currentTab === 'tab3'" class="w-full h-screen py-4">
			<h2 class="absolute font-bold text-xl bg-blue-500 px-4 py-1 text-white" style="border-top-left-radius: 10px 10px;">My IP</h2>
			<div class="flex flex-col gap-4 h-full bg-white px-4 py-12 rounded-lg overflow-y-auto w-full py-6">
				<h1 class="text-2xl font-bold tect-gray-700 text-center">Informasi IP Anda</h1>
				<div class="mt-6 grid grid-cols-2 gap-4">
				  <div class="flex flex-col bg-gray-100 p-4 rounded-lg text-gray-600 text-center">
					<span class="text-lg font-semibold">IP</span>
					<span class="text-xl font-bold text-blue-500">{{ MYIPipAddress }}</span>
				  </div>
				  <div class="flex flex-col bg-gray-100 p-4 rounded-lg text-gray-600 text-center">
					<span class="text-lg font-semibold">Negara</span>
					<span class="text-xl font-bold text-blue-500">{{ MYIPcountry }}</span>
				  </div>
				  <div class="flex flex-col bg-gray-100 p-4 rounded-lg text-gray-600 text-center">
					<span class="text-lg font-semibold">Region</span>
					<span class="text-xl font-bold text-blue-500">{{ MYIPregion }}</span>
				  </div>
				  <div class="flex flex-col bg-gray-100 p-4 rounded-lg text-gray-600 text-center">
					<span class="text-lg font-semibold">Kota</span>
					<span class="text-xl font-bold text-blue-500">{{ MYIPcity }}</span>
				  </div>
				  <div class="flex flex-col bg-gray-100 p-4 rounded-lg text-gray-600 text-center">
					<span class="text-lg font-semibold">Latitude</span>
					<span class="text-xl font-bold text-blue-500">{{ MYIPlatitude }}</span>
				  </div>
				  <div class="flex flex-col bg-gray-100 p-4 rounded-lg text-gray-600 text-center">
					<span class="text-lg font-semibold">Longitude</span>
					<span class="text-xl font-bold text-blue-500">{{ MYIPlongitude }}</span>
				  </div>
				</div>
				<div class="flex flex-col bg-gray-100 p-4 rounded-lg text-gray-600 text-center">
					<span class="text-lg font-semibold">ISP</span>
					<span class="text-xl font-bold text-blue-500">{{ MYIPisp }}</span>
				</div>
				<div class="flex flex-col bg-gray-100 p-4 rounded-lg text-gray-600 text-center">
					<span class="text-lg font-semibold">Organisasi</span>
					<span class="text-xl font-bold text-blue-500">{{ MYIPorganization }}</span>
				</div>
			</div>
		  </div>
		  <div v-else-if="currentTab === 'tab4'" class="w-full h-screen py-4">
			<h2 class="absolute font-bold text-xl bg-blue-500 px-4 py-1 text-white" style="border-top-left-radius: 10px 10px;">About</h2>
			<div class="flex flex-col gap-4 h-full bg-white px-6 py-9 round-lg overflow-y-auto w-full">
				<img class="h-24 w-24 m-auto" src="https://hy-tech.my.id/images/logo.png" />
				<h2 class="text-center font-semibold text-gray-700 text-2xl -mt-12">Nuxt + Vue Basic Application</h2>
				<p>
				Nuxt + Vue Basic Application is a platform that combines the power of Nuxt.js, a Vue.js framework used to create powerful and scalable web applications, with the capabilities of Vue.js, a JavaScript library focused on developing responsive user interfaces and interactive.
				</p>
				<strong>This application has several key features, including:</strong>
				<ul class="decimal-list-inside">
					<li class="mb-2">
						<strong>AI Chatbot</strong>: This feature allows users to interact with intelligent and responsive chatbots. These chatbots can provide answers to user questions, provide recommendations, or perform certain tasks based on user requests.
					</li>
					<li class="mb-2">
						<strong>Translate</strong>: The translation feature allows users to translate text from one language to another instantly. By using the available translation services, users can easily communicate in a language they understand or translate content from another language into the language they want.
					</li>
					<li class="mb-2">
						<strong>MyIP</strong>: The MyIP feature provides information about the user's IP address. This can be useful in various scenarios, such as for debugging purposes, security, or to provide customized services based on the user's geographic location.
					</li>
				</ul>
				<p>
					Apart from these main features, this application can also be developed by adding additional features according to user needs. With a modular and flexible design, developers can easily add or remove features according to the needs of the project being carried out.
				</p>
				<p class="mt-12 py-4 text-center text-gray-500">
					©2024 <a class="text-blue-500" href="https://hy-tech.my.id/">Fitri HY</a>. All rights reserved.
				</p>
			</div>
		  </div>
	  </div>
	</div>
</template>


<script>
export default {
  data() {
    return {
      CHATBOTinputMessage: '',
      CHATBOTmessages: [],
      currentTab: 'tab1',
	  
	  TRANSLATEquery: '',
      TRANSLATEtargetLanguage: 'en',
      TRANSLATEtranslatedText: '',
	  
	  MYIPipAddress: "",
      MYIPcountry: "",
      MYIPregion: "",
      MYIPcity: "",
      MYIPisp: "",
      MYIPorganization: "",
      MYIPlatitude: "",
      MYIPlongitude: ""
    };
  },
  methods: {
    async ChatbotAI() {
      if (this.CHATBOTinputMessage.trim() === '') return;

      this.CHATBOTmessages.push({ text: this.CHATBOTinputMessage, isUser: true });
      this.CHATBOTinputMessage = '';

      try {
        const response = await fetch(`https://api.hy-tech.my.id/api/gemini/${this.CHATBOTmessages[this.CHATBOTmessages.length - 1].text}`);
        const data = await response.json();

        this.CHATBOTmessages.push({ text: data.text, isUser: false });
      } catch (error) {
        console.error('Error fetching data:', error);
        this.CHATBOTmessages.push({ text: 'Maaf, terjadi kesalahan dalam mengambil jawaban.', isUser: false });
      }
    },
	Translate() {
      const apiUrl = `https://api.hy-tech.my.id/api/translate?text=${this.TRANSLATEquery}&target=${this.TRANSLATEtargetLanguage}`;
      fetch(apiUrl)
        .then(response => {
          if (!response.ok) {
            throw new Error('Terjadi kesalahan saat mengambil data terjemahan.');
          }
          return response.json();
        })
        .then(data => {
          this.TRANSLATEtranslatedText = data.translation;
        })
        .catch(error => {
          console.error('Error:', error);
        });
    },
	fetchMyIp() {
      const apiUrl = `https://api.hy-tech.my.id/api/myip`;
      fetch(apiUrl)
        .then((response) => {
          if (!response.ok) {
            throw new Error("Gagal mengambil data IP");
          }
          return response.json();
        })
        .then((data) => {
          this.MYIPipAddress = data.ip;
          this.MYIPcountry = data.country;
          this.MYIPregion = data.region;
          this.MYIPcity = data.city;
          this.MYIPisp = data.isp;
          this.MYIPorganization = data.organization;
          this.MYIPlatitude = data.latitude;
          this.MYIPlongitude = data.longitude;
        })
        .catch(error => {
          console.error('Error:', error);
        });
    },
  },
  mounted() {
    this.fetchMyIp();
  },
};
</script>
