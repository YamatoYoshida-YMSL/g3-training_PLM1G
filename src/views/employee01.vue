


<script setup>
import { useLockScreen, IconSearch, IconPlus, IconDownload, IconUpload, IconDelete, IconCheck, IconClose, } from 'viy-ui';
import { useI18n } from 'vue-i18n';
import { useApi } from '@/composables/useApi';

    import { get } from 'lodash-es';

const { t } = useI18n();
const { lockScreen } = useLockScreen();

const doUpdate = (row) => {
  detailVisible.value = true;
  updateFlag.value = true;
  //The first time you open the side, you need to initialize the form controls in the side
  //Otherwise, calling the resetFields method later to reset the value is incorrect
  nextTick(() => {
    detailForm.value && detailForm.value.resetFields();
    merge(detailFormData, row);
  })
}
const doDelete = (row) => {
  VueMessageBox.confirm(t('M.W.000001'), 'Warning', {
    confirmButtonText: 'OK',
    cancelButtonText: 'Cancel',
    type: 'warning',
  }).then(() => {
    deleteDsApi.runAsync({
      companyCd: row.companyCd,
      employeeCd: row.employeeCd
    });
  })
        
defineOptions({
  name: 'employee01',
});
    
const form = ref();
const conditionArea = ref();
const viy2Button_HRUAX = ref();
const conditionForm = ref();
const viy2Row_Ha4HQ = ref();
const joinDate = ref();
const employeeCd = ref();
const gender = ref();
const detailedList = ref();
const viy2Button_HRWV9 = ref();
const viy2Button_74HSsU = ref();
const viy2Button_74HB0k = ref();
const viy2Table_Hvba2 = ref();
const viy2Table_Hvba2Pagination = ref();
const viy2Aside = ref();
const detailForm = ref();
const detail = ref();
const viy2Row_IETqp = ref();
const companyCd = ref();
const viy2Row_7cFC2O = ref();
const detailEmployeeCd = ref();
const viy2Row_7cFAxA = ref();
const detailEmployeeNm = ref();
const viy2Row_7cFz6I = ref();
const detailJoinDate = ref();
const viy2Row_7cFxwu = ref();
const groupCd = ref();
const viy2Row_7cFvXI = ref();
const detailGender = ref();
const viy2Row_7cEufe = ref();
const email = ref();
const viy2Row_7dfh6W = ref();
const save = ref();
const cancel = ref();


const formData = reactive({
});
    
  	const conditionFormData = reactive({
      		joinDate: '' ,  employeeCd: '' ,  gender: '' 
    });
           	const detailFormData = reactive({
      		datafieldviy2InputBox_IFaWa: '' ,  datafieldviy2InputBox_IFaWa: '' ,  datafieldviy2InputBox_IFaWa: '' ,  datafieldviy2DateTimePicker_II595: '' ,  datafieldviy2Select_IIkUm: '' ,  datafieldviy2Radio_IIxiA: '' ,  datafieldviy2InputBox_IFaWa: '' 
    });

    
const rules = reactive({
  detailEmployeeCdRules: [
          {
                  required:true

,                  message: computed(() => { return t('validation.error.required'); })

          }
          
        ]
        
});
    

    
    const detailvisible = ref(false);
    

            
 


  
    

            

	

	

   













            

	

	

   

      












            

	

	

   













            














            
 



 
    const groupCdOpts = reactive([
                {
      				label:
      					'Option 1'
,
      				value:
      					'Option 1'
      			},
                {
      				label:
      					'Option 2'
,
      				value:
      					'Option 2'
      			},
                {
      				label:
      					'Option 3'
,
      				value:
      					'Option 3'
      			},
    ]);












                




 const detailGenderOpts = reactive([
                {
value: "Option 1" ,label: "Option 1"      			},
                {
value: "Option 2" ,label: "Option 2"      			},
                {
value: "Option 3" ,label: "Option 3"      			}
    ])











            

	

	

   













            



  




    



  
























    








    
 


  
        



  






                









        

	

	

   








            




 const genderOpts = reactive([
                {
value: "all" ,label: "all"      			},
                {
value: "male" ,label: "male"      			},
                {
value: "female" ,label: "female"      			}
    ])




















 


  
        



  




    



  




    



  






    


  




const viy2Table_Hvba2EditConfig = reactive({
     trigger: 'click'

     
     
     
});





  
  

const viy2Table_Hvba2MouseConfig = reactive({
    
    
    extension: true

});
  
  



  
  


const viy2Table_Hvba2CurrentPage = ref(1);
const viy2Table_Hvba2PageSize = ref(10);





  
    

    

    




 





    




 





    




 





    




 





    




 





    




 





    


const viy2Table_Hvba2OperateButtons = (scope) => {

      return [ 
          {
              label:'update'
              ,size: 'small' 
              ,type: 'text' 
               
              ,icon:  IconUpload
              ,click: doUpdate
               
               
              
               
               
          },
          {
              label:'delete'
              ,size: 'small' 
              ,type: 'text' 
               
              ,icon:  IconDelete
              ,click: doDelete
               
               
              
               
               
          }
      ];
};
  

    





    
    const downloadsDsApi = useApi({
        method: 'post',
        data: ()=>{
 return conditionFormData;
 },
        responseType: 'blob',                            
                    
    }, {
        onSuccess: (data, params) => {
  const fileName = 'EmployeeMst.xlsx';
    // download
  VueUtil.saveAs(data,fileName);
},
    });
    const downloadsDs = downloadsDsApi.data;
    const downloadDsApi = useApi({
        method: 'post',
        data: ()=>{
 return conditionFormData;
 },
        responseType: 'blob',                            
                    
    }, {
        onSuccess: (data, params) => {
  const fileName = 'EmployeeMst.xlsx';
    // download
  VueUtil.saveAs(data,fileName);
},
    });
    const downloadDs = downloadDsApi.data;
    const employeeListApi = useApi({
        url: '/employee/getEmployeeMstList',
        method: 'post',
        data: ()=>{
    conditionFormData.pageSize=viy2TablePageSize.value;
    conditionFormData.currentPage=viy2TableCurrentPage.value;
    return conditionFormData;
},
                    
    }, {
        manual: true,
    });
    const employeeList = employeeListApi.data;
    const downloadpdfDSApi = useApi({
        method: 'post',
        responseType: 'blob',                            
                    
    }, {
        onSuccess: (data, params) => {

  const fileName = 'EmployeeMst.pdf';

  // download
  VueUtil.saveAs(data, fileName);
},
    });
    const downloadpdfDS = downloadpdfDSApi.data;


const viy2Button_HRUAXClick = () => {
    if (!conditionForm.value) {
        return;
    }
    // Call query API(Writing method:DatasetId +Api.runAsync)
     employeeListApi.runAsync();
};
    
        const viy2Button_HRWV9Click = () => {
      detailForm.value && detailForm.value.resetFields();
      updateFlag.value = false;
      detailVisible.value = true;
};
          const viy2Button_74HSsUClick = () => {
  if (employeeList.value.content.length > 0) {
    downloadDsApi.runAsync();
  } else {
    VueNotification({
      title: 'Error',
      message: t('M.E.000003'),
      position: "top-right",
      type: 'error',
    });
  }
};
          const viy2Button_74HB0kClick = () => {
  if (employeeList.value.content.length > 0 ) {
    downloadpdfDSApi.runAsync();
  } else {
    VueNotification({
      title: 'Error',
      message: t('M.E.000003'),
      position: "top-right",
      type: 'error',
    });
  }
};
          const viy2Table_Hvba2PageCurrentChange = // When flipping pages, retrieve data based on page and size
() => {
    if (!conditionForm.value) {
        return;
    }
    if(employeeList.value.length === 0){
        return;
    }
     employeeListApi.runAsync();                          
};
        const viy2Table_Hvba2PageSizeChange = // When flipping pages, retrieve data based on page and size
() => {
    if (!conditionForm.value) {
        return;
    }
    if(employeeList.value.length === 0){
        return;
    }
     employeeListApi.runAsync();                          
};
  

const viy2Table_Hvba2EmployeeCdEditRender = computed(() => {
  return {
    enabled: false,
    attrs: {
      
      
      textAlign: 'left', 
      
      
      
      
      
      
      
      
    },
  };                
});

const viy2Table_Hvba2EmployeeNmEditRender = computed(() => {
  return {
    enabled: false,
    attrs: {
      
      
      textAlign: 'left', 
      
      
      
      
      
      
      
      
    },
  };                
});

const viy2Table_Hvba2GroupNmEditRender = computed(() => {
  return {
    enabled: false,
    attrs: {
      
      
      textAlign: 'left', 
      
      
      
      
      
      
      
      
    },
  };                
});

const viy2Table_Hvba2JoinDateEditRender = computed(() => {
  return {
    enabled: false,
    attrs: {
      
      
      textAlign: 'left', 
      
      
      
      
      
      
      
      
    },
  };                
});

const viy2Table_Hvba2GenderEditRender = computed(() => {
  return {
    enabled: false,
    attrs: {
      
      
      textAlign: 'left', 
      
      
      
      
      
      
      
      
    },
  };                
});

const viy2Table_Hvba2EmailEditRender = computed(() => {
  return {
    enabled: false,
    attrs: {
      
      
      textAlign: 'left', 
      
      
      
      
      
      
      
      
    },
  };                
});
  
  
  
  
        const saveClick = () => {
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
    })
};
          const cancelClick = ()=>{
    detailForm.value.resetFields();
    detailVisible.value=false;  
};




