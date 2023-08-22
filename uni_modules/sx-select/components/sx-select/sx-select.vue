<template>
	<picker class="sx-select" @change="pickerChange" :value="index" :range="items" :range-key="itemText">
		<slot :title="selectTitle">
			<text class="sx-select-title" :class="className">
				{{ selectTitle }}
			</text>
		</slot>
	</picker>
</template>

<script>
	export default {
		name: 'sx-select',
		props: {
			value: String | Number,
			items: {
				type: Array,
				default: () => {
					return [];
				}
			},
			itemText: {
				type: String,
				default: 'text'
			},
			itemValue: {
				type: String,
				default: 'value'
			},
			title: {
				type: String,
				default: '请选择'
			},
			className: String
		},
		data() {
			return {
				index: undefined
			};
		},
		methods: {
			pickerChange(e) {
				this.index = e.target.value;
				const value = this.item ? this.item[this.itemValue] || this.item : '';
				this.emit(value);
			},
			getIndex() {
				this.index = this.items.findIndex(v => (v[this.itemValue] || v) === this.value);
			},
			emit(value) {
				this.$emit('input', value);
				this.$emit('change', value);
			}
		},
		computed: {
			item() {
				return this.items[this.index];
			},
			selectTitle() {
				if (typeof this.index === 'number' && this.index !== -1) {
					return this.item ? this.item[this.itemText] || this.item : this.value;
				} else {
					return this.title;
				}
			}
		},
		created() {
			this.getIndex();
		},
		watch: {
			items() {
				this.getIndex();
			},
			value(value) {
				this.getIndex();
				this.emit(value);
			}
		}
	};
</script>

<style scoped>
	/* 	.sx-select .sx-select-title {
		font-size: 12px;
	} */
</style>