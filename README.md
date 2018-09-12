# webpack_cli
cliѧϰ
һ��
1.npm install --global vue-cli �� cnpm install --global vue-cli ��ȫ�ְ�װvue-cli��

2.vue init webpack webpack-vue-router-mx �� vue init webpack-simple webpack-vue-router-mx������һ������webpackģ�������Ŀ=>webpack-vue-router-mx:�ļ�����,�����ļ���ֻ����Сд��ĸ��

3.npm install �� cnpm i �����ػ���node��һЩ�ļ���

4.cd webpack-router-mx���ڴ��ļ�����ִ�����

5.npm run dev ��vue�Զ�����������������˴�vue��Ŀ��

6.�˽�Ŀ¼�ṹ��
  build	��Ŀ����(webpack)��ش���
    config	����Ŀ¼�������˿ںŵȡ����ǳ�ѧ����ʹ��Ĭ�ϵġ�
    node_modules	npm ���ص���Ŀ����ģ��
  src	����������Ҫ������Ŀ¼��������Ҫ�������鶼�����Ŀ¼���������˼���Ŀ¼���ļ���
    assets: ����һЩͼƬ����logo�ȡ�
    components: Ŀ¼�������һ������ļ������Բ��á�
  App.vue: ��Ŀ����ļ�������Ҳ����ֱ�ӽ����д�������ʹ�� components Ŀ¼��
  main.js: ��Ŀ�ĺ����ļ���
  static	��̬��ԴĿ¼����ͼƬ������ȡ�
  test	��ʼ����Ŀ¼����ɾ��
  .xxxx�ļ�	��Щ��һЩ�����ļ��������﷨���ã�git���õȡ�
  index.html	��ҳ����ļ�����������һЩ meta ��Ϣ��ͳ�ƴ���ɶ�ġ�
  package.json	��Ŀ�����ļ���
  README.md	��Ŀ��˵���ĵ���markdown ��ʽ

7.��ѧ�߿��Գ����޸�src�ļ����µ��ļ�
  ��app.vue template�� : 
    <h2 :title="obj.title">{{obj.name || '��ȥ�����ǳ�'}}</h2>
    <h2 @click="fn">{{ '1111'  &&  msg }}</h2>
      ��·���ʽ��
        || : ǰΪfalse����Ϊtrue => true��ǰΪtrue����Ϊtrue/false => true��ǰ���Ϊfalse => false��
        && : ǰΪfalse����Ϊtrue/false => false��ǰΪtrue����Ϊfalse => false��ǰ���Ϊtrue => true
  ���������src�µ�components�д���js�ļ����������������ݣ����£�
    <template>
	    <div class="todoList">
		    mx
	    </div>
    </template>
    <script>
    export default {
	    name:'todoList',
	    data(){
		    return {
			    name : 'wyq'
		    }
	    }
    }
    </script>
  ��app.vue script�� :
    // ����todoList���
    import todoList from './components/todoList.vue'
    export default {
      // .vue�ļ������
      // �������ܶ� ͨ��name�ֶ�ȥ�������������
      name: 'app',
      data () {
        return {
          msg: 'Welcome to Your Vue.js App',
          obj : {
            name:''
          }
        }
      },
      methods:{
        fn (){
        this.obj.name = 'wyq'
        }
      },
      components:{
        todoList
      }
    }