</script>
        
<template>
<VueForm ref="form" :model="formData" v-loading="lockScreen" :style="{ }" >    
		<VuePanel :title="t('Condition Area')" title-align="left" collapse-icon-position="left" id="conditionArea" ref="conditionArea" >		<template #header>
            <div  style="width: 100px" >
                    <VueButton color="#39B0F9" icon-position="left" id="viy2Button_HRUAX" ref="viy2Button_HRUAX" @click="viy2Button_HRUAXClick" :icon="IconSearch" >
        Search
</VueButton>



            </div>
        </template>
            
            <VueForm 


                   

                   

                   

                   
              id="conditionForm"
			  ref="conditionForm"
                                       
    
    

 :model="conditionFormData" >
	<VueRow 


                   

                   

                   

                   
              id="viy2Row_Ha4HQ"
			  ref="viy2Row_Ha4HQ"
                                       
    
    

 >
          <VueCol 

item-key="item"
                   

                   

                   

                   

                   
                                       
    
    

 
	:md="{span:8}"  
>
        
    <VueFormItem 


  :label="t('JoinDate')"



    prop="joinDate"

                             

                                 


  
>
    <VueDatePicker 


                   

                   

                   

                   
              id="joinDate"
			  ref="joinDate"
                                       
    
	 		v-model="conditionFormData.joinDate"
    

        
            
            
    />
    </VueFormItem>


