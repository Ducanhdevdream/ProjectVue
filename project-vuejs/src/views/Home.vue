<template>
  <div class="container">
    <div class="main-content">
      <div class="content">
        <draggable
            class="drag-wrap"
            :list="directories"
            group="directories"
            :move="moveDirectory">
          <List class="directory" v-for="(directory) in directories" :key="directory.id" :id="directory.id"
                :directory="directory"
                @reloadDirectories="getData"/>
          <div class="listWrap add-directory-btn" ref="addListBtn" @click="createListForm()">
            
          </div>
          <div class="listWrap add-directory-form" id="addWrap" ref="addListWrap">
            <el-input placeholder="Nhập tiêu đề danh sách." v-model="directoryName"></el-input>
            <el-button type="success" class="add-list" @click="createList">Thêm danh sách</el-button>
            <i class="el-icon-close close-add-list" @click="cancelCreateList()"></i>
          </div>
        </draggable>
      </div>
    </div>
  </div>
</template>

<script>
import List from "@/components/List";
import { mapState, mapMutations } from 'vuex'
import draggable from 'vuedraggable'


export default {
  name: 'Home',
  components: {
    List,
    draggable
  },
  data () {
    return {
      dynamicValidateForm: {
        directoryName: ''
      },
      directoryName: '',
      cards: [],
      newList: [],
      directories: [],
    }
  },
  computed: {
    ...mapState('auth', ['isAuthenticated']),
  },
  methods: {
    ...mapMutations('home', [
       'addList'
    ]),
    
  },
  mounted() {
    
  },
}
</script>

<style lang="scss" scoped>
  .container {
    height: 95vh;
    overflow-x: auto;

    .main-content {
      position: relative;
      outline: none;
      margin: 0 7px;

      .content {
        position: absolute;
        overflow-x: auto;
        top: 45px;

        .listWrap {
          padding: 12px;
          text-align: left;
          background-color: rgba(255, 255, 255, 0.24);
          border-radius: 4px;
          width: 270px;
          font-size: 15px;
          box-sizing: border-box;
          float: left;
          margin-right: 15px;
          cursor: pointer;
        }

        #addWrap {
          background: white !important;
          color: #67748a;
          display: none;
          
          .add-list {
            padding: 7px 10px;
            margin: 5px 10px 0 0;
          }

           .close-add-list {
            font-size: 16px;
          }
        }
      }
    }
  }

   .container::-webkit-scrollbar {
    width: 8px;
  }
  
  .container::-webkit-scrollbar-track {
    border-radius: 8px;
    background-color: #56567e7d;
  }

  .container::-webkit-scrollbar {
    height: 10px;
  }

  .container::-webkit-scrollbar-thumb:hover {
    background: #bfbfc47d;
  }

  .container::-webkit-scrollbar-track {
    border-radius: 7px;
    background-color: #57575a73;
  }

  .container::-webkit-scrollbar-thumb {
    background: #cfcfd163;
    border-radius: 7px;
  }
</style>
