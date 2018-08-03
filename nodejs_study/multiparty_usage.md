node.js 서버로 post request를 보냈다고 가정하자.
파이썬 코드와 자바스크립트 코드는 다음과 같다.
// request_test.py
import requests

file_dict = {'transfer_file' : open('number_list.txt', 'rb')}

r = requests.post('http://127.0.0.1:8250/data', files=file_dict)

print(r.status_code)
// node_test.js

router.post('/data', function(req, res, next)
{
    console.log(req.headers,"HEADERS...")
    res.send("complete...")
}
// number_list.txt
1
2
3
4
5
6
7
8
9
10

python request_test.py 를 입력하면 다음과 같은 결과가 node_test.js에 나타난다.

이 때, 
해당 데이터를 parsing 하고 싶으면 다음과 같이 하면 된다.

커맨드라인에 
npm install multiparty을 입력해서 패키지를 설치한다.
let multiparty = require('multiparty');

router.post('/data', function(req, res, next)
{
    let form = new multiparty.Form();
    form.on('part', function(part)
    {
        let filename;
        let size;
        let full_data = '';
        if(part.filename)
        {
            filename    = part.filename;
            size        = part.byteCount;
            part.on('data', function(data)
            {
                full_data += data;
            });
            part.on('end', function()
            {
                console.log(full_data);
            });
        }
    }
    //console.log(req.headers,"HEADERS...")
    form.parse(req)
    res.send("complete...")
}
다시 request_test.py를 실행해보자.

그러면, 
위에 number_list.txt가 그대로 출력되는걸 확인 할 수 있다.
[출처] nodejs에서 multipart/form-data parsing하기|작성자 헬로우잼
