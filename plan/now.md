####目前方案(计划)
####1预备方法
    AES加密方法：
    
    data是需要被加密的 字符串
    key是密钥 16位
    iv是AES加密方法中的偏移向量,需要是 16位

	const aesEncrypt = function (data, key, iv) {
        	var key = CryptoJS.enc.Utf8.parse(key); //为了避免补位，直接用16位的秘钥
        	var iv = CryptoJS.enc.Utf8.parse(iv); //16位初始向量
        	console.log(data);
        	var encrypted = CryptoJS.AES.encrypt(data, key, {
                	iv: iv,
               		mode:CryptoJS.mode.CBC,
                	padding:CryptoJS.pad.Pkcs7,
            	});
        	return encrypted.toString();
    	}

    生成n位随机数方法：
    /**
    * number 意指生成 number位随机数
    /
    function createrandkey(number) {
            var charStr = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789"
            var lencharList = charStr.length
            var resRandKey=""
            for (var i = 0;  i< number; i += 1)
                randnum = Math.random() * lencharList,
                randnum = Math.floor(randnum),
                resRandKey += charStr.charAt(randnum);
            return resRandKey
    }
#
### 整个过程有三个关键参数
##### key      : 双方约定
##### iv       : 双方约定
##### randkey  : 前端生成( createrandkey(16)即可生成 )

####1 第一次加密：使用 key 和 iv进行第一次AES加密
    params是原始的json参数,比如是 要传的手机号
    var params={"mobile":"13666666666"}
    var params1 = aesEncrypt(JSON.stringify(params),key,iv)
####2 第二次加密：使用 randkey 和 iv 进行第二次 AES加密
    var params2 = aesEncrypt(params1,randkey,iv)

####3 将randkey 和 加密params2 传输到服务端
    即传两个参数即可
        {
            randkey:randkey,
            params:params2
        }
###后端操作：
    使用randkey 解密出 prams1
    使用key     解密出 params