8.webpack.config.js��һЩ���õ����飺
  module.exports = {
    entry: './src/main.js',
    output: {
      // __dirname + '/public'֮ǰ��д��
      // path.resolve(__dirname, './dist'),��������÷���һ����
      path: path.resolve(__dirname, './dist'),
      //  publicPath: ����˼�����һ��������ַ�����ڴ���̬��Դ�����õ�ַ���⣬����ͼƬ�ĵ�ַ·�����⡣
      //  /dist/ ֮ǰ����� �������Ǳ������б�����
      // publicPath: './',
      publicPath: '/dist/',
      filename: 'build.js'
      },
      // ���飺https://segmentfault.com/a/1190000013176083?utm_source=tag-newest
      resolve: {
        alias: {
          'vue$': 'vue/dist/vue.esm.js'
        },
        // �ڵ������û���ļ���׺ʱ��webpack���Զ����Ϻ�׺ȥ���Է����ļ��Ƿ���ڡ�
        extensions: ['*', '.js', '.vue', '.json']
      },
      // ���飺https://www.jianshu.com/p/c2dd1c195462
      devServer: {
        //��ʹ�� html5 history api,��������Ӧ404ʱ����index.html����Ҫ�����ù��ܽ�����������
        historyApiFallback: true,
        noInfo: true,
        overlay: true
      },
      // ���ڻ������ж� => �������� �� ��������
      if (process.env.NODE_ENV === 'production'){}
  }
  
����û��simple��cli
1.�����ļ���vue-cli

2.���ն˵�vue-cli�ļ�����
  �������vue init webpack webpack-router-study
  ����ʾ���ã�������ɺ���vue-cli�ļ����л��Զ������ļ���webpack-router-study
  ���ն����� cd webpack-router-study�л�����ǰ�ļ����£��������npm run dev
  ����һ���˿ں�8080�ĵ�ַ��Ϊ�ɹ���

3.��Visual Studio code��webpack-router-study�ļ��У����ļ����д���build��config��node_modules��src��static��.babelrc��.editorconfig��.gitignore��.postcssrc.js��.index.html��package-lock.json��package.json��README.md�ļ�
���ǿɲ������ļ���Ϊsrc�ļ��С�

4.��src�ļ����У�asset�ļ������ڴ���ͼƬ����Դ��components���ڴ洢�����Զ���������router�ļ����д�ŵ�index.js���ڵ�����������Դ������ļ��е�@����build�ļ�����webpack.base.conf.js�ļ���resolve���õľ���·����������·�ɣ�App.vue�ļ���Ψһ�ĳ����ļ���main.js�ļ�����·����Ϣ��
main.js�ļ����µĸ���ֵ����˼��
Vue.config.productionTip = false//����Ϊ false ����ֹ vue ������ʱ����������ʾ��
// router ������Ҫ Vue.use() => ȫ��ע��
// Ȼ��Ҫ�� new Vue() ȥע��
/* eslint-disable no-new */
new Vue({
  el: '#app',
  router,
  components: { App },
  template: '<App/>'
})

index.js�ļ��µ���˼��
import User from '@/components/User'//������ΪUser�����
Vue.use(Router)//�����һ��ģ�黯������ʹ����������ͨ��vue.use��ȷ�İ�װ·�ɹ��ܣ���vueʵ����ȥע��router

5.router-link�����
  ʹ�� router-link �����������ͨ������ `to` ����ָ�����ӣ� <router-link> Ĭ�ϻᱻ��Ⱦ��һ�� `<a>` ��ǩ

  ���ӣ����ȣ���components�ļ����´���һ��HelloRouter�������index.js �ļ������룬
  ���뷽ʽ��import HelloRouter from '@/components/HelloRouter'
  ��export default new Router��routes������·���������Ϣ��
  {
        path: '/helloRouter',
        name: 'HelloRouter',
        component: HelloRouter
  }
  ��App.vue�ļ��е�template�е�div��д�룺
  <router-link to="/">��ҳ</router-link> //��/�����·����
  <router-link to="/helloRouter">HelloRouter</router-link>
  ����ʵ����ת��

6.route��router
  ���ǿ������κ������ͨ�� this.$router ����·������Ҳ����ͨ�� this.$route ���ʵ�ǰ·��
  ��App.vue���ļ��У�������export default�µ�created���������ڴ�ӡthis.$router��this.$route,����router��·������route�ǵ�ǰ·�ɡ�

