<template>
<MkStickyContainer>
	<template #header><MkPageHeader :actions="headerActions" :tabs="headerTabs"/></template>
	<div style="overflow: clip;">
		<MkSpacer :content-max="600" :margin-min="20">
			<div class="_formRoot znqjceqz">
				<div id="debug"></div>
				<div ref="containerEl" v-panel class="_formBlock about" :class="{ playing: easterEggEngine != null }">
					<img src="/client-assets/about-icon.png" alt="" class="icon" draggable="false" @load="iconLoaded" @click="gravity"/>
					<div class="misskey">AZPick(based on CherryPick/Misskey)</div>
					<div class="version">v{{ version }}</div>
					<span v-for="emoji in easterEggEmojis" :key="emoji.id" class="emoji" :data-physics-x="emoji.left" :data-physics-y="emoji.top" :class="{ _physics_circle_: !emoji.emoji.startsWith(':') }"><MkEmoji class="emoji" :emoji="emoji.emoji" :custom-emojis="$instance.emojis" :is-reaction="false" :normal="true" :no-style="true"/></span>
				</div>
				<div class="_formBlock" style="text-align: center;">
					{{ i18n.ts._aboutMisskey.about }}<br><a href="https://misskey-hub.net/docs/misskey.html" target="_blank" class="_link">{{ i18n.ts.learnMore }}</a>
				</div>
				<div class="_formBlock" style="text-align: center;">
					<MkButton style="margin: 8px;" primary rounded inline @click="iLoveAZPick">I <Mfm text="$[jelly ❤]"/> #AZPick</MkButton>
					<MkButton style="margin: 8px;" primary rounded inline @click="iLoveAozorasky">I <Mfm text="$[jelly 🥰]"/> #Aozorasky</MkButton>
				</div>
				<FormSection>
					<template #label>Aozorasky</template>
						<div class="_formLinks">
							<FormLink to="https://aozora.uk" external>
								<template #icon><i class="fas fa-globe"></i></template>
								aozora.uk
								<template #suffix>aozora.uk</template>
							</FormLink>
							<FormLink to="https://aozora-uk.github.io/statuspage" external>
								<template #icon><i class="fas fa-plug"></i></template>
								Status Page
								<template #suffix>github.io</template>
							</FormLink>
							<FormLink to="https://github.com/aozora-uk/azpick" external>
								<template #icon><i class="fab fa-git-alt"></i></template>
								{{ i18n.ts._aboutMisskey.source }}
								<template #suffix>Github</template>
							</FormLink>
						</div>
				</FormSection>
				<FormSection>
					<template #label>CherryPick</template>
					<div class="_formLinks">
						<FormLink to="https://github.com/kokonect-link/cherrypick" external>
							<template #icon><i class="fab fa-git-alt"></i></template>
							{{ i18n.ts._aboutMisskey.source }}
							<template #suffix>GitHub</template>
						</FormLink>
						<!--
						<FormLink to="https://crowdin.com/project/misskey" external>
							<template #icon><i class="fas fa-language"></i></template>
							{{ i18n.ts._aboutMisskey.translation }}
							<template #suffix>Crowdin</template>
						</FormLink>
						-->
						<FormLink to="https://discord.gg/V8qghB28Aj" external>
							<template #icon><i class="fab fa-discord"></i></template>
							{{ i18n.ts._aboutMisskey._cherrypick.community }}
							<template #suffix>Discord</template>
						</FormLink>
						<FormLink to="https://www.patreon.com/noridev" external>
							<template #icon><i class="fas fa-hand-holding-medical"></i></template>
							{{ i18n.ts._aboutMisskey._cherrypick.donate }}
							<template #suffix>Patreon</template>
						</FormLink>
						<FormLink to="https://www.paypal.me/noridev" external>
							<template #icon><i class="fas fa-hand-holding-medical"></i></template>
							{{ i18n.ts._aboutMisskey._cherrypick.donate }}
							<template #suffix>PayPal</template>
						</FormLink>
						<FormLink to="https://toss.me/noridev" external>
							<template #icon><i class="fas fa-hand-holding-medical"></i></template>
							{{ i18n.ts._aboutMisskey._cherrypick.donate }}
							<template #suffix>Toss</template>
						</FormLink>
					</div>
				</FormSection>
				<FormSection>
					<template #label>Misskey</template>
					<div class="_formLinks">
						<FormLink to="https://github.com/misskey-dev/misskey" external>
							<template #icon><i class="fab fa-git-alt"></i></template>
							{{ i18n.ts._aboutMisskey.source }}
							<template #suffix>GitHub</template>
						</FormLink>
						<FormLink to="https://crowdin.com/project/misskey" external>
							<template #icon><i class="fas fa-language"></i></template>
							{{ i18n.ts._aboutMisskey.translation }}
							<template #suffix>Crowdin</template>
						</FormLink>
						<FormLink to="https://www.patreon.com/syuilo" external>
							<template #icon><i class="fas fa-hand-holding-medical"></i></template>
							{{ i18n.ts._aboutMisskey.donate }}
							<template #suffix>Patreon</template>
						</FormLink>
					</div>
					<template #caption><MkLink url="https://github.com/misskey-dev/misskey/graphs/contributors">{{ i18n.ts._aboutMisskey.allContributors }}</MkLink></template>
				</FormSection>
				<FormSection>
					<template #label>{{ i18n.ts._aboutMisskey.contributors }}</template>
					<div :class="$style.contributors">
						<a href="https://github.com/syuilo" target="_blank" :class="$style.contributor">
							<img src="https://avatars.githubusercontent.com/u/4439005?v=4" :class="$style.contributorAvatar">
							<span :class="$style.contributorUsername">@syuilo(Misskey)</span>
						</a>
						<a href="https://github.com/tamaina" target="_blank" :class="$style.contributor">
							<img src="https://avatars.githubusercontent.com/u/7973572?v=4" :class="$style.contributorAvatar">
							<span :class="$style.contributorUsername">@tamaina(Misskey)</span>
						</a>
						<a href="https://github.com/mei23" target="_blank" :class="$style.contributor">
							<img src="https://avatars.githubusercontent.com/u/30769358?v=4" :class="$style.contributorAvatar">
							<span :class="$style.contributorUsername">@mei23(Misskey&v12-lts)</span>
						</a>
						<a href="https://github.com/r-ca" target="_blank" :class="$style.contributor">
							<img src="https://avatars.githubusercontent.com/u/66072112?v=4" :class="$style.contributorAvatar">
							<span :class="$style.contributorUsername">@r-ca(rca-fedi/cp&yoiyami)</span>
						</a>
						<a href="https://github.com/noridev" target="_blank" :class="$style.contributor">
							<img src="https://avatars.githubusercontent.com/u/11006910?v=4" :class="$style.contributorAvatar">
							<span :class="$style.contributorUsername">@noridev(Cherrypick)</span>
						</a>
						<a href="https://github.com/morotesovtannu" target="_blank" :class="$style.contributor">
							<img src="https://avatars.githubusercontent.com/u/68218785?v=4" :class="$style.contributorAvatar">
							<span :class="$style.contributorUsername">@morotesovtannu(AZPick)</span>
						</a>
					</div>
					<template #caption><MkLink url="https://github.com/aozora-uk/azpick/graphs/contributors">{{ i18n.ts._aboutMisskey.allContributors }}</MkLink></template>
				</FormSection>
				<FormSection>
					<template #label><Mfm text="$[jelly ❤]"/> {{ i18n.ts._aboutMisskey.patrons }}</template>
					<div v-for="patron in patrons" :key="patron">{{ patron }}</div>
					<template #caption>{{ i18n.ts._aboutMisskey.morePatrons }}</template>
				</FormSection>
			</div>
		</MkSpacer>
	</div>
