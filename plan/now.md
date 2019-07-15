####目前方案(计划)
#####1 先进性一次加密 ASE(params,下发的key)生成params1
#####2 生成随机randkey
#####2 再进行一次加密 ASE(params1,randkey)
#####3 将randkey 和 加密params2 进行二进制反码传输到客户端操作传输到服务端进行解析