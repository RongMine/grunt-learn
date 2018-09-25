#### [grunt-learn](https://github.com/RongMine/grunt-learn "地址")

// module.exports = function(grunt) {//wrapper函数
//     //注册任务
//     /*
//     * grunt.registerTask(taskName, [description, ] taskList/callback)
//     * taskName:任务名称
//     * description：任务描述，可选
//     * taskList:任务数组，在执行当前任务前需要执行的任务列表,顺序执行
//     */
//
//     // Project configuration.
//     grunt.initConfig({ //各个任务的配置都在initConfig里
//         // 任意数据。
//         pkg: grunt.file.readJSON('package.json'),//--------导入外部数据
//         my_property: 'whatever',
//
//         uglify: {//grunt concat  遍历包含的所有目标并依次处理
//             options: {
//                 // 这里是任务级的Options，覆盖默认值
//                 banner: '/*! <%= pkg.name %> */\n'//--------使用外部数据
//             },
//
//             // 这里是concat任务的配置信息。
//            inner:{
//                //grunt concat:inner 执行特定目标
//
//                //格式一
//                src: ['src/bb.js', 'src/bbb.js'],//源文件
//                dest: 'dest/b.js',//目标文件
//                //格式二
//                files: {
//                    'dest/b.js': ['src/bb.js', 'src/bbb.js'],
//                    'dest/b1.js': ['src/bb1.js', 'src/bbb1.js'],
//                },
//                //格式三：
//                //files: [
//                //    {src: ['src/aa.js', 'src/aaa.js'], dest: 'dest/a.js'},
//                //    {src: ['src/aa1.js', 'src/aaa1.js'], dest: 'dest/a1.js'},
//                //],
//
//                options: {
//                    // 单个目标的options,不需要可忽略
//                },
//            }
//         },
//         //...
//     });
//
// };

module.exports = function(grunt){
    grunt.registerTask('test1',function(){
        //var done = this.async();//处理异步
        console.log(1);
        setTimeout(function(){
            console.log("end");
            //done();//完成
        },6000);
    });
    grunt.registerTask('test2',function(){
        console.log(2);
    })
    grunt.registerTask('test3',function(){
        console.log(3);
    });
    grunt.registerTask('test4',function(){
        console.log(4);
    })
    grunt.registerTask('test','aa',['test1','test2','test3','test4'])

    grunt.registerTask('n1','bb',function(){
        grunt.task.run(['test1','test2','test3','test4']);
    })
}