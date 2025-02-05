<script setup>
import { IconCheck, IconClose, IconDelete, IconDownload, IconEdit, IconPlus, IconSearch, useLockScreen } from 'viy-ui';
import { useI18n } from 'vue-i18n';
import { get, merge } from 'lodash-es';
import { useApi } from '@/composables/useApi';

const { t } = useI18n();
const { lockScreen } = useLockScreen();

const updateFlag = ref(false);

const validateEmail = (rule, value, callback) => {
  if (value) {
    const emailRegExp = /^[a-zA-Z0-9_\-]+@[a-zA-Z0-9_\-]+(\.[a-zA-Z0-9_\-]+)+$/;
    if (!emailRegExp.test(value)) {
      callback(new Error(t('M.E.000002')));
    } else {
      callback();
    }
  } else {
    callback();
  }
};
const doUpdate = (row) => {
  detailVisible.value = true;
  updateFlag.value = true;
  // The first time you open the side, you need to initialize the form controls in the side
  // Otherwise, calling the resetFields method later to reset the value is incorrect
  nextTick(() => {
    detailForm.value && detailForm.value.resetFields();
    merge(detailFormData, row);
  });
};
const doDelete = (row) => {
  VueMessageBox.confirm(t('M.W.000001'), 'Warning', {
    confirmButtonText: 'OK',
    cancelButtonText: 'Cancel',
    type: 'warning',
  }).then(() => {
    deleteDsApi.runAsync({
      companyCd: row.companyCd,
      employeeCd: row.employeeCd,
    });
  });
};

defineOptions({
  name: 'employee01',
});

const form = ref();
const viy2Panel_KEd7N = ref();
const viy2Row_KG6RZ = ref();
const searchBtn = ref();
const conditionForm = ref();
const conditionRow = ref();
const joinDate = ref();
const employeeCd = ref();
const gender = ref();
const viy2Panel_KFRLT = ref();
const viy2Row_LSq40 = ref();
const addBtn = ref();
const downloadExcelBtn = ref();
const downloadPDFBtn = ref();
const viy2Table = ref();
const viy2TablePagination = ref();
const viy2Aside = ref();
const detailForm = ref();
const viy2Panel_MdFgd = ref();
const companyCd = ref();
const viy2InputBox_1gKHrE = ref();
const viy2InputBox_7zeCIo = ref();
const viy2DateTimePicker_XCKaH = ref();
const groupCd = ref();
const viy2Radio_L4DEv = ref();
const viy2InputBox_L4QZw = ref();
const viy2Row_7Xunbi = ref();
const saveBtn = ref();
const cancelBtn = ref();

const formData = reactive({
});

    	const conditionFormData = reactive({
      		joinDate: [], employeeCd: '', gender: '',
});
             	const detailFormData = reactive({
      		companyCd: '01', employeeCd: '', employeeNm: '', joinDate: '', groupCd: '', gender: '', mailAddress: '',
});

const rules = reactive({
  viy2InputBox_1gKHrERules: [
    {
      required: true,

      message: computed(() => {
        return t('M.E.000001');
      }),

    },

  ],
  groupCdRules: [
    {
      required: true,

      message: computed(() => {
        return t('M.E.000004');
      }),

    },

  ],
  viy2InputBox_L4QZwRules: [
    {
      validator: validateEmail,

      trigger: 'manual',

    },

  ],

});

const detailVisible = ref(false);

const genderOpts = reactive([
  { value: '', label: 'all' },
  { value: '0', label: 'male' },
  { value: '1', label: 'female' },
]);

const viy2TableEditConfig = reactive({

});

const viy2TableMouseConfig = reactive({

  extension: true,

});

const viy2TableCurrentPage = ref(1);
const viy2TablePageSize = ref(10);

const viy2TableOperateButtons = (scope) => {
  return [
    {
      label: '',
      size: 'small',
      type: 'text',

      icon: IconEdit,
      click: doUpdate,

    },
    {
      label: '',
      size: 'small',
      type: 'text',

      icon: IconDelete,
      click: doDelete,

    },
  ];
};