</MkStickyContainer>
</template>

<script lang="ts" setup>
import { nextTick, onBeforeUnmount } from 'vue';
import { version } from '@/config';
import FormLink from '@/components/form/link.vue';
import FormSection from '@/components/form/section.vue';
import MkButton from '@/components/MkButton.vue';
import MkLink from '@/components/MkLink.vue';
import { physics } from '@/scripts/physics';
import { i18n } from '@/i18n';
import { defaultStore } from '@/store';
import * as os from '@/os';
import { definePageMetadata } from '@/scripts/page-metadata';

const patrons = [
	'まっちゃとーにゅ',
	'mametsuko',
	'noellabo',
	'AureoleArk',
	'Gargron',
	'Nokotaro Takeda',
	'Suji Yan',
	'oi_yekssim',
	'regtan',
	'Hekovic',
	'nenohi',
	'Gitmo Life Services',
	'naga_rus',
	'Efertone',
	'Melilot',
	'motcha',
	'nanami kan',
	'sevvie Rose',
	'Hayato Ishikawa',
	'Puniko',
	'skehmatics',
	'Quinton Macejkovic',
	'YUKIMOCHI',
	'dansup',
	'mewl hayabusa',
	'Emilis',
	'Fristi',
	'makokunsan',
	'chidori ninokura',
	'Peter G.',
	'見当かなみ',
	'natalie',
	'Maronu',
	'Steffen K9',
	'takimura',
	'sikyosyounin',
	'Nesakko',
	'YuzuRyo61',
	'blackskye',
	'sheeta.s',
	'osapon',
	'public_yusuke',
	'CG',
	'吴浥',
	't_w',
	'Jerry',
	'nafuchoco',
	'Takumi Sugita',
	'GLaTAN',
	'mkatze',
	'kabo2468y',
	'mydarkstar',
	'Roujo',
	'DignifiedSilence',
	'uroco @99',
	'totokoro',
	'うし',
	'kiritan',
	'weepjp',
	'Liaizon Wakest',
	'Duponin',
	'Blue',
	'Naoki Hirayama',
	'wara',
	'Wataru Manji (manji0)',
	'みなしま',
	'kanoy',
	'xianon',
	'Denshi',
	'Osushimaru',
	'にょんへら',
	'おのだい',
	'Leni',
	'oss',
	'Weeble',
	'蝉暮せせせ',
	'ThatOneCalculator',
	'pixeldesu',
];