</VueCol>

          <VueCol 

item-key="item"
                   

                   

                   

                   

                   
                                       
    
    

 
	:md="{span:8}"  
>
        

    <VueFormItem 


  :label="t('EmployeeCd')"



    prop="employeeCd"

                             

                                 


  
>
    <VueInput 


                   

                   

                   

                   
              id="employeeCd"
			  ref="employeeCd"
                                       
    
	 		v-model="conditionFormData.employeeCd"
    

              
              
              
              
                  
            
              

    >


    </VueInput>
    </VueFormItem>


</VueCol>

          <VueCol 

item-key="item"
                   

                   

                   

                   

                   
                                       
    
    

 
	:md="{span:8}"  
>
        
    <VueFormItem 


  :label="t('Gender')"



    prop="gender"

                             

                                 


  
>
    <VueRadioGroup 


                   

                   

                   

                   
direction="horizontal"
                   

                   

                   
              id="gender"
			  ref="gender"
                                       
    
	 		v-model="conditionFormData.gender"
    

			  split-size="default"
        >
          
               <VueRadio
	   			v-for = "option in genderOpts"
                   :key="option.value"
               	:label="option.value"
                  	
                
                
               >
                       {{option.label}}
               </VueRadio>

    </VueRadioGroup>
    </VueFormItem>


