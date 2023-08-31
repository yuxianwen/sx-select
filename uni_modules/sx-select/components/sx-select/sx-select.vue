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
			value: null,
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
		methods: {
			pickerChange(e) {
				const index = e.target.value;
				const value = this.items[index][this.itemValue]
				this.$emit('input', value);
				this.$emit('change', value);
			}
		},
		computed: {
			item() {
				return this.items[this.index];
			},
			index() {
				return this.items.findIndex(v => {
					return JSON.stringify(v[this.itemValue]) === JSON.stringify(this.value.valueOf())
				});
			},
			selectTitle() {
				if (typeof this.index === 'number' && this.index !== -1) {
					return this.item ? this.item[this.itemText] : this.value;
				} else {
					return this.title;
				}
			}
		}
	};
</script>