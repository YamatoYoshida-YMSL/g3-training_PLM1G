<script setup>
import { useLockScreen } from 'viy-ui';
import { useI18n } from 'vue-i18n';

const { t } = useI18n();
const { lockScreen } = useLockScreen();

defineOptions({
  name: 'sampleAPOLO',
});

const form = ref();
const viy2Row_yMnie = ref();
const viy2Card_12bWCQ = ref();
const viy2Space_VTFXw = ref();
const viy2InputBox_VWuGY = ref();
const viy2InputBox_alMXNq = ref();
const viy2Space_9laN0O = ref();
const viy2InputBox_VWwBu = ref();
const viy2InputBox_alNLyU = ref();
const viy2InputBox_9lzyVU = ref();
const viy2Radio_VIc50 = ref();
const viy2Button_VIBgM = ref();
const viy2Button_VIA0g = ref();
const viy2Select_VGd0E = ref();
const viy2Card_12cfoT = ref();

const formData = reactive({
  datafieldviy2InputBox_VWuGY: '*****', datafieldviy2InputBox_VWuGY: '*****', datafieldviy2InputBox_VWwBu: '***', datafieldviy2InputBox_VWuGY: '*****', datafieldviy2InputBox_VX3z3: '**', datafieldviy2Radio_VIc50: '', datafieldviy2Select_VGd0E: '',
});

const viy2Radio_VIc50Opts = reactive([
  { value: '現行図のみ', label: '現行図のみ' },
  { value: '現行図＋旧廃図（2世代前まで）', label: '現行図＋旧廃図（2世代前まで）' },
]);

const viy2Select_VGd0EOpts = reactive([
  {
      				label:
      					'50件',
      				value:
      					'50件',
      			},
  {
      				label:
      					'100件',
      				value:
      					'100件',
      			},
  {
      				label:
      					'200件',
      				value:
      					'200件',
      			},
]);
</script>