const genderDsApi = useApi({
  method: 'post',
  localData: [
    { value: '0', label: 'male' },
    { value: '1', label: 'female' },
  ],

});
const genderDs = genderDsApi.data;
const employeeListApi = useApi({
  url: '/employee/getEmployeeMstListPageable',
  method: 'post',
  data: () => {
    conditionFormData.pageSize = viy2TablePageSize.value;
    conditionFormData.currentPage = viy2TableCurrentPage.value;
    return conditionFormData;
  },

}, {
  onSuccess: (data, params) => {
    showSuccessMessage(t('M.E.000005', [data.totalElements]));
  },

  initialData: {
    content: [],
  },
  manual: true,
});
const employeeList = employeeListApi.data;
const updateDsApi = useApi({
  url: '/employee/updateEmployeeMst',
  method: 'post',
  data: () => {
    return detailFormData;
  },

}, {
  onSuccess: (data, params) => {
    VueNotification({
      title: 'Success',
      message: 'Save Success',
      type: 'success',
    });
    detailVisible.value = false;
    employeeListApi.runAsync();
  },
  manual: true,
});
const updateDs = updateDsApi.data;
const downloadDsApi = useApi({
  url: '/employee/downloadExcel',
  method: 'post',
  data: () => {
    return conditionFormData;
  },
  responseType: 'blob',

}, {
  onSuccess: (data, params) => {
    const fileName = 'EmployeeMst.xlsx';

    // download
    VueUtil.saveAs(data, fileName);
  },
  manual: true,
});
const downloadDs = downloadDsApi.data;
const deleteDsApi = useApi({
  url: '/employee/deleteEmployeeMst',
  method: 'post',

}, {
  onSuccess: (data, params) => {
    VueNotification({
      title: 'Success',
      message: 'Delete Success',
      type: 'success',
    });
    employeeListApi.runAsync();
  },
  manual: true,
});
const deleteDs = deleteDsApi.data;
const groupDsApi = useApi({
  url: '/employee/groupMstFile',
  method: 'post',
  data: {},

});
const groupDs = groupDsApi.data;
const downloadpdfDSApi = useApi({
  url: '/employee/downloadpdf',
  method: 'post',
  data: () => {
    return conditionFormData;
  },
  responseType: 'blob',

}, {
  onSuccess: (data, params) => {
    const fileName = 'EmployeeMst.pdf';

    // download
    VueUtil.saveAs(data, fileName);
  },
  manual: true,
});
const downloadpdfDS = downloadpdfDSApi.data;
const saveDsApi = useApi({
  url: '/employee/insertEmployeeMst',
  method: 'post',
  data: () => {
    return detailFormData;
  },

}, {
  onSuccess: (data, params) => {
    VueNotification({
      title: 'Success',
      message: 'Save Success',
      type: 'success',
    });
    detailVisible.value = false;
    employeeListApi.runAsync();
  },
  manual: true,
});
const saveDs = saveDsApi.data;

const searchBtnClick = () => {
  if (!conditionForm.value) {
    return;
  }

  // Call query API(Writing method:DatasetID + Api.runAsync)
  employeeListApi.runAsync();
};

