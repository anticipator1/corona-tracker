<template>
    <div class="Dashboard grey lighten-4">
         <v-container  class="my-5">
    <v-card> 
    <v-card-title>
      <h2 class="primary--text">Corona Cases</h2>
      <v-spacer></v-spacer>
     <v-text-field v-model="search" placeholder="Country Name..."></v-text-field>
    </v-card-title>
      <table class="table table-hover table-fixed">
	    <thead> 
	      <tr>
		    <th tabindex="0" style="" data-field="name">
		  <div class="th-inner both">Country</div>
		  <div class="fht-cell"></div>
		</th>
		<th tabindex="0" style="" data-field="name">
		  <div class="th-inner both">Total Confirmed</div>
		  <div class="fht-cell"></div>
		</th>
		<th tabindex="0" style="" data-field="price">
		  <div class="th-inner both">Total Death</div>
		  <div class="fht-cell"></div>
		</th>
        <th tabindex="0" style="" data-field="price">
		  <div class="th-inner both">Total New Cases</div>
		  <div class="fht-cell"></div>
		</th>
        <th tabindex="0" style="" data-field="price">
		  <div class="th-inner both">New Deaths</div>
		  <div class="fht-cell"></div>
		</th>
        <th tabindex="0" style="" data-field="price">
		  <div class="th-inner both">Total Recovered</div>
		  <div class="fht-cell"></div>
		</th>
        <th tabindex="0" style="" data-field="price">
		  <div class="th-inner both">New Recovered</div>
		  <div class="fht-cell"></div>
		</th>
	      </tr>
	    </thead>
	    <tbody>
            <tr v-for="coun in filtered" :key="coun.index">
               <td>{{coun.Country}}</td>
               <td class="green--text">{{coun.TotalConfirmed}}</td>
               <td class="red--text">{{coun.TotalDeaths}}</td>
               <td class="amber--text">{{coun.NewConfirmed}}</td>
                <td class="orange--text">{{coun.NewDeaths}}</td>
                <td class="blue--text">{{coun.TotalRecovered}}</td>
                <td class="cyan--text">{{coun.NewRecovered}}</td>
            </tr>      
	    </tbody>
	  </table>
  </v-card>
         </v-container>
    </div>
</template>

<script>
export default {
    name:'Home',
    data(){
        return{
            search:'',
            res:[],
            
        }
    },
   created(){
        async function asyncData(){
	    const response = await fetch('https://api.covid19api.com/summary');
	    const data = await response.json();
	    return data;
         }
        
             const result = asyncData();
            result.then(data =>{
                this.res=data.Countries
                //this.coun=data.Countries[1].Country
                 //   if(data.Countries[i].Country=='Nepal'){
                   //     console.log("Total Confirmed cases : "+data.Countries[i].TotalConfirmed);
                     //   console.log("Total deaths: "+data.Countries[i].TotalDeaths);
                   
            }
            );
        },
        
        computed:{
            filtered:function(){
                return this.res.filter((coun)=>{
                    return coun.Country.toLowerCase().match(this.search.toLowerCase());
                });
            }
        }
    
}
</script>


<style lang="scss" scoped>


.table-fixed{
  width: 100%;
  background-color: #f3f3f3;
  tbody{
    height:300px;
    overflow-y:auto;
    width: 100%;
    }
}
</style>