<template>
  <VueForm ref="form" v-loading="lockScreen" :model="formData" :style="{ }">
    <VueRow

      id="viy2Row_yMnie"
      ref="viy2Row_yMnie"
    >
      <VueCol

        item-key="item"

        :md="{ span: 10 }"
      >
        <VueCard

          id="viy2Card_12bWCQ"
          ref="viy2Card_12bWCQ"
        >
          <VueText id="viy2Text_VPkzh" ref="viy2Text_VPkzh" size="large" :style="{ fontSize: '24px', fontWeight: 'bold', fontStyle: 'normal', display: 'inline-block' }">
            YMC-APOLO 検索条件入力
          </VueText>

          <VueText id="viy2Text_yMDoT" ref="viy2Text_yMDoT" :style="{ width: '100%', display: 'inline-block' }">
            生産図のみ対象です
          </VueText>

          <VueText id="viy2Text_yMG2D" ref="viy2Text_yMG2D" :style="{ width: '100%', display: 'inline-block', color: '#FF0000' }">
            図面は社外秘の情報です。扱いには十分注意して下さい。
          </VueText>

          <VueText id="viy2Text_VHIsH" ref="viy2Text_VHIsH" size="large" :style="{ width: '100%', display: 'inline-block' }">
            ・標準部品
          </VueText>

          <VueSpace

            id="viy2Space_VTFXw"
            ref="viy2Space_VTFXw"
          >
            <VueFormItem

              prop="datafieldviy2InputBox_VWuGY"

              size="small"
            >
              <VueInput

                id="viy2InputBox_VWuGY"

                ref="viy2InputBox_VWuGY"
                v-model="formData.datafieldviy2InputBox_VWuGY"

                size="small"

                :style="{ width: '100px' }"
              />
            </VueFormItem>

            <VueText id="viy2Text_aiHSgy" ref="viy2Text_aiHSgy" :style="{ width: '100%', display: 'inline-block', marginBottom: '20px' }">
              -
            </VueText>

            <VueFormItem

              prop="datafieldviy2InputBox_VWuGY"

              size="small"
            >
              <VueInput

                id="viy2InputBox_alMXNq"

                ref="viy2InputBox_alMXNq"
                v-model="formData.datafieldviy2InputBox_VWuGY"

                size="small"

                :style="{ width: '100px' }"
              />
            </VueFormItem>

            <VueText id="viy2Text_VTKb9" ref="viy2Text_VTKb9" size="small" :style="{ width: '100%', display: 'inline-block', textAlign: 'right', marginBottom: '20px' }">
              ・・・例) 9****-99999
            </VueText>
          </VueSpace>

          <VueText id="viy2Text_9g4nx8" ref="viy2Text_9g4nx8" size="large" :style="{ width: '100%', display: 'inline-block' }">
            ・普通部品
          </VueText>

          <VueSpace

            id="viy2Space_9laN0O"
            ref="viy2Space_9laN0O"
          >
            <VueFormItem

              prop="datafieldviy2InputBox_VWwBu"

              size="small"
            >
              <VueInput

                id="viy2InputBox_VWwBu"

                ref="viy2InputBox_VWwBu"
                v-model="formData.datafieldviy2InputBox_VWwBu"

                size="small"

                :style="{ width: '100px' }"
              />
            </VueFormItem>

            <VueText id="viy2Text_VX6IG" ref="viy2Text_VX6IG" :style="{ width: '100%', display: 'inline-block', marginBottom: '20px' }">
              -
            </VueText>

            <VueFormItem

              prop="datafieldviy2InputBox_VWuGY"

              size="small"
            >
              <VueInput

                id="viy2InputBox_alNLyU"

                ref="viy2InputBox_alNLyU"
                v-model="formData.datafieldviy2InputBox_VWuGY"

                size="small"

                :style="{ width: '100px' }"
              />
            </VueFormItem>

            <VueText id="viy2Text_9lzndM" ref="viy2Text_9lzndM" :style="{ width: '100%', display: 'inline-block', marginBottom: '20px' }">
              -
            </VueText>

            <VueFormItem

              prop="datafieldviy2InputBox_VX3z3"

              size="small"
            >
              <VueInput

                id="viy2InputBox_9lzyVU"

                ref="viy2InputBox_9lzyVU"
                v-model="formData.datafieldviy2InputBox_VX3z3"

                size="small"

                :style="{ width: '100px' }"
              />
            </VueFormItem>

            <VueText id="viy2Text_9laN1a" ref="viy2Text_9laN1a" size="small" :style="{ width: '100%', display: 'inline-block', textAlign: 'right', marginBottom: '20px' }">
              ・・・例) 123-AAAAA-**
            </VueText>
          </VueSpace>

          <VueText id="viy2Text_9g5LWI" ref="viy2Text_9g5LWI" size="large" :style="{ width: '100%', display: 'inline-block' }">
            ・図面終了状態
          </VueText>

          <VueFormItem

            prop="datafieldviy2Radio_VIc50"
          >
            <VueRadioGroup

              id="viy2Radio_VIc50"

              ref="viy2Radio_VIc50"
              v-model="formData.datafieldviy2Radio_VIc50"

              direction="horizontal"

              split-size="default"
            >
              <VueRadio
                v-for="option in viy2Radio_VIc50Opts"
                :key="option.value"
                :label="option.value"
              >
                {{ option.label }}
              </VueRadio>
            </VueRadioGroup>
          </VueFormItem>

          <VueButton id="viy2Button_VIBgM" ref="viy2Button_VIBgM" icon-position="left" color="#EAEAEA">
            SEARCH
          </VueButton>

          <VueButton id="viy2Button_VIA0g" ref="viy2Button_VIA0g" icon-position="left" color="#EAEAEA">
            RESET
          </VueButton>

          <VueFormItem

            label="1ページあたりの表示件数"

            prop="datafieldviy2Select_VGd0E"
          >
            <VueSelect
              id="viy2Select_VGd0E"

              ref="viy2Select_VGd0E"
              v-model="formData.datafieldviy2Select_VGd0E"

              :style="{ width: '20%' }"

              :options="viy2Select_VGd0EOpts"
            />
          </VueFormItem>
        </VueCard>
      </VueCol>

      <VueCol

        item-key="item"

        :md="{ span: 8 }"
      >
        <VueCard

          id="viy2Card_12cfoT"
          ref="viy2Card_12cfoT"
        >
          <VueText id="viy2Text_VGqFK" ref="viy2Text_VGqFK" size="small" :style="{ width: '100%', display: 'inline-block' }">
            ps00023
          </VueText>

          <VueText id="viy2Text_VGAGr" ref="viy2Text_VGAGr" size="large" :style="{ width: '100%', display: 'inline-block', fontWeight: 'bold', fontSize: '24px' }">
            お知らせ
          </VueText>
        </VueCard>
      </VueCol>
    </VueRow>
  </VueForm>
</template>
