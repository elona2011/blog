title: KPI
date: 2015-12-11 22:39:56
tags:
  - javascript
  - gulp
categories:
  - js
---

# 雪碧图

使用gulp生成sprites图片和样式表
http://www.w3ctrain.com/2015/12/09/generating-sprites-with-gulp/

# handlebars
预编译模板

function aaa(o1, o2, o3, o4, e1, e2){
    var best_result;
    var result = [];

    best_result = (o1 + o2 + o3 + o4 + e1 + e2) / 6 * 0.98;
    <!-- console.log(best_result); -->

    for(var i = 0; i < arguments.length; i++){
        if(arguments[i] === best_result){
            result[i] = 0;
        }
        else if(arguments[i] > best_result){
            result[i] = (arguments[i] - best_result) / best_result * 100;
        }
        else{
            result[i] = (best_result - arguments[i]) / best_result * 50 ;
        }
        <!-- console.log(result[i]); -->
    }

    if(Math.min(result[0], result[1], result[2], result[3]) < Math.min(result[4], result[5])){
        return true;
    }
    else{
        return false;
    }
}

function b(){
    out_i:
    for(var i = 2800000; i < 4300000; i+=10000){
        console.log('i='+i);
        for(var j = 2800000; j < 4300000; j+=10000){
            for(var k = 2800000; k < 4300000; k+=10000){
                for(var u = 2800000; u < 4300000; u+=10000){
                    outer:
                    for(var v = 2800000; v < 4300000; v+=10000){
                        for(var w = 2800000; w < 4300000; w+=10000){
                            if(!aaa(i,j,k,u,v,w)){
                                <!-- console.log('w='+w+'v='+v+'u='+u+'k='+k+'j='+j+'i='+i); -->
                                break outer;
                            }
                            if(v === 4300000 && w === 4300000){
                                console.log('win:'+i+','+j+','+k+','+u);
                                break out_i;
                            }
                        }
                    }
                }
            }
        }
    }
}
