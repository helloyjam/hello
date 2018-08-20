# mongodb conf 옵션 

mongodb에서 mongodb.conf 파일을 작성할 때 자주 쓰는 옵션은 다음과 같다.

'''
fork=<boolean>  // default=False
mongos(MongoDB Shard) 또는 mongod(MongoDB system)를 daemon 모드로 돌릴 수 있도록 가능하게 해주는 옵션이다.
기본적으로, mongos 또는 mongod는 daemon으로 돌리지 않게 되어 있다.


pidFilePath=<string>
프로세스 ID를 저장하고 있는 파일경로를 지정해준다.
/home/share/mongodb.pid 로 입력하면 해당 경로에 생성된 파일은 pid값만 가지고 있다.


logAppend=<boolean>
true값이면 mongos 또는 mongod가 재시작될때 이미 존재하는 로그파일의 끝단에 로그를 이어붙인다.
이 옵션이 없다면 mongod는 존재하는 log파일을 백업하고 새로운 log 파일을 만든다.

logpath=<string>
해당 경로에는 로그가 저장되는 경로이다.

dbpath=<string>
디폴트값은 리눅스(또는 macOS)에서 /data/db이다.
윈도우에서는 \data\db이다.
해당 경로는 mongod 인스턴스가 데이터를 저장하는 폴더이다.

package management system을 사용해서 mongodb를 설치했다면 /etc/mongod.conf 파일을 확인할 수 있따.
또한 이 dbpath는 mongod에 한해서만 사용이 가능하다.


directoryPerDB=<boolean>
true 값이면 mongodb는 각 데이터베이스에 데이터를 저장하기 위해서 별도의 디렉터리를 사용한다.
디렉터리는 dbpath 디렉터리 아래에 위치한다.
그리고 각 서브디렉터리 네임은 데이터베이스 네임에 똑같이 대응된다.
데이터베이스 네임이 dbman 이면 서브디렉터리 네임도 dbman이다.

port=<integer>
'''
additional...

verbose=<boolean>
maxConns=<integer>
rest=<boolean>
noauth=<boolean>
oplogSize=<integer>
