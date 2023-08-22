<template>
	<view class="content">
		
		<view class="title">默认状态：</view>
		<view class="item">
			<sx-select v-model="model" :items="[]" />
		</view>
		<view class="title">推荐用法1：使用官方uni-list和uni-item组件使用</view>
		<view class="item">

			<uni-list>
				<sx-select v-model="model" :items="sexItems">
					<template slot-scope="{title}">
						<uni-list-item title="性别" show-arrow :right-text="title" />
					</template>
				</sx-select>
				<sx-select v-model="job" :items="jobItems" title="">
					<template slot-scope="{title}">
						<uni-list-item title="职业" show-arrow :right-text="title" />
					</template>
				</sx-select>
			</uni-list>
		</view>

		<view class="title">推荐用法2：结合官方uni-icon使用</view>
		<sx-select v-model="model" :items="cityItems" title="选择城市">
			<template slot-scope="{title}">
				<text style="font-size: 14px;">{{title}}</text> <uni-icons type="bottom"></uni-icons>
			</template>
		</sx-select>
	</view>
</template>

<script>
	const sexItems = [{
		text: '男',
		value: 1
	}, {
		text: '女',
		value: 2
	}];
	const jobItems = [{
			text: '前端开发工程师',
			value: '1'
		}, {
			text: '后端开发工程师',
			value: '2'
		},
		{
			text: '测试工程师',
			value: '3'
		}
	]
	const cityItems = [{
		text: '北京',
		value: 1
	}, {
		text: '上海',
		value: '2'
	}]

	export default {
		data() {
			return {
				model: '',
				job: '1',
				sexItems,
				jobItems,
				cityItems
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	.content {
		padding: 10px;
	}

	.title {
		font-size: 14px;
		font-weight: bold;
		margin-bottom: 10px;
	}

	.item {
		margin-bottom: 20px;
	}
</style>