<script>
export default {
    props: {
        modelValue: { type: String, default: ""},
    },
    emits: ["submit", "update:modelValue"],
    method: {
        updateModelValue(e) {
            this.$emit("update:modelValue", e.target.Value);
        },
        submit(){
            this.$emit("submit");
        },
    },
}
</script>

<template>
    <div class = "input-group">
        <input
            type="text"
            class="form-control"
            placeholder="Nhập thông tin cần tìm"
            :value="modelValue"
            @input="updateModelValue"
            @keyup.enter="submit"
        />
        <div class="input-group-append">
            <button
            class="btn btn-outline-secondary"
            type="button"
            @click="submit"
            >
            <i class="fas fa-search"></i> Tìm kiếm
            </button>
        </div>
    </div>
</template>


<!-- 
props: một component có thể nhận dữ liệu từ cha
   + modelValue là một prop duy nhất của component này, giúp con nhận dữ liệu từ cha
   + kiểu dữ liệu của props là String
   + Giá trị mặc định là chuỗi rỗng, nếu kg có nào truyền từ cha

   emits: khai báo sự kiện mà component này có thể phát ra
   + submit : khi người dùng nhất nút gửi
   + update:modelValue - khi giá trị nhập thay đổi, giúp cập nhật dữ liệu con lên cha

   method: xử lý sự kiện
    + updateModelValue(e): gọi khi người dùng thay đổi nội dung, gửi từ con lên cha
        phát ra sự kiện update:modelValue về component cha
        truyền giá trị e.target.Value về cha
    + submit: gọi hàm khi phát ra sự kiện "submit" về component cha
    + Dùng để xử lý khi người dùng nhấn nút gửi dữ liệu

-->