7.��̬·��ƥ��
  ·����תЯ��ֵ��
  ��components�ļ����д���User.vue�ļ�
  �ļ��ṹ��
  <template>
    <h1>
        ��ã������˽⶯̬router������
        {{$route.params.id}}
    </h1>
  </template>
  <script>
  export default {
      name:'User'
  }
  </script>
  <style>

  </style>
  ��index.js�ļ�������
  { 
      // ·����תЯ��ֵ
      // ����·�������ȼ������� indexԽС ���ȼ�Խ��
      path: '/user/:id/set/:time', 
      name:'User' ,
      component: User
  }
  ͨ��$route.params.id $route.params.time ���Ի�ȡ��·����תʱЯ����ֵ

7.��Ӧ·�ɲ����ı仯
  ����watch��⣺
  ��App.vue�ļ��µ�export default��д�룺
  // �۲⵱ǰ��̬·�����ݵı��
    watch:{
      // �۲ⷢ���仯��·��
      '$route' (newVal,oldVal){
        // ��·�ɱ仯������Ӧ...
        console.log(newVal)
      }
    }

8.ƥ�����ȼ���ƥ������ȼ��Ͱ���·�ɵĶ���˳��˭�ȶ���ģ�˭�����ȼ�����ߡ�

9.Ƕ��·�ɣ�ʵ�������е�Ӧ�ý��棬ͨ���ɶ��Ƕ�׵������϶��ɡ�ͬ���أ�URL �и��ζ�̬·��Ҳ��ĳ�ֽṹ��ӦǶ�׵ĸ������
  ��components�ļ����´���userInfo.vue�����Password.vue�������userInfo.vue��div��д��<router-view></router-view>�����ڽ���Passwrod.vue�������index.js�ļ������ã�
  {
      path: '/userInfo/',
      name: 'userInfo',
      component: userInfo,
      // Ҫע�⣬�� / ��ͷ��Ƕ��·���ᱻ������·���� �������ֵ�ʹ��Ƕ���������������Ƕ�׵�·����
      children:[
        {
          path:'',
          component:Password
        },
        {
          path:'password',
          name: 'Psaaword',
          component:Password
        }
      ]
  }
  ���У�children��·��ֻд���֣�·��Ϊ�գ�����һ�����������ֱ����ʾ��

10.����·��
  ��App.vue�ļ��µ�div�������д����<router-view></router-view>��������һ��ʱ������ҳ������ʾ�����������ֲ�ͬʱ������Ĭ��default�������ԷŲ�ͬ��·�ɣ��磺
  <router-view></router-view>
  <router-view name='b'></router-view>
  ��index.js �ļ������ã�ע��componentҪ��s����
  // ����·��
    {
      path:'/outputs',
      components:{
        default:userInfo,
        a:User,
        b:HelloRouter
      }
    }

11.���ʽ�ĵ���
  ����push����ֱ����תҳ��
  ��App.vue�ļ��е�ĳ����ǩ��һ������¼�����methods������ã�
  fn(){
      // // �ַ���
      // ע�� ���ǵ��ӵģ������� --error
      // this.$router.push('helloRouter')
      // ����
      // ע�� ��Ҳ�ǵ��ӵģ������� --error
      //this.$router.push({path:'user/9527/set/9527'})
      // ������·��
      //this.$router.push({ name: 'User', params: { id: 123,time:9527 }})
      // ����ѯ��������� /register?plan=private
      //this.$router.push({ path: 'HelloRouter', query: { name: 'name' }})
      // ����һ����¼����ͬ�� history.back()
      this.$router.go(-1)
    }

12.router-link��to�������ã���� <router-link :to="..."> ��ͬ�ڵ��� router.push(...)��
 <router-link :to="{name:'User',params:{id:'123',time:'123'}}">����router-link��to��������</router-link>
  ע�⣺toǰ��һ��Ҫ��ð��

13.�ض���
  ��index.html�ļ������ã�
  // �ض���
    // һ��ŵ�������
    {
      //path:'/sss',
      path:'*',
      redirect:'/HelloRouter'
    }
 ��8080�˿ڸ�·�����벻��ȷ�ĵ�ַʱ���Զ���ת����redirect���涨��ĵ�ַ

14.HTML5 Historyģʽ
  ��export default new Router������mode:'history'��URL ���������� url������ http://yoursite.com/user/id