
<template>
    <div id="app">


        <div class="image-upload">
            <label for="file-input">
                <img :src="imageSrc" class="image" name="photo"  accept="image/*">
            </label>
            <label for="file-input2">
                <img :src="imageSrc2" class="image" name="photo2"  accept="image/*">
            </label>
            <input @change="uploadImage" id="file-input" type="file" name="photo" accept="image/*">
            <input @change="uploadImage" id="file-input2" type="file" name="photo2" accept="image/*">
        </div>
    </div>

</template>

<script>
    export default {
        name: 'app',
        data () {
            return {
                title: 'Hello',
                imageSrc: 'https://t3.ftcdn.net/jpg/00/64/67/52/240_F_64675209_7ve2XQANuzuHjMZXP3aIYIpsDKEbF5dD.jpg',
                imageSrc2: 'https://cdn2.iconfinder.com/data/icons/picons-essentials/71/user_add-512.png'
            }
        },
        methods: {
            uploadImage: function(e) {
                var files = e.target.files;
                if(!files[0]) {
                    return;
                }
                var data = new FormData();
                data.append('media', files[0])
                var reader = new FileReader();
                reader.onload = (e) => {
                    this.imageSrc = e.target.result;
                };
                reader.readAsDataURL(files[0]);
            },
            uploadImage2: function(e) {
                var files = e.target.files;
                if(!files[0]) {
                    return;
                }
                var data = new FormData();
                data.append('media', files[0])
                var reader = new FileReader();
                reader.onload = (e) => {
                    this.imageSrc2 = e.target.result;
                };
                reader.readAsDataURL(files[0]);
            }
        }
    }
</script>

<style>
    body {
        margin: 0;
    }
    .image {
        width: 50%;
        height: 50%;
        display: block;
        margin: 0 auto;
        z-index: 2;
    }
    .container {
        margin: 0 auto;
        width: 600px;

    }
    .image-upload > input
    {
        display: none;
    }
</style>