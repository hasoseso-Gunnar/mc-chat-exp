<template>
  <div class="q-pa-md items-start q-gutter-md">
      <q-card class="q-pb-lg">
          <div class="q-pa-md row justify-center">
              <div style="width: 80%;">
                  <diV v-for="thread in threads">
                      <q-chat-message
                          :name= thread.name
                          :avatar=thread.avatar
                          :text=thread.thread
                          :sent=thread.sent
                          bg-color="grey-2"
                      />
                  </diV>
                  <q-chat-message
                      bg-color="grey-2"
                      name="bot君"
                      avatar="https://cdn.quasar.dev/img/avatar2.jpg"
                      v-if="botkunLoading"
                  > 
                      <q-spinner-dots size="2rem" />
                  </q-chat-message>
              </div>
          </div>
          <div style="width: 80%; margin-left: auto; margin-right: auto;">
              <q-input                
                  outlined
                  dense
                  v-model="message[0]"
                  label="メッセージ"
                  icon="send"
                 >
                  <template v-slot:after>
                      <q-btn 
                          flat 
                          dense
                          label="送信"
                          type="submit"
                          @click="sendGPTmessage"
                      />
                  </template>
              </q-input>
          </div>
      </q-card>
      <div class="text-left text-h5 article_headline">使用方法 / 注意事項</div>
      <div>
          <p style="font-size: 1rem; line-height: 180%;">
              ・「メッセージ」欄に文字を入力し、「送信」ボタンを押すことでテキストが送信される。<br>
              ・無料版のAPIなので、返信には30～60秒ほど掛かる。<br>
              <br>
          </p>
      </div>
  </div>
</template>
<script setup lang="ts">
  import { ref, onMounted } from "vue";
  import { useQuasar } from "quasar";

  //ページを増やすときはここを必ず変える！
  const pageId = ref<string>('7');

  const $q = useQuasar();
  const display = ref<boolean>(false);

  //GPT周りの変数
  const message = ref<Array<string>>(['']);
  const botkunLoading = ref<boolean>(false);
  const threads = ref<Array<any>>([
      {
          name:'bot君',
          thread:['なんでも話しかけてね！'],
          avatar:'https://cdn.quasar.dev/img/avatar2.jpg',
          sent:false,
      }
  ]);

  //GPTメッセージ送信時の処理
  async function sendGPTmessage(){

      botkunLoading.value = true;

      // 結果を挿入
      threads.value.push({
          name:'諸君',
          thread: message.value,
          avatar:'https://cdn.quasar.dev/img/avatar4.jpg',
          sent:true,
      });

      //GASにリクエスト送信
      const requestOptions = {
          method: 'POST',
          headers: {
                  'Content-Type': 'application/x-www-form-urlencoded',
              },
          body: `message=${message.value[0]}`,
      };

      message.value = [''];

      const promise = await fetch("https://script.google.com/macros/s/AKfycbzxPJHFTRwVBQ_uluyIc1LEXu2QaUSGKAzEZQb9PssIXItoMzdF1HuglTMBFELeMWhR/exec", requestOptions);
      const data = await promise.json();

      // レスポンスを挿入
      threads.value.push({
          name:'bot君',
          thread:[data.res],
          avatar:'https://cdn.quasar.dev/img/avatar2.jpg',
          sent:false,
      })

      botkunLoading.value = false;
  }

  function liked () {
      $q.notify({
          color: 'green-4',
          textColor: 'white',
          icon: 'thumb_up_off_alt',
          message: 'いいね機能近日実装予定'
      });
  }
</script>
<style scoped>
  blockquote {
      margin: 0;
  }

  blockquote p {
      padding: 15px;
      background: #eee;
      border-radius: 5px;
  }

  strong{
      font-weight: bold
  }

  .responsive_flex{
      display: flex;
  }

  .insert_img{
      width:70%;
      margin-left: 15%;
  }
  .tatenaga_img{
      height: 600px;
      width: 50%;
      margin-left: 25%;
  }

  .comment_section{
      max-width: 400px; 
      margin-left: 10px;
      margin-bottom: 10px;
  }

  .yokonaga_img{
      width: 100%;
      height: 400px;
  }

  @media screen and (max-width: 1024px){
      div.responsive_flex{
          display: block;
      }
      div.insert_img{
          width:90%;
          margin-left: 5%;
      }
      div.comment_section{
          max-width: 90%; 
          margin-left: 5%;
          margin-bottom: 10px;
      }
      div.tatenaga_img{
          height: 300px;
          width: 90%;
          margin-left: 5%;
      }
      .yokonaga_img{
          height: 300px;
          width: 90%;
          margin-left: 5%;
      }
  }
  pre code {
      font-size: .8rem;
      margin: 1.5rem 0;
      padding: 0.5rem 0.5rem;
      background-color: #364549;
      color: #e3e3e3;
      width: 100%;
      display: inline-block;
      font-family: Consolas, Menlo, Monaco, -apple-system, BlinkMacSystemFont, "Segoe UI", Meiryo, monospace;
      overflow-x: auto;
      -webkit-overflow-scrolling: touch;
  }
  .article_headline{
      font-weight: bold;
      margin-top: 30px;
      padding: 0.4em 0.5em;
      color: #494949;
      background: #f4f4f4;
      border-left: solid 5px #9c27b0;
      border-bottom: solid 3px #d7d7d7;
  }
</style>