const addBtnClick = () => {
  detailForm.value && detailForm.value.resetFields();
  updateFlag.value = false;
  detailVisible.value = true;
};
const downloadExcelBtnClick = () => {
  if (employeeList.value.content.length > 0) {
    downloadDsApi.runAsync();
  } else {
    VueNotification({
      title: 'Error',
      message: t('M.E.000003'),
      position: 'top-right',
      type: 'error',
    });
  }
};
const downloadPDFBtnClick = () => {
  if (employeeList.value.content.length > 0) {
    downloadpdfDSApi.runAsync();
  } else {
    VueNotification({
      title: 'Error',
      message: t('M.E.000003'),
      position: 'top-right',
      type: 'error',
    });
  }
};
const viy2TablePageCurrentChange // When flipping pages, retrieve data based on page and size
= () => {
  if (!conditionForm.value) {
    return;
  }
  if (employeeList.value.length === 0) {
    return;
  }
  employeeListApi.runAsync();
};
const viy2TablePageSizeChange // When flipping pages, retrieve data based on page and size
= () => {
  if (!conditionForm.value) {
    return;
  }
  if (employeeList.value.length === 0) {
    return;
  }
  employeeListApi.runAsync();
};

const viy2TableEmployeeCdEditRender = computed(() => {
  return {
    enabled: false,
    attrs: {

      textAlign: 'center',

    },
  };
});

const viy2TableEmployeeNmEditRender = computed(() => {
  return {
    enabled: false,
    attrs: {

      textAlign: 'center',

    },
  };
});

const viy2TableGroupNmEditRender = computed(() => {
  return {
    enabled: false,
    attrs: {

      textAlign: 'left',

    },
  };
});

const viy2TableJoinDateEditRender = computed(() => {
  return {
    enabled: false,
    attrs: {

      textAlign: 'center',
      type: 'dates',

    },
  };
});
const viy2TableGenderFormatter = function (row, columnConfig, cellValue) {
  if (row.cellValue === '0') {
    return row.cellValue = 'male';
  }
  if (row.cellValue === '1') {
    return row.cellValue = 'female';
  }
};

const viy2TableGenderEditRender = computed(() => {
  return {
    enabled: false,
    attrs: {

      textAlign: 'center',

    },
  };
});

const viy2TableMailAddressEditRender = computed(() => {
  return {
    enabled: false,
    attrs: {

      textAlign: 'left',

    },
  };
});

const saveBtnClick = () => {
  if (!form) {
    return;
  }
  detailForm.value.validate((valid) => {
    if (valid) {
      if (updateFlag.value) {
        updateDsApi.runAsync();
      } else {
        saveDsApi.runAsync();
      }
    }
  });
};
const cancelBtnClick = () => {
  form.value.resetFields();
  detailVisible.value = false;
};
</script>

