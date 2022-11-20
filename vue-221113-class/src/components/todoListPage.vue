<template>
    <div class="top_tit">
        {{ message }}
    </div>
    <div class="form-floating mb-3 col-4 center-set">
        <input type="text" class="form-control me-3" id="floatingInput" v-model="new_data">
        <label for="floatingInput">新增代辦事項</label>
        <button type="button" class="btn btn-dark w25" @click="add_new_data">新增</button>
    </div>
    <div class="list_all_show">
        <ul>
            <li class="bt-line" v-for="(item,key) in todos_data">
                <div class="g-div">
                    <input class="form-check-input me-2" type="checkbox" value="" id="" v-model="item.computed">
                    <label class="form-check-label" for="" :class="{'computed':item.computed}">
                        <span>{{ item.todo_tit}}</span>
                    </label>
                </div>
                <div class="del_btn" @click="del_data(key)">X</div>
            </li>
        </ul>
    </div>
</template>

<style scoped>
body {
    margin: 0;
    background: #fff;
    color: #000;
}
.top_tit {
    margin: 5% 0 25px 0;
    font-size: 30px;
    font-weight: bold;
    text-align: center;
}
.center-set {
    margin: 0 auto;
    display: flex;
    align-items: center;
    align-items: stretch;
}
.w25 {
    width: 25%;
}
.list_all_show {
    margin: 40px auto 0;
}
.list_all_show ul {
    list-style-type: none;
    padding: 0;
}
.list_all_show ul li {
    display: flex;
    justify-content: space-between;
}
.bt-line {
    padding:10px 0;
    border-bottom: 1px solid #dadfe3 !important;
}
.del_btn {
    background-color: #212529;
    color: #fff;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 25px;
    height: 25px;
    cursor: pointer;
}
.computed {
    text-decoration-line: line-through;
    color: #7c7c7c;
}

.form-control {
    display: block;
    width: 100%;
    padding: 0.375rem 0.75rem;
    font-size: 1rem;
    font-weight: 400;
    line-height: 1.5;
    color: #212529;
    background-color: #fff;
    background-clip: padding-box;
    border: 1px solid #ced4da;
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    border-radius: 0.375rem;
    transition: border-color .15s ease-in-out,box-shadow .15s ease-in-out;
}
</style>

<script>
    export default {
        data() {
			return {
				message: 'To Do List',
				new_data:'',
				todos_data:[
					{
						todo_tit:'打掃家裡(廚房)',
						computed: false,
					},
					{
						todo_tit:'做作業(vue)',
						computed: false,
					},
				]
			}
		},
        methods: {
			add_new_data(){
				let value = this.new_data;

				if(value == ''){
					alert('請輸入代辦事項，不可空白！');
				}else{
					this.todos_data.push({
						todo_tit:value,
						computed: false,
					});
				}
				//清空new_data
				this.new_data = '';
			},
			del_data(key){
				//.splice(索引值, 要刪除的筆數)
				this.todos_data.splice(key,1);
			}
		},
    }
</script>