</VueCol>

</VueRow>

</VueForm>

</VuePanel>

<VuePanel :title="t('Detailed List')" id="detailedList" ref="detailedList" >		<template #header>
            <div  style="width: 300px" >
                    <VueButton icon-position="left" color="#29BF00" id="viy2Button_HRWV9" ref="viy2Button_HRWV9" @click="viy2Button_HRWV9Click" :icon="IconPlus" >
        Add
</VueButton>

    <VueButton icon-position="left" color="#39B0F9" id="viy2Button_74HSsU" ref="viy2Button_74HSsU" @click="viy2Button_74HSsUClick" :icon="IconDownload" >
        Excel
</VueButton>

    <VueButton icon-position="left" color="#39B0F9" id="viy2Button_74HB0k" ref="viy2Button_74HB0k" @click="viy2Button_74HB0kClick" :icon="IconDownload" >
        PDF
</VueButton>



            </div>
        </template>
            
            

            
<VueTable  



                   

                   

                   

                   

                   
              id="viy2Table_Hvba2"
			  ref="viy2Table_Hvba2"
                                       
    
    
        
      
      

  	   :data="employeeList.content"
        
       :edit-config="viy2Table_Hvba2EditConfig"
       :mouse-config="viy2Table_Hvba2MouseConfig"
> 
    
<VueInputColumn    



:edit-render="viy2Table_Hvba2EmployeeCdEditRender"



field="employeeCd"
                   
align="left"
                   

                   

                   
width="200px"
                   
:title="t('Employee Cd')"
                   
header-align="center"
                   
                                       
    
    

     
>

        
</VueInputColumn>
<VueInputColumn    



:edit-render="viy2Table_Hvba2EmployeeNmEditRender"



field="employeeNm"
                   
align="left"
                   

                   

                   
width="200px"
                   
:title="t('Employee Nm')"
                   
header-align="center"
                   
                                       
    
    

     
>

        
</VueInputColumn>
<VueInputColumn    



:edit-render="viy2Table_Hvba2GroupNmEditRender"



field="groupNm"
                   
align="left"
                   

                   

                   
width="200px"
                   
:title="t('Group Nm')"
                   
header-align="center"
                   
                                       
    
    

     
>

        
</VueInputColumn>
<VueInputColumn    



:edit-render="viy2Table_Hvba2JoinDateEditRender"



field="joinDate"
                   
align="left"
                   

                   

                   
width="200px"
                   
:title="t('JoinDate')"
                   
header-align="center"
                   
                                       
    
    

     
>

        
</VueInputColumn>
<VueInputColumn    



:edit-render="viy2Table_Hvba2GenderEditRender"



field="gender"
                   
align="left"
                   

                   

                   
width="200px"
                   
:title="t('Gender')"
                   
header-align="center"
                   
                                       
    
    

     
>

        
</VueInputColumn>
<VueInputColumn    



:edit-render="viy2Table_Hvba2EmailEditRender"



field="email"
                   
align="left"
                   

                   

                   
width="200px"
                   
:title="t('Email')"
                   
header-align="center"
                   
                                       
    
    

     
>

        
</VueInputColumn>

  <VueButtonColumn


