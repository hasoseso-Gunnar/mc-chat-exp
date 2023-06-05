<template>
    <p class="text-h5">さまざまな物事への考え方に関する調査</p>
    <q-tabs
        v-model="tab"
        class="text-teal"
        style="display: none;"
    >
        <q-tab name="start" label="Start"/>
        <q-tab name="explain" label="Explain"/>
        <q-tab name="chat" label="Chat"/>
    </q-tabs>
    <q-tab-panels
        v-model="tab"
        animated
    >
        <q-tab-panel name="start">
            <div class="q-pa-md">
                <p class="text-subtitle1 text-black">1. あなたは選択的夫婦別姓制度制度に賛成ですか？反対ですか？</p>
                <div class="row">
                    <div class="col-2" align="center">
                        <p>賛成</p>
                        <q-radio v-model="radioAgree" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="agree" />
                    </div>
                    <div class="col-2" align="center">
                        <p>反対</p>
                        <q-radio v-model="radioAgree" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="disagree" />
                    </div>
                </div>
            </div>
            <div class="q-pa-md q-mt-xl">
                <p class="text-subtitle1 text-black">2. 以下に続けて各質問を読み，あなたの考えに最もよく当てはまる選択肢を選んでください。</p>
                <div style="height: 40px;"></div>
                <p class="text-subtitle1 text-black">『<span class="text-red-9">選択的夫婦別姓制度</span>に関するあなたの考えは・・・』</p>
                <div style="height: 40px;"></div>
                <p class="text-subtitle1 text-black">あなたが根底に持っている道徳的な信念や信条を，どのくらい反映していますか？</p>
                <div class="row">
                    <div class="col-2" align="center">
                        <p>全く反映していない</p>
                        <q-radio v-model="radioMC1" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="1" />
                    </div>
                    <div class="col-2" align="center">
                        <p>少し反映している</p>
                        <q-radio v-model="radioMC1" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="2" />
                    </div>
                    <div class="col-2" align="center">
                        <p>ある程度反映している</p>
                        <q-radio v-model="radioMC1" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="3" />
                    </div>
                    <div class="col-2" align="center">
                        <p>強く反映している</p>
                        <q-radio v-model="radioMC1" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="4" />
                    </div>
                    <div class="col-2" align="center">
                        <p>非常に強く反映している</p>
                        <q-radio v-model="radioMC1" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="5" />
                    </div>
                </div>
                <div style="height: 40px;"></div>
                <p class="text-subtitle1 text-black">基本的な善悪についての，あなたの考え方と，どのくらい関係していますか？</p>
                <div class="row">
                    <div class="col-2" align="center">
                        <p>全く関係していない</p>
                        <q-radio v-model="radioMC2" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="1" />
                    </div>
                    <div class="col-2" align="center">
                        <p>少し関係している</p>
                        <q-radio v-model="radioMC2" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="2" />
                    </div>
                    <div class="col-2" align="center">
                        <p>ある程度関係している</p>
                        <q-radio v-model="radioMC2" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="3" />
                    </div>
                    <div class="col-2" align="center">
                        <p>強く反映している</p>
                        <q-radio v-model="radioMC2" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="4" />
                    </div>
                    <div class="col-2" align="center">
                        <p>非常に強く関係している</p>
                        <q-radio v-model="radioMC2" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="5" />
                    </div>
                </div>
                <div style="height: 40px;"></div>
                <p class="text-subtitle1 text-black">どのくらい，道徳的な原則に基づくものですか？</p>
                <div class="row">
                    <div class="col-2" align="center">
                        <p>全く基づかない</p>
                        <q-radio v-model="radioMC3" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="1" />
                    </div>
                    <div class="col-2" align="center">
                        <p>少し基づく</p>
                        <q-radio v-model="radioMC3" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="2" />
                    </div>
                    <div class="col-2" align="center">
                        <p>ある程度基づく</p>
                        <q-radio v-model="radioMC3" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="3" />
                    </div>
                    <div class="col-2" align="center">
                        <p>強く基づく</p>
                        <q-radio v-model="radioMC3" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="4" />
                    </div>
                    <div class="col-2" align="center">
                        <p>非常に強く基づく</p>
                        <q-radio v-model="radioMC3" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="5" />
                    </div>
                </div>
                <div style="height: 40px;"></div>
                <p class="text-subtitle1 text-black">どのくらい，道徳的なスタンスを表していますか？</p>
                <div class="row">
                    <div class="col-2" align="center">
                        <p>全く表していない</p>
                        <q-radio v-model="radioMC4" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="1" />
                    </div>
                    <div class="col-2" align="center">
                        <p>少し表している</p>
                        <q-radio v-model="radioMC4" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="2" />
                    </div>
                    <div class="col-2" align="center">
                        <p>ある程度表している</p>
                        <q-radio v-model="radioMC4" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="3" />
                    </div>
                    <div class="col-2" align="center">
                        <p>強く表している</p>
                        <q-radio v-model="radioMC4" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="4" />
                    </div>
                    <div class="col-2" align="center">
                        <p>非常に強く表している</p>
                        <q-radio v-model="radioMC4" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="5" />
                    </div>
                </div>
                <div align="right">
                    <q-btn 
                        v-if="radioAgree === '' || radioMC1 === '' || radioMC2 === '' || radioMC3 === '' || radioMC4 === ''"
                        label="次のページへ"
                        flat
                        class="bg-grey text-white"
                    ></q-btn>
                    <q-btn 
                        v-else
                        label="次のページへ"
                        flat
                        class="bg-blue-7 text-white"
                        @click="toExplain"
                    ></q-btn>
                </div>
            </div>
        </q-tab-panel>
        <q-tab-panel name="explain">
            <div class="q-pa-md">
                <p class="text-subtitle1 text-black">この次のセクションからは、「選択的夫婦別姓制度」に関して人物との会話を行ってもらいます。</p>
                <p class="text-subtitle1 text-black">また、この人物はあなたと{{ opinion }}意見を持っています。</p>
                <div style="height: 40px;"></div>
                <p class="text-subtitle1 text-black">以上のことを踏まえ、会話を始める前に以下の質問について回答してください。</p>
                <div style="height: 40px;"></div>
                <p class="text-subtitle1 text-black">この後の会話を通してどのくらい相手の意見は変わると思いますか？</p>
                <div class="row">
                    <div class="col-2" align="center">
                        <p>全く変わらない</p>
                        <q-radio v-model="radioCA" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="1" />
                    </div>
                    <div class="col-2" align="center">
                        <p>少ししか変わらない</p>
                        <q-radio v-model="radioCA" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="2" />
                    </div>
                    <div class="col-2" align="center">
                        <p>ある程度変わる</p>
                        <q-radio v-model="radioCA" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="3" />
                    </div>
                    <div class="col-2" align="center">
                        <p>かなり変わる</p>
                        <q-radio v-model="radioCA" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="4" />
                    </div>
                    <div class="col-2" align="center">
                        <p>完全に変わる</p>
                        <q-radio v-model="radioCA" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="5" />
                    </div>
                </div>
                <div align="right">
                    <q-btn 
                        v-if="radioCA === ''"
                        label="次のページへ"
                        flat
                        class="bg-grey text-white"
                    ></q-btn>
                    <q-btn 
                        v-else
                        label="次のページへ"
                        flat
                        class="bg-blue-7 text-white"
                        @click="toChat"
                    ></q-btn>
                </div>
            </div>
        </q-tab-panel>
        <q-tab-panel name="chat">
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
                                v-if="loading"
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
                        ・「メッセージ」欄に文字を入力し、「送信」ボタンを押すことでテキストが送信されます。<br>
                        ・返信には30～60秒ほど掛かります。<br>
                    </p>
                </div>
            </div>
        </q-tab-panel>
    </q-tab-panels>
