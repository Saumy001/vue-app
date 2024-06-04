<template>
<div>
    <table>
        <thead>
            <tr>
                <th>Serial no.</th>
                <th>Image</th>
                <th>Name</th>
                <th>Address</th>
                <th>Age</th>

            </tr>
        </thead>
        <tbody>
            <tr v-for="(user, index) in users" :key="user.id">
                <td>{{ index+1 }} </td>
                <td>
                    <img :src="user.image" @click="openModal(user.image)" alt="user image" style="cursor: pointer; width: 50px; height: 50px;" />
                </td>

                <td>{{ user.name }}</td>
                <td>{{ user.address }}</td>
                <td>{{ user.age }}</td>
            </tr>
        </tbody>
    </table>

    <div v-if="showModal" class="modal" @click.self="closeModal">
        <div class="modal-content">
            <span class="close" @click="closeModal">&times;</span>
            <img :src="modalimage" alt="user image" />
        </div>
    </div>
</div>
</template>

        
<script>
export default {
    data() {
        return {
            users: [{
                    id: 1,
                    image: '',
                    name: 'Virat Kohi',
                    address: 'Delhi',
                    age: 35
                },
                {
                    id: 2,
                    image: '',
                    name: 'Rohit Sharma',
                    address: 'Mumbai',
                    age: 37
                }

            ],
            showModal: false,
            modalImage: ''
        };
    },
    methods: {
        openModal(image) {
            this.modalImage = image;
            this.showModal = true;
        },
        closeModal() {
            this.showModal = false;
            this.modalImage = ''
        }
    }
};
</script>

            
<style>
table {
    width: 100%;
    border-collapse: collapse;
}

th,
td {
    border: 1px solid #ddd;
    padding: 8px;
}

th {
    background-color: #f2f2f2;
    text-align: left;
}

.modal {
    display: block;
    position: fixed;
    z-index: 1;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    overflow: auto;
    background-color: rgb(0, 0, 0);
    background-color: rgba(0, 0, 0, 0.4);
}

.modal-content {
    margin: 15% auto;
    padding: 20px;
    border: 1px solid #888;
    width: 80%;
    max-width: 500px;
    background-color: white;
}

.close {
    color: #aaa;
    float: right;
    font-size: 28px;
    font-weight: bold;
}

.close:hover,
.close:focus {
    color: black;
    text-decoration: none;
    cursor: pointer;
}

.modal-content img {
    width: 100%;
    height: auto;
}
</style>