align="center"
                   

                   

                   
width="200px"
                   
header-align="center"
                   
:title="t('operate')"
                   

                   
                                       
    
    

           :buttons="viy2Table_Hvba2OperateButtons"
  />


</VueTable>
    <VuePagination
      ref="viy2Table_Hvba2Pagination"
      
      layout="total,sizes,prev,pager,next,"
      v-model:current-page="viy2Table_Hvba2CurrentPage"
    	v-model:page-size="viy2Table_Hvba2PageSize"
      
        :total="get(employeeList,'totalElemants')"


      
            @current-change="viy2Table_Hvba2PageCurrentChange"
            @size-change="viy2Table_Hvba2PageSizeChange"
     />


</VuePanel>

<VueAside v-model="detailvisible" 


                   
:modal="true"
                   
              id="viy2Aside"
			  ref="viy2Aside"
                                       
    
    

 >



            <VueForm 


                   

                   

                   

                   
              id="detailForm"
			  ref="detailForm"
                                       
    
    

 :model="detailFormData" >
	<VuePanel :title="t('Detail')" title-align="left" :collapse="true" id="detail" ref="detail" >            
            <VueRow 


                   

                   

                   

                   
              id="viy2Row_IETqp"
			  ref="viy2Row_IETqp"
                                       
    
    

 >
          <VueCol 

item-key="item"
                   

                   

                   

                   

                   
                                       
    
    

 
	:md="{span:24}"  
>
        

    <VueFormItem 


  :label="t('Company Cd')"



    prop="datafieldviy2InputBox_IFaWa"

                             

                                 


  
>
    <VueInput 


                   

                   

                   

                   
              id="companyCd"
			  ref="companyCd"
                                       
    
	 		v-model="detailFormData.datafieldviy2InputBox_IFaWa"
    

              
              
              
              
                  
            
              

    >


    </VueInput>
    </VueFormItem>


</VueCol>

</VueRow>

            <VueRow 


                   

                   

                   

                   
              id="viy2Row_7cFC2O"
			  ref="viy2Row_7cFC2O"
                                       
    
    

 >
          <VueCol 

item-key="item"
                   

                   

                   

                   

                   
                                       
    
    

 
	:md="{span:24}"  
>
        

    <VueFormItem 


  :label="t('Employee Cd')"



    prop="datafieldviy2InputBox_IFaWa"

  :rules="rules.detailEmployeeCdRules"
                             

                                 


  
>
    <VueInput 


                   

                   

                   

                   

                   
              id="detailEmployeeCd"
			  ref="detailEmployeeCd"
                                       
    
	 		v-model="detailFormData.datafieldviy2InputBox_IFaWa"
    

              
              
              
              
                  
            
              

    >


    </VueInput>
    </VueFormItem>


</VueCol>

</VueRow>

            <VueRow 


                   

                   

                   

                   
              id="viy2Row_7cFAxA"
			  ref="viy2Row_7cFAxA"
                                       
    
    

 >
          <VueCol 

item-key="item"
                   

                   

                   

                   

                   
                                       
    
    

 
	:md="{span:24}"  
>
        

    <VueFormItem 


  :label="t('Employee Nm')"



    prop="datafieldviy2InputBox_IFaWa"

                             

                                 


  
>
    <VueInput 


                   

                   

                   

                   
              id="detailEmployeeNm"
			  ref="detailEmployeeNm"
                                       
    
	 		v-model="detailFormData.datafieldviy2InputBox_IFaWa"
    

              
              
              
              
                  
            
              

    >


    </VueInput>
    </VueFormItem>


</VueCol>

</VueRow>

            <VueRow 


                   

                   

                   

                   
              id="viy2Row_7cFz6I"
			  ref="viy2Row_7cFz6I"
                                       
    
    

 >
          <VueCol 

item-key="item"
                   

                   

                   

                   

                   
                                       
    
    

 
	:md="{span:24}"  
