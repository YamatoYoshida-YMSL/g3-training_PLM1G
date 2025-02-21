<script setup>
import { useLockScreen } from 'viy-ui';
import { useI18n } from 'vue-i18n';

const { t } = useI18n();
const { lockScreen } = useLockScreen();

defineOptions({
  name: 'ZmnSearchResult',
});

const form = ref();
const viy2Card_12d5Ci = ref();
const viy2Table_W8DXb = ref();
const viy2Button_Wa4Vh = ref();
const viy2Button_9nX3KC = ref();
const viy2divider_WciTg = ref();
const viy2Radio_Wb7hI = ref();
const viy2Radio_9nO97I = ref();
const viy2Radio_9nOxXS = ref();
const viy2Radio_9nOWuc = ref();
const viy2Radio_9nPTW0 = ref();
const viy2Button_9nVeAE = ref();
const viy2Button_Wa3Zn = ref();
const viy2Radio_WcGoU = ref();

const formData = reactive({
  datafieldviy2Radio_Wb7hI: '', datafieldviy2Radio_Wb7hI: '', datafieldviy2Radio_Wb7hI: '', datafieldviy2Radio_Wb7hI: '', datafieldviy2Radio_Wb7hI: '', datafieldviy2Radio_WcGoU: '',
});

const viy2Table_W8DXbEditConfig = reactive({
  trigger: 'click',

});

const viy2Table_W8DXbMouseConfig = reactive({

  extension: true,

});

const viy2Radio_Wb7hIOpts = reactive([
  { value: 'G2E', label: 'G2E' },
  { value: 'G3E', label: 'G3E' },
  { value: 'G4-1', label: 'G4-1' },
  { value: 'G4-2', label: 'G4-2' },
  { value: 'G4W', label: 'G4W' },
  { value: 'G5E', label: 'G5E' },
]);

const viy2Radio_9nO97IOpts = reactive([
  { value: 'FGC', label: 'FGC' },
  { value: '浜北', label: '浜北' },
  { value: '中瀬', label: '中瀬' },
  { value: '新居技術棟4F', label: '新居技術棟4F' },
]);

const viy2Radio_9nOxXSOpts = reactive([
  { value: 'Option 1', label: 'Option 1' },
  { value: 'Option 2', label: 'Option 2' },
]);

const viy2Radio_9nOWucOpts = reactive([
  { value: 'Option 1', label: 'Option 1' },
  { value: 'Option 2', label: 'Option 2' },
]);

const viy2Radio_9nPTW0Opts = reactive([
  { value: 'Option 1', label: 'Option 1' },
  { value: 'Option 2', label: 'Option 2' },
  { value: 'Option 3', label: 'Option 3' },
  { value: 'Option', label: 'Option' },
  { value: 'Option', label: 'Option' },
  { value: 'Option', label: 'Option' },
  { value: 'Option', label: 'Option' },
]);

const viy2Radio_WcGoUOpts = reactive([
  { value: 'G5フリーコピー室', label: 'G5フリーコピー室' },
  { value: 'G5出図室', label: 'G5出図室' },
  { value: 'YMSLテスト', label: 'YMSLテスト' },
  { value: '品証専用（総務SC）', label: '品証専用（総務SC）' },
]);

const viy2Table_W8DXbViy2TableInputLinkColumn_W9od1EditRender = computed(() => {
  return {
    enabled: false,
    target: '_blank',
  };
});

const viy2Table_W8DXbPLOTOEditRender = computed(() => {
  return {
    enabled: false,
  };
});
</script>

