<template>
  <div class="chat-wrapper">
    <div class="chat-header gr" @click.once="chatInit" v-if="!visible">
      <div class="chat-header__text">Шушпанчик на связи!</div>
      <div class="chat-header__photo"></div>
    </div>
    <div class="chat-body gr" v-if="visible">
      <div class="chat-area">
        <div  
          class="dialog" 
          v-for="(message, index) in lastChat"
          :class="'dialog-'+message.type"
          :key="index"
          >
            <div class="dialog-avatar"></div>
            <div class="dialog-text">{{message.text}}</div>
            
        </div>
        
      </div>
      <form class="input-message" @submit.prevent="sendMessage"> 
        <textarea
        id="inputMessageTextarea"
        rows="2"
        v-model.trim="query"
        @submit="sendMessage"
        @keydown.enter.prevent="sendMessage"
        />
        <button type="submit">🔥</button>
      </form>
      
      
      {{ info }}
    </div>
    
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Chat',
  data () {
    return {
      info: null,
      query: '',
      visible: false,
      lastMessage: '',
      chat: [
        {
          type: 'in',
          text: 'Шушпанчик ждёт, пока ты ему что-то напишешь :)'
        }
      ]
    }
  },
  computed: {
    lastChat: function () {
      return this.chat.slice(-8)
    }
  },
  methods: {
    chatInit: function () {
      this.visible = true
      // document.querySelector('textarea#inputMessageTextarea').focus()
    },
    sendMessage: function () {      
      if ((this.lastMessage != this.query) && (this.query != '')) {

        this.lastMessage = this.query

        this.chat.push({
          type: 'out',
          text: this.query
        }) 

        let data = new FormData()
        data.append('q', this.query)
        axios
          .post('/api/get-answer', data,
            {
              headers: {
                'Content-type': 'application/x-www-form-urlencoded'
              }
            }
          )
          .then(response => {
              if (response.status == 200) {
                this.chat.push({
                  type: 'in',
                  text: response.data.a
                }) 
              } 
            }
                       
          )

        this.query = ''
      }
      
    }
  },
  mounted () {

  }
}
</script>

<style lang="scss" scoped>
.chat-wrapper {
  position: fixed;
  padding: 10px;
  right: 10px;
  bottom: 10px;
  max-width: 340px;
  z-index: 1000;
  color: #000;
  overflow: hidden;
}

.chat-header {
  $block-height: 45px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  border-radius: $block-height;
  cursor: pointer;
  box-shadow: 0 5px 6px 0px rgba(0,0,0,.3);
  transition: .3s;

  &:hover {
    transform: translateY(-3px);
    box-shadow: 0 10px 12px 3px rgba(0,0,0,.3);
  }

  &__text {
    padding: 0 10px 0 25px;
    font-weight: 600;
    color: #3d3d9a;
  }
  &__photo {
    width: $block-height;
    height: $block-height;
    border-radius: $block-height;
    background-image: url('http://www.netlore.ru/userfiles/image/sush_4.jpg');
    background-size: 100%;
    border: 2px solid #fff;
  }
}

.chat-body {
  margin-top: 15px;
  padding: 15px 25px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  border-radius: 25px;
  box-shadow: 0 5px 6px 0px rgba(0,0,0,.3);
  transition: .3s;
  max-height: 80vh;
  overflow-y: auto;
  overflow-x: hidden
}

.chat-area {
  .dialog {
    display: flex;
    flex-direction: row;
    align-items: center;
    max-width: 280px;
    margin: 10px 0;

    .dialog-text {
      margin: 0 10px;
    }

    .dialog-avatar {
      $block-height: 45px;
      width: $block-height;
      height: $block-height;
      border-radius: $block-height;
      flex-shrink: 0;
      background: #5595c8;
      background-size: 100%;
      border: 2px solid #fff;
    }
  }
  .dialog-out {
    flex-direction: row-reverse;
  }

  .dialog-in {
    .dialog-avatar {
      background-image: url('http://www.netlore.ru/userfiles/image/sush_4.jpg');
    }
  }
}

.input-message {
  margin-top: 15px; 
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  align-items: stretch;

  textarea, button {
    outline: none;
    font-size: 24px;
  }

  textarea {
    resize: none;
    background: rgba(255,255,255,.4);
    border: none;
    overflow: auto;
    caret-color: rgb(238, 0, 186);
    border-radius: 15px 0 0 15px;
    width: 100%;
    padding-left: 10px;
  }

  button {
    border-radius: 0 15px 15px 0;
    border: none;
    border-bottom: 2px solid rgb(207, 207, 207);
    min-width: 50px;
    background-color: white;
  }
}

.gr {
  background: linear-gradient(-45deg, #d6a191, #cf91a9, #d2f3ff, #b6e7dc);
  background-size: 400% 400%;
  animation: Gradient 15s ease infinite;
}

@keyframes Gradient {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

</style>