let isKokonect = false;

let easterEggReady = false;
let easterEggEmojis = $ref([]);
let easterEggEngine = $ref(null);
const containerEl = $ref<HTMLElement>();

const meta = await os.api('meta', { detail: true });
if (meta.uri == 'https://kokonect.link' || 'http://localhost:3000') isKokonect = true;

function iconLoaded() {
	const emojis = defaultStore.state.reactions;
	const containerWidth = containerEl.offsetWidth;
	for (let i = 0; i < 32; i++) {
		easterEggEmojis.push({
			id: i.toString(),
			top: -(128 + (Math.random() * 256)),
			left: (Math.random() * containerWidth),
			emoji: emojis[Math.floor(Math.random() * emojis.length)],
		});
	}

	nextTick(() => {
		easterEggReady = true;
	});
}

function gravity() {
	if (!easterEggReady) return;
	easterEggReady = false;
	easterEggEngine = physics(containerEl);
}

function iLoveAZPick() {
	os.post({
		initialText: 'I $[jelly ❤] #AZPick',
		instant: true,
	});
}
function iLoveAozorasky() {
	os.post({
		initialText: 'I $[jelly 🥰] #Aozorasky',
		instant: true,
	});
}

onBeforeUnmount(() => {
	if (easterEggEngine) {
		easterEggEngine.stop();
	}
});

const headerActions = $computed(() => []);

const headerTabs = $computed(() => []);

definePageMetadata({
	title: i18n.ts.aboutMisskey,
	icon: null,
});
</script>

<style lang="scss" scoped>
.znqjceqz {
	> .about {
		position: relative;
		text-align: center;
		padding: 16px;
		border-radius: var(--radius);

		&.playing {
			&, * {
				user-select: none;
			}

			* {
				will-change: transform;
			}

			> .emoji {
				visibility: visible;
			}
		}

		> .icon {
			display: block;
			width: 100px;
			margin: 0 auto;
			border-radius: 16px;
		}

		> .misskey {
			margin: 0.75em auto 0 auto;
			width: max-content;
		}

		> .version {
			margin: 0 auto;
			width: max-content;
			opacity: 0.5;
		}

		> .emoji {
			position: absolute;
			top: 0;
			left: 0;
			visibility: hidden;

			> .emoji {
				pointer-events: none;
				font-size: 24px;
				width: 24px;
			}
		}
	}
}
</style>

<style lang="scss" module>
.contributors {
	display: grid;
	grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
	grid-gap: 12px;
}
.contributor {
	display: flex;
	align-items: center;
	padding: 12px;
	background: var(--buttonBg);
	border-radius: 6px;
	&:hover {
		text-decoration: none;
		background: var(--buttonHoverBg);
	}
	&.active {
		color: var(--accent);
		background: var(--buttonHoverBg);
	}
}
.contributorAvatar {
	width: 30px;
	border-radius: 100%;
}
.contributorUsername {
	margin-left: 12px;
}
</style>
