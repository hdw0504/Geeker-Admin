<template>
	<div class="home card">
		<!-- <img class="home-bg" src="@/assets/images/welcome.png" alt="welcome" /> -->
		<el-upload class="upload-demo" drag action="" :http-request="uploadRequest" multiple accept=".png">
			<el-icon class="el-icon--upload"><upload-filled /></el-icon>
			<div class="el-upload__text">Drop file here or <em>click to upload</em></div>
			<template #tip>
				<div class="el-upload__tip">jpg/png files with a size less than 500kb</div>
			</template>
		</el-upload>
	</div>
</template>

<script setup lang="ts" name="home">
import { request } from "@/api";
import { UploadRequestOptions } from "element-plus";

const uploadRequest = (options: UploadRequestOptions) => {
	console.log("?", options);
	const eggRequest = request("/egg");
	// const fd = new FormData();
	eggRequest
		.post(
			"/upload",
			{ file: options.file },
			{
				headers: {
					"Content-Type": "multipart/form-data"
				}
			}
		)
		.then(() => {});
	// const { file } = options;
	// // 设置默认单次最大上传1kb
	// let max = 1024 * 100;
	// let count = Math.ceil(file.size / max);
	// if (count > 100) {
	// 	max = file.size / 100;
	// 	count = 100;
	// }
	// // 切片文件
	// const chunks = Array.from({ length: count }, (_, i) => ({ file: file.slice(max * i, max * (i + 1)) }));
	// chunks.forEach(chunk=>{
	// 	let fd = new FormData()
	// 	fd.append('file',chunk.file)
	// 	eggRequest.post('')
	// })
};
</script>

<style scoped lang="scss">
@import "./index.scss";
</style>
