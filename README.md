客户端：
post_request_data = {
        "dev_id":dev_id,
        "map_id":map_id,
        "position_id":position_id,
        "task_id":task_id,
        "position": position,
        "data":data,
        "image":str(img_data_bs64, encoding='ascii')  # bytes -> str, 'ascii' for base64
    }
    
    

服务器端：
response_data = {
                    "err_code": error_code,  # 0 无错误， 其它是错误码
                    "map_id": map_id,
                    "err_desc": err_desc[error_code],  # 错误的描述
                    "status": status,  # 对算法结果的判断，[正常，异常]比如指示灯是否全亮，对于无法给出判断结果的，可不填
                    "dev_id": dev_id,
                    "position_id": position_id,  # 巡检点编号
                    "task_id": task_id,
                    "data": data,
                    "bounding": box_list,  # 算法跑出来的结果
                    "image": img_base64[2:-1]  # 转str后，有两个前缀字符‘b’需要去掉
                }
                
                
    img_path='./20190822_6.jpg'           
    img_data_bs64 = None
    with open(img_path, "rb") as f:
        img_data = f.read()
        img_data = zlib.compress(img_data)
        img_data_bs64 = base64.b64encode(img_data)
        
        
     post_request_data = {
        "dev_id":dev_id,
        "map_id":map_id,
        "position_id":position_id,
        "task_id":task_id,
        "position": position,
        "data":data,
        "image":str(img_data_bs64, encoding='ascii')  # bytes -> str, 'ascii' for base64
    }            
        
