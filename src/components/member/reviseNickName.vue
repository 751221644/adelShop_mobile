<template>
	<div>
		<headersec tabname="修改昵称" ref="noback"></headersec>
		<div class="container_div">
			<input class="input" type="text" id="inp_nickName" />
		</div>
		<div class="btn_div">
			<button class="btn_save" @click="saveNickname">保存</button>
		</div>
	</div>
</template>
<script>
	import Headersec from '../base/HeaderSec.vue';
	export default {
		components: {
			Headersec,
		},
		mounted() {},
		methods: {
			// saveNickname() {
			// 	const that = this
			// 	var nickName = document.getElementById('inp_nickName').value;
			// 	// this.$http.post('/myapi/adel-shop/app/auth/updateUser.htm?nickName='+nickName)
			// 	// 	.then(function(res) {
			// 	// 	})
			// 	// 	.catch((error) => {
			// 	// 		console.error(error);
			// 	// 	})
			// 	var getPersonUrl = '/myapi/adel-shop/app/auth/updateUser.htm?nickName=' + 11
			// 	this.$http.post(getPersonUrl)
			// 		.then(function(res) {
			// 			console.log(res.data.data)
			// 		})
			// 		.catch(function(error) {
			// 			console.log(error);
			// 		});
			// }
			saveNickname() {
				var nickName = document.getElementById('inp_nickName').value;
				console.log('tyyyyyyyyy',typeof(nickName));
				const that = this
				var getPersonUrl = '/myapi/adel-shop/app/auth/updateUser.htm?nickName='+nickName
				this.$http.post(getPersonUrl)
					.then(function(res) {
						console.log(res.data.message)
						if (res.data.message == null) {
							// that.setCookie('UserName', userName, 365)
							// that.setCookie('password', passWord, 365)
							// that.getCookie(userName)
							that.tofirstPage();
						} else {}
					})
					.catch(function(error) {
						console.log(error);
					});
			},
		}
	}
</script>
<style>
	.container_div {
		display: flex;
		height: 2rem;
		justify-content: center;
	}
	.input {
		margin-top: 1.2rem;
		width: 80%;
		height: .6rem;
		border-bottom: 1px solid;
		border-radius: .5rem;
		/* color: green; */
		outline: none;
		font-size: .3rem;
		border-right: 1px solid;
	}
	.btn_div {
		display: flex;
		justify-content: center;
	}
	.btn_save {
		width: 80%;
		height: .7rem;
		font-size: .3rem;
		border-radius: .5rem;
		color: white;
		background-color: #E43448;
		outline: none;
		margin-top: .5rem;
	}
</style>

