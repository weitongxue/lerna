## lerna探索
  + 初始化项目
    `lerna init --independent` *（Independent：单独发版模式，更加灵活）*

    `lerna create module_A` 创建子模块

  + 安装依赖
    - 公共依赖，所有模块都会依赖的（以lodash为例）  
    `lerna add lodash`

    - 各模块单独安装的依赖，（例如：module_A 依赖 vue；module_B 依赖weitongxue-utils）  

      `lerna add vue --scope=module_a` / `lerna add weitongxue-utils --scope=module_b`  

      *(--scope的值，对应模块里package.json里的name)*


  + 注意

    使用`lerna add lodash`安装了全局依赖，上面 moduleA 和 moduleB 都依赖了 lodash，且在各自的node_modules 里都有副本，这其实很浪费空间。  
    
    可以使用`lerna bootstrap --hoist`进行依赖的抽离，从而都会抽离到最外层的node_modules里，但是各自模块里的package.json信息依旧是保留的


  + 更新公共依赖
    
    借助*lerna-update-wizard*这个包  

    `npm install --save-dev lerna-update-wizard`  

    然后在根目录执行 `./node_modules/.bin/lernaupdate` 就可以选择更新了