<template>
  <VueForm ref="form" v-loading="lockScreen" :model="formData" :style="{ }">
    <VuePanel id="viy2Panel_KEd7N" ref="viy2Panel_KEd7N" :title="t('conditionArea')">
      <template #header>
        <div style="width: 300px">
          <VueRow

            id="viy2Row_KG6RZ"
            ref="viy2Row_KG6RZ"
          >
            <VueCol

              item-key="item"

              align="right"

              :inline="true"

              :md="{ span: 24 }"
            >
              <VueButton id="searchBtn" ref="searchBtn" icon-position="left" type="primary" :icon="IconSearch" @click="searchBtnClick">
                {{ t('search') }}
              </VueButton>
            </VueCol>
          </VueRow>
        </div>
      </template>

      <VueForm

        id="conditionForm"
        ref="conditionForm"

        :model="conditionFormData"
      >
        <VueRow

          id="conditionRow"
          ref="conditionRow"
        >
          <VueCol

            item-key="item"

            :md="{ span: 8 }"
          >
            <VueFormItem

              :label="t('joinDate')"

              label-width="100px"

              prop="joinDate"
            >
              <VueDatePicker

                id="joinDate"

                ref="joinDate"
                v-model="conditionFormData.joinDate"

                type="daterange"

                value-format="YYYYMMDD"
              />
            </VueFormItem>
          </VueCol>

          <VueCol

            item-key="item"

            :md="{ span: 8 }"
          >
            <VueFormItem

              :label="t('employeeCd')"

              label-width="110px"

              prop="employeeCd"
            >
              <VueInput

                id="employeeCd"

                ref="employeeCd"
                v-model="conditionFormData.employeeCd"

                :clearable="true"
              />
            </VueFormItem>
          </VueCol>

          <VueCol

            item-key="item"

            :md="{ span: 8 }"
          >
            <VueFormItem

              :label="t('gender')"

              label-width="100px"

              prop="gender"
            >
              <VueRadioGroup

                id="gender"

                ref="gender"
                v-model="conditionFormData.gender"

                direction="horizontal"

                split-size="default"
              >
                <VueRadio
                  v-for="option in genderOpts"
                  :key="option.value"
                  :label="option.value"
                >
                  {{ option.label }}
                </VueRadio>
              </VueRadioGroup>
            </VueFormItem>
          </VueCol>
        </VueRow>
      </VueForm>
    </VuePanel>

    <VuePanel id="viy2Panel_KFRLT" ref="viy2Panel_KFRLT" :title="t('detailsArea')">
      <template #header>
        <div style="width: 400px">
          <VueRow

            id="viy2Row_LSq40"
            ref="viy2Row_LSq40"
          >
            <VueCol

              item-key="item"

              align="right"

              :inline="true"

              :md="{ span: 24 }"
            >
              <VueButton id="addBtn" ref="addBtn" icon-position="left" type="success" :icon="IconPlus" @click="addBtnClick">
                {{ t('add') }}
              </VueButton>

              <VueButton id="downloadExcelBtn" ref="downloadExcelBtn" icon-position="left" type="primary" :icon="IconDownload" @click="downloadExcelBtnClick">
                {{ t('downloadExcel') }}
              </VueButton>

              <VueButton id="downloadPDFBtn" ref="downloadPDFBtn" icon-position="left" type="primary" :icon="IconDownload" @click="downloadPDFBtnClick">
                {{ t('downloadPDF') }}
              </VueButton>
            </VueCol>
          </VueRow>
        </div>
      </template>

      <VueTable

        id="viy2Table"

        ref="viy2Table"
        height="550px"

        :data="employeeList.content"

        :edit-config="viy2TableEditConfig"
        :mouse-config="viy2TableMouseConfig"
      >
        <VueInputColumn

          :edit-render="viy2TableEmployeeCdEditRender"

          field="employeeCd"

          align="center"

          :sortable="true"

          width="200px"

          :title="t('employeeCd')"

          header-align="center"
        />
        <VueInputColumn

          :edit-render="viy2TableEmployeeNmEditRender"

          field="employeeNm"

          align="center"

          width="200px"

          :title="t('employeeNm')"

          header-align="center"
        />
        <VueInputColumn

          :edit-render="viy2TableGroupNmEditRender"

          field="groupNm"

          align="left"

          width="200px"

          :title="t('groupNm')"

          header-align="center"
        />
        <VueDateTimeColumn

          :edit-render="viy2TableJoinDateEditRender"

          field="joinDate"

          align="center"

          width="200px"

          :title="t('joinDate')"

          header-align="center"
        />
        <VueInputColumn

          :formatter="viy2TableGenderFormatter"

          :edit-render="viy2TableGenderEditRender"

          field="gender"

          align="center"

          width="200px"

          :title="t('gender')"

          header-align="center"
        />
        <VueInputColumn

          :edit-render="viy2TableMailAddressEditRender"

          field="mailAddress"

          align="left"

          width="200px"

          :title="t('mailAddress')"

          header-align="center"
        />

        <VueButtonColumn

          align="center"

          :title="t('operate')"

          header-align="center"

          width="130px"

          :buttons="viy2TableOperateButtons"
        />
      </VueTable>
      <VuePagination
        ref="viy2TablePagination"

        v-model:current-page="viy2TableCurrentPage"
        v-model:page-size="viy2TablePageSize"
        layout="total, sizes, prev, pager, next, jumper"

        :total="get(employeeList, 'totalElements')"

        @current-change="viy2TablePageCurrentChange"
        @size-change="viy2TablePageSizeChange"
      />
    </VuePanel>

    <VueAside
      id="viy2Aside"

      ref="viy2Aside"

      v-model="detailVisible"
      :show-close="true"
    >
      <VueForm

        id="detailForm"
        ref="detailForm"

        :model="detailFormData"
      >
        <VuePanel id="viy2Panel_MdFgd" ref="viy2Panel_MdFgd" :title="t('detail')">
          <VueFormItem

            v-show="false"

            :label="t('companyCd')"

            label-width="104px"

            prop="companyCd"
          >
            <VueInput

              id="companyCd"
              ref="companyCd"

              v-model="detailFormData.companyCd"
            />
          </VueFormItem>

          <VueFormItem

            :label="t('employeeCd')"

            label-width="104px"

            prop="employeeCd"

            :rules="rules.viy2InputBox_1gKHrERules"
          >
            <VueInput

              id="viy2InputBox_1gKHrE"

              ref="viy2InputBox_1gKHrE"

              v-model="detailFormData.employeeCd"

              :clearable="true"
              :maxlength="7"

              :disabled="updateFlag"
            />
          </VueFormItem>

          <VueFormItem

            :label="t('employeeNm')"

            label-width="106px"

            prop="employeeNm"
          >
            <VueInput

              id="viy2InputBox_7zeCIo"

              ref="viy2InputBox_7zeCIo"

              v-model="detailFormData.employeeNm"
              :clearable="true"

              :maxlength="20"
            />
          </VueFormItem>

          <VueFormItem

            :label="t('joinDate')"

            label-width="104px"

            prop="joinDate"
          >
            <VueDatePicker

              id="viy2DateTimePicker_XCKaH"

              ref="viy2DateTimePicker_XCKaH"
              v-model="detailFormData.joinDate"

              type="date"
            />
          </VueFormItem>

          <VueFormItem

            :label="t('groupCd')"

            label-width="104px"

            prop="groupCd"

            :rules="rules.groupCdRules"
          >
            <VueSelect

              id="groupCd"

              ref="groupCd"
              v-model="detailFormData.groupCd"

              :clearable="true"

              :options="groupDs"

              :props="{
                label: 'groupNm',
                value: 'groupCd',

              }"
            />
          </VueFormItem>

          <VueFormItem

            :label="t('gender')"

            label-width="104px"

            prop="gender"
          >
            <VueRadioGroup

              id="viy2Radio_L4DEv"

              ref="viy2Radio_L4DEv"
              v-model="detailFormData.gender"

              direction="horizontal"

              split-size="default"
            >
              <VueRadio
                v-for="option in genderDs"
                :key="option.value"
                :label="option.value"
                :name="option.name"
                :disabled="option.disabled"
              >
                {{ option.label }}
              </VueRadio>
            </VueRadioGroup>
          </VueFormItem>

          <VueFormItem

            :label="t('mailAddress')"

            label-width="104px"

            prop="mailAddress"

            :rules="rules.viy2InputBox_L4QZwRules"
          >
            <VueInput

              id="viy2InputBox_L4QZw"

              ref="viy2InputBox_L4QZw"
              v-model="detailFormData.mailAddress"

              :maxlength="40"
            />
          </VueFormItem>

          <VueRow

            id="viy2Row_7Xunbi"
            ref="viy2Row_7Xunbi"
          >
            <VueCol

              item-key="item"

              align="center"

              :inline="true"

              :md="{ span: 24 }"
            >
              <VueButton id="saveBtn" ref="saveBtn" icon-position="left" type="success" :icon="IconCheck" @click="saveBtnClick">
                {{ t('save') }}
              </VueButton>

              <VueButton id="cancelBtn" ref="cancelBtn" icon-position="left" type="warning" :icon="IconClose" @click="cancelBtnClick">
                {{ t('cancel') }}
              </VueButton>
            </VueCol>
          </VueRow>
        </VuePanel>
      </VueForm>
    </VueAside>
  </VueForm>
</template>
