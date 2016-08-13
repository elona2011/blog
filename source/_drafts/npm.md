# node_modules

npm3之后，node_modules改为扁平化module安装。实际效果是：在module不冲突的情况下，安装一个module会把它所有的依赖都安装在项目根node_modules上，而不是以前的树型结构。
http://stackoverflow.com/questions/32951150/why-does-installing-one-npm-package-add-many-subfolders-in-node-modules
