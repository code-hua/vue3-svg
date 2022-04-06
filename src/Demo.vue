
<template>
    <img
        :style="{
            color: svgColor,
            fill: svgColor,
            height: height,
            width: width
        }"
        :src="src"
        onload="SVGInject(this)"
    />
    <hr />
    <br />
    <label for="project_desc" style="float:center;font-size: 23px;">更改颜色：</label>
    <input
        type="color"
        name="brand_logo_color"
        readonly="readonly"
        style="width:100px;"
        v-model="svgColor"
        @change="updateColor"
    />
</template>

<script>
import { defineComponent, ref, inject } from 'vue'
export default defineComponent({
    props: {
        svgColor: { type: String, },
        src: { type: String, },
        height: { type: String, },
        width: { type: String, },
    },
    emits: ['result'],
    setup(props, context) {
        const svgColor = ref(props.svgColor)
        const src = ref(props.src)
        const height = ref(props.height)
        const width = ref(props.width)
        const reloadd = inject("reload");
        const updateColor = () => {
            context.emit('result', svgColor.value);
            reloadd();
        }
        return { svgColor, src, updateColor, svgColor, width, height }
    },
})
</script>