>
        
    <VueFormItem 


  :label="t('JoinDate')"



    prop="datafieldviy2DateTimePicker_II595"

                             

                                 


  
>
    <VueDatePicker 


                   

                   

                   

                   
              id="detailJoinDate"
			  ref="detailJoinDate"
                                       
    
	 		v-model="detailFormData.datafieldviy2DateTimePicker_II595"
    

        
            
            
    />
    </VueFormItem>


</VueCol>

</VueRow>

            <VueRow 


                   

                   

                   

                   
              id="viy2Row_7cFxwu"
			  ref="viy2Row_7cFxwu"
                                       
    
    

 >
          <VueCol 

item-key="item"
                   

                   

                   

                   

                   
                                       
    
    

 
	:md="{span:24}"  
>
        
    <VueFormItem 


  :label="t('GroupCd')"



    prop="datafieldviy2Select_IIkUm"

                             

                                 


  
>
    <VueSelect


                   

                   

                   

                   

                   

                   
              id="groupCd"
			  ref="groupCd"
                                       
    
	 		v-model="detailFormData.datafieldviy2Select_IIkUm"
    

            :options="groupCdOpts"

          
          
          
    >
            
            
    </VueSelect>
    </VueFormItem>


</VueCol>

</VueRow>

            <VueRow 


                   

                   

                   

                   
              id="viy2Row_7cFvXI"
			  ref="viy2Row_7cFvXI"
                                       
    
    

 >
          <VueCol 

item-key="item"
                   

                   

                   

                   

                   
                                       
    
    

 
	:md="{span:24}"  
>
        
    <VueFormItem 


  :label="t('Gender')"



    prop="datafieldviy2Radio_IIxiA"

                             

                                 


  
>
    <VueRadioGroup 


                   

                   

                   

                   
direction="horizontal"
                   

                   

                   
              id="detailGender"
			  ref="detailGender"
                                       
    
	 		v-model="detailFormData.datafieldviy2Radio_IIxiA"
    

			  split-size="default"
        >
          
               <VueRadio
	   			v-for = "option in detailGenderOpts"
                   :key="option.value"
               	:label="option.value"
                  	
                
                
               >
                       {{option.label}}
               </VueRadio>

    </VueRadioGroup>
    </VueFormItem>


</VueCol>

</VueRow>

            <VueRow 


                   

                   

                   

                   
              id="viy2Row_7cEufe"
			  ref="viy2Row_7cEufe"
                                       
    
    

 >
          <VueCol 

item-key="item"
                   

                   

                   

                   

                   
                                       
    
    

 
	:md="{span:24}"  
>
        

    <VueFormItem 


  :label="t('Email')"



    prop="datafieldviy2InputBox_IFaWa"

                             

                                 


  
>
    <VueInput 


                   

                   

                   

                   
              id="email"
			  ref="email"
                                       
    
	 		v-model="detailFormData.datafieldviy2InputBox_IFaWa"
    

              
              
              
              
                  
            
              

    >


    </VueInput>
    </VueFormItem>


</VueCol>

</VueRow>

            <VueRow 


                   

                   

                   

                   
              id="viy2Row_7dfh6W"
			  ref="viy2Row_7dfh6W"
                                       
    
    

 >
          <VueCol 

item-key="item"
                   

                   

                   

                   

                   
                                       
    
    

 
	:md="{span:24}"  
>
        <VueButton icon-position="left" color="#29BF00" id="save" ref="save" @click="saveClick" :icon="IconCheck" >
        Save
</VueButton>

        <VueButton icon-position="left" color="#39B0F9" id="cancel" ref="cancel" @click="cancelClick" :icon="IconClose" >
        Cancel
</VueButton>

</VueCol>

</VueRow>

</VuePanel>


</VueForm>



</VueAside>


        </VueForm>
</template>





[{"line":843,"column":0,"message":"Parsing error: '}' expected."}]