</template>
<script setup lang="ts">
import { ref, onMounted } from "vue";
import { useQuasar } from "quasar";

const $q = useQuasar();

//タブ設定
const tab = ref<string>('chat');

//ラジオボタン設定
//1ページ目
const radioAgree = ref<string>('');
const radioMC1 = ref<string>('');
const radioMC2 = ref<string>('');
const radioMC3 = ref<string>('');
const radioMC4 = ref<string>('');

//2ページ目
const radioCA = ref<string>('');

//次のページへ
const toExplain = function(){
    tab.value = "explain";
    if(radioAgree.value === 'agree'){
        opinion.value = '異なる';
        agree.value = '反対';
    }else{
        opinion.value = '同じ';
        agree.value = '賛成';
    };
};

const toChat = async function(){
    tab.value = "chat";

    loading.value = true;

    const fn = function() {
        loading.value = false;

        threads.value.push({
            name:'Aさん',
            thread:[`あなたは選択的夫婦別姓に${agree.value}しているようですね。その理由を訊かせて頂けますか？`],
            avatar:'https://cdn.quasar.dev/img/avatar2.jpg',
            sent: false,
        });
    };
    const tm = 2000;
    setTimeout(fn,tm);
};

//賛成・反対系
const opinion = ref<string>('同じ');
const agree = ref<string>('賛成');

//GPT周りの変数
const message = ref<Array<string>>(['']);
const loading = ref<boolean>(false);
const threads = ref<Array<any>>([

]);

//GPTメッセージ送信時の処理
async function sendGPTmessage(){

    loading.value = true;

    // 結果を挿入
    threads.value.push({
        name:'あなた',
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

    const promise = await fetch("https://script.google.com/macros/s/AKfycbwYbGf6qf4CfZ_hd0gbQpBrKJfi59iEOi9BHNFhEh_-NIjwpY7FjTQ3wErlFMZqePWL/exec", requestOptions);
    const data = await promise.json();

    // レスポンスを挿入
    threads.value.push({
        name:'Aさん',
        thread:[data.res],
        avatar:'https://cdn.quasar.dev/img/avatar2.jpg',
        sent:false,
    })

    loading.value = false;
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