<template>
  <VueForm ref="form" v-loading="lockScreen" :model="formData">
    <VueCard

      id="viy2Card_12d5Ci"
      ref="viy2Card_12d5Ci"
    >
      <template #header>
        <VueText id="viy2Text_W5UIO" ref="viy2Text_W5UIO" :style="{ width: '100%', display: 'inline-block', textAlign: 'left', fontSize: '30px' }">
          YMC-APOLO 検索結果
        </VueText>

        <VueText id="viy2Text_W7NRO" ref="viy2Text_W7NRO" :style="{ width: '100%', display: 'inline-block' }">
          ・部品番号をクリックするとイメージが表示されます
        </VueText>

        <VueText id="viy2Text_9ngaIi" ref="viy2Text_9ngaIi" :style="{ width: '100%', display: 'inline-block' }">
          ・PLOT機能の使用方法はヘルプを参照ください
        </VueText>

        <VueText id="viy2Text_9ng9o2" ref="viy2Text_9ng9o2" type="danger" :style="{ width: '100%', display: 'inline-block' }">
          　PLOT機能以外での印刷は禁止です
        </VueText>

        <VueText id="viy2Text_9ng8x8" ref="viy2Text_9ng8x8" :style="{ width: '100%', display: 'inline-block' }">
          　やむをえず印刷する場合は、Printkeyを起動した状態で"PrintScreen"キーを押してください
        </VueText>
      </template>
      <VueText id="viy2Text_W7AOI" ref="viy2Text_W7AOI" :style="{ width: '100%', display: 'inline-block' }" />

      <VueText id="viy2Text_9neuFa" ref="viy2Text_9neuFa" :style="{ width: '100%', display: 'inline-block' }" />

      <VueTable

        id="viy2Table_W8DXb"
        ref="viy2Table_W8DXb"

        :edit-config="viy2Table_W8DXbEditConfig"
        :mouse-config="viy2Table_W8DXbMouseConfig"
      >
        <VueSelectionColumn

          align="center"

          width="50px"

          header-align="center"

          type="checkbox"
        />

        <VueIndexColumn

          align="center"

          width="50px"

          min-width="50px"

          header-align="center"
        />

        <VueInputLinkColumn

          :edit-render="viy2Table_W8DXbViy2TableInputLinkColumn_W9od1EditRender"

          title="inputlink"

          width="200px"
        />
        <VueRadioColumn

          :edit-render="viy2Table_W8DXbPLOTOEditRender"

          field="PLOTO"

          width="200px"

          title="PLOTO"
        />
        <VueText id="viy2Text_W9T25" ref="viy2Text_W9T25" :style="{ width: '100%', display: 'inline-block' }">
          Info1
        </VueText>
        <VueText id="viy2Text_9nAZEm" ref="viy2Text_9nAZEm" :style="{ width: '100%', display: 'inline-block' }">
          Info2
        </VueText>
      </VueTable>

      <VueButton id="viy2Button_Wa4Vh" ref="viy2Button_Wa4Vh" icon-position="left">
        DISPYAY
      </VueButton>

      <VueButton id="viy2Button_9nX3KC" ref="viy2Button_9nX3KC" icon-position="left">
        DISPLAY CHECK CLEAR
      </VueButton>

      <VueDivider

        id="viy2divider_WciTg"
        ref="viy2divider_WciTg"
      />

      <VueText id="viy2Text_Wb1Gh" ref="viy2Text_Wb1Gh" :style="{ width: '100%', display: 'inline-block' }">
        出力プロッターを選択して下さい
      </VueText>

      <VueFormItem

        prop="datafieldviy2Radio_Wb7hI"
      >
        <VueRadioGroup

          id="viy2Radio_Wb7hI"

          ref="viy2Radio_Wb7hI"
          v-model="formData.datafieldviy2Radio_Wb7hI"

          direction="horizontal"

          split-size="default"
        >
          <VueRadio
            v-for="option in viy2Radio_Wb7hIOpts"
            :key="option.value"
            :label="option.value"
          >
            {{ option.label }}
          </VueRadio>
        </VueRadioGroup>
      </VueFormItem>

      <VueText id="viy2Text_9nNo0U" ref="viy2Text_9nNo0U" :style="{ width: '100%', display: 'inline-block' }">
        出力プロッターを選択して下さい
      </VueText>

      <VueFormItem

        prop="datafieldviy2Radio_Wb7hI"
      >
        <VueRadioGroup

          id="viy2Radio_9nO97I"

          ref="viy2Radio_9nO97I"
          v-model="formData.datafieldviy2Radio_Wb7hI"

          direction="horizontal"

          split-size="default"
        >
          <VueRadio
            v-for="option in viy2Radio_9nO97IOpts"
            :key="option.value"
            :label="option.value"
          >
            {{ option.label }}
          </VueRadio>
        </VueRadioGroup>
      </VueFormItem>

      <VueText id="viy2Text_9nOll8" ref="viy2Text_9nOll8" :style="{ width: '100%', display: 'inline-block' }">
        出力プロッターを選択して下さい
      </VueText>

      <VueFormItem

        prop="datafieldviy2Radio_Wb7hI"
      >
        <VueRadioGroup

          id="viy2Radio_9nOxXS"

          ref="viy2Radio_9nOxXS"
          v-model="formData.datafieldviy2Radio_Wb7hI"

          direction="horizontal"

          split-size="default"
        >
          <VueRadio
            v-for="option in viy2Radio_9nOxXSOpts"
            :key="option.value"
            :label="option.value"
          >
            {{ option.label }}
          </VueRadio>
        </VueRadioGroup>
      </VueFormItem>

      <VueText id="viy2Text_9nOKp0" ref="viy2Text_9nOKp0" :style="{ width: '100%', display: 'inline-block' }">
        出力プロッターを選択して下さい
      </VueText>

      <VueFormItem

        prop="datafieldviy2Radio_Wb7hI"
      >
        <VueRadioGroup

          id="viy2Radio_9nOWuc"

          ref="viy2Radio_9nOWuc"
          v-model="formData.datafieldviy2Radio_Wb7hI"

          direction="horizontal"

          split-size="default"
        >
          <VueRadio
            v-for="option in viy2Radio_9nOWucOpts"
            :key="option.value"
            :label="option.value"
          >
            {{ option.label }}
          </VueRadio>
        </VueRadioGroup>
      </VueFormItem>

      <VueText id="viy2Text_9nPGHO" ref="viy2Text_9nPGHO" :style="{ width: '100%', display: 'inline-block' }">
        出力プロッターを選択して下さい
      </VueText>

      <VueFormItem

        prop="datafieldviy2Radio_Wb7hI"
      >
        <VueRadioGroup

          id="viy2Radio_9nPTW0"

          ref="viy2Radio_9nPTW0"
          v-model="formData.datafieldviy2Radio_Wb7hI"

          direction="horizontal"

          split-size="default"
        >
          <VueRadio
            v-for="option in viy2Radio_9nPTW0Opts"
            :key="option.value"
            :label="option.value"
          >
            {{ option.label }}
          </VueRadio>
        </VueRadioGroup>
      </VueFormItem>

      <VueButton id="viy2Button_9nVeAE" ref="viy2Button_9nVeAE" icon-position="left">
        PLOT
      </VueButton>

      <VueButton id="viy2Button_Wa3Zn" ref="viy2Button_Wa3Zn" icon-position="left">
        PLOTO CLEAR
      </VueButton>

      <VueText id="viy2Text_Wcf0f" ref="viy2Text_Wcf0f" type="danger" :style="{ width: '100%', display: 'inline-block' }">
        プロット出力依頼結果画面はブラウザの右上にある[X]で都度閉じて下さい。
      </VueText>

      <VueText id="viy2Text_9nYvtG" ref="viy2Text_9nYvtG" type="danger" :style="{ width: '100%', display: 'inline-block' }">
        [-]を使った場合は画面はタスクバーに残り、次のプロット依頼結果がわかりにくい状況になります。
      </VueText>

      <VueText id="viy2Text_WczSf" ref="viy2Text_WczSf" :style="{ width: '100%', display: 'inline-block' }">
        -- 特殊 ---
      </VueText>

      <VueFormItem

        prop="datafieldviy2Radio_WcGoU"
      >
        <VueRadioGroup

          id="viy2Radio_WcGoU"

          ref="viy2Radio_WcGoU"
          v-model="formData.datafieldviy2Radio_WcGoU"

          direction="horizontal"

          split-size="default"
        >
          <VueRadio
            v-for="option in viy2Radio_WcGoUOpts"
            :key="option.value"
            :label="option.value"
          >
            {{ option.label }}
          </VueRadio>
        </VueRadioGroup>
      </VueFormItem>

      <VueText id="viy2Text_9o55E8" ref="viy2Text_9o55E8" :style="{ width: '100%', display: 'inline-block', color: '#41B55E' }">
        Ｇ５フリーコピー室へのプロットは設計管理／試作管理／ＡＭ技管、Ｇ５出図室へのプロットは設計管理に限定します。 その他の部署の方は選択しないで下さい。
      </VueText>
    </VueCard>
  </VueForm>
</template>
