<template>
	<div>
	<div id="favor">
			<button v-on:click="Push">Push</button>
			<button v-on:click="SortName">Name</button> 
			<button v-on:click="SortLastName">Lastname</button> 
			<ul >
				<li v-for="(as,item) in mass" :key="item">
					{{as.lastname}}, {{as.firstname}}, {{as.patronymic}}, {{as.number}}
					
				</li>
			</ul>
			<ul >
				<li v-for="(as,item) in moss" :key="item">
					{{as.lastname}}, {{as.firstname}}, {{as.patronymic}}, {{as.number}}
					
				</li>
			</ul>
	</div>
	</div>
</template>

<script>
export default{
	data(){
		return{
		as:"",
		mass:[], 
		moss:[]
		};
	},
	methods:{
			Push: function(){
				let fio = prompt("Введите через пробел Ф И О, номер телефона. Если хотите добавить человека в избранное пятым элементом поставьте единицу");
				fio = fio.split(" ");
				//console.log(fio[0]);
				
				
				if (fio.length == 5){
					this.Move(fio);
				}else{
				this.FMove(fio);
				}
			},
			Move: function(fio){
				let i,j;
				let is_last = 0;
				for (i = 0; i<this.mass.length; i++){
					if (this.mass[i].lastname.localeCompare(fio[0]) >0){
						is_last = 1;
						this.mass.push(this.mass[this.mass.length-1]);
						for(j=this.mass.length-2;j>i;j--){
							this.mass[j] = this.mass[j-1];
						}
						this.mass[i] = {lastname:fio[0],firstname:fio[1], patronymic:fio[2], number:fio[3]};
						break;
					}
				}
				console.log(this.mass);
				if (is_last == 0){
					this.mass.push({lastname:fio[0],firstname:fio[1], patronymic:fio[2], number:fio[3]});
				}
			},
			SortName: function(){
				let i,j;
				for (i = 0; i<this.mass.length; i++){
					for (j = 0; j<this.mass.length-1;j++ ){
						if (this.mass[j].firstname.localeCompare(this.mass[j+1].firstname) >0){
							let o = this.mass[j];
							this.mass[j] = this.mass[j+1];
							this.mass[j+1] = o;
						}
					}
				}				
				this.mass.push();
				this.FSortName();
			},
			SortLastName: function(){
				let i,j;			
				for (i = 0; i<this.mass.length; i++){
					for (j = 0; j<this.mass.length-1;j++ ){
						if (this.mass[j].lastname.localeCompare(this.mass[j+1].lastname) >0){
							let o = this.mass[j];
							this.mass[j] = this.mass[j+1];
							this.mass[j+1] = o;
						}
					}
				}				
				this.mass.push();
				this.FSortLastName();
			},
			FMove: function(fio){
				let is_last = 0;
				let i,j;
				for (i = 0; i<this.moss.length; i++){
					if (this.moss[i].lastname.localeCompare(fio[0]) >0){
						is_last = 1;
						this.moss.push(this.moss[this.moss.length-1]);
						this.moss[i] = {lastname:fio[0],firstname:fio[1], patronymic:fio[2], number:fio[3]};
						for(j=i;j<this.moss.length-2;j++){
							this.moss[j+1] = this.moss[j];
						}
						break;
					}
				}
				if (is_last == 0){
					this.moss.push({lastname:fio[0],firstname:fio[1], patronymic:fio[2], number:fio[3]});
				}
			},
			FSortName: function(){
				let i,j;			
				for (i = 0; i<this.moss.length; i++){
					for (j = 0; j<this.moss.length-1;j++ ){
						if (this.moss[j].firstname.localeCompare(this.moss[j+1].firstname) >0){
							let o = this.moss[j];
							this.moss[j] = this.moss[j+1];
							this.moss[j+1] = o;
						}
					}
				}				
				this.moss.push();
			},
			FSortLastName: function(){
				let i,j;
				for (i = 0; i<this.moss.length; i++){
					for (j = 0; j<this.moss.length-1;j++ ){
						if (this.moss[j].lastname.localeCompare(this.moss[j+1].lastname) >0){
							let o = this.moss[j];
							this.moss[j] = this.moss[j+1];
							this.moss[j+1] = o;
						}
					}
				}				
				this.moss.push();
			}
		}
		
	};

</script>