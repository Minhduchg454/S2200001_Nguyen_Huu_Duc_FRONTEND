<script>
export default{
    props: {
        contacts: { type: Array, default: []},
        activeIndex: { type: Number, default: -1},
    },
    emits: ["update:activeIndex"],
        methods: {
            updateActiveIndex(index) {
                this.$emit("update:activeIndex", index);
            }
        }
};
</script>

<template>
    <ul class="list-group">
        <li
        class="list-group-item"
            v-for="(contact,index) in contacts"
            :key="contact._id"
        :class="{ active: index === activeIndex}"
        @click="updateActiveIndex(index)"
        >
            {{ contact.name }}
        </li>
    </ul>
</template>


<!-- 
    props: nhận dữ liệu từ component cha
        + contacts nhận danh sách liên hệ từ cha, là một mảng
        + Chỉ số liên hệ được chọn, mặc định là -1

    emits: sự kiện, cập nhật activeIndex cho cha khi người dùng click vào một liên hệ
        +method: 
            Khi click vào một liên hệ, gọi updateActiveIndex(index).
	        Phát sự kiện "update:activeIndex" để component cha cập nhật activeIndex.

    Template: hiển thị danh sách liên hệ, chọn một liên hệ và làm nổi bật liên hệ đó
        +hiện danh sách với v-for, lập qua mảng contact với index, tạo danh sách với li
            contact: dữ liệu từng liên hệ, index là số thứ tự phần tử trong mảng
            :key="contact._id" giúp Vue nhận diện từng phần tử trong danh sách, dễ dàng cập nhật khi có thay đổi

    Nếu index === activeIndex thì thêm class"active" làm nổi bật liên hệ đó
        Bắt sự kiện Click: khi click vào liên hệ, cập nhật activeIndex lên cha

-->