<i18n>
{
  "en": {
    "name": "Name",
    "twitch": "Twitch",
    "countryCode": "Country Code",
    "removePlayer": "Remove Player"
  },
  "ja": {
    "name": "プレイヤー名",
    "twitch": "Twitch ID",
    "countryCode": "国名コード",
    "removePlayer": "プレイヤーの削除"
  }
}
</i18n>

<template>
  <div class="Player d-flex align-center">
    <v-icon class="PlayerHandle">
      mdi-drag-vertical
    </v-icon>
    <text-input
      v-model="playerData.name"
      :label="$t('name')"
    />
    <text-input
      v-model="playerData.social.twitch"
      :label="$t('twitch')"
      left-border
    />
    <text-input
      v-model="playerData.country"
      :label="$t('countryCode')"
      left-border
    />
    <modify-button
      :style="{ 'margin-left': '5px' }"
      icon="mdi-account-minus"
      :tooltip="$t('removePlayer')"
      @click="removePlayer"
    />
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import store from '../store';
import TextInput from './TextInput.vue';
import ModifyButton from './ModifyButton.vue';

export default Vue.extend({
  name: 'Player',
  components: {
    TextInput,
    ModifyButton,
  },
  props: {
    playerData: {
      type: Object,
      default(): object {
        return {};
      },
    },
  },
  methods: {
    removePlayer(): void {
      store.commit('removePlayer', {
        teamID: this.playerData.teamID,
        id: this.playerData.id,
      });
    },
  },
});
</script>
