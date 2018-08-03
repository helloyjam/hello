# nodejs 프로세스에서 사용가능한 메모리 증가시키기

nodejs는 기본 메모리 제한으로 프로그램을 실행한다.

많은 데이터를 변수에 저장하는 어플리케이션을 실행하려면, 메모리 할당 문제로 인해 nodejs 프로세스가 종료된다.

node의 메모리 제한을 증가시키는 방법을 알아보자.

```js
// memory_test.js
const v9 = require('v8')

console.log(v8.getHeapStatistics())

const totalHeapSize = v8.getHeapStatistics().total_available_size
let totalHeapSizeInGB = (totalHeapSize / 1024 /1024 / 1024).toFixed(2)

console.log(`Total heap size (bytes) ${totalHeapSize}, (GB ~${totalHeapSizeInGB})`)
```

위와 같이 코드를 작성하고 
node memory_test.js 로 실행하면 다음과 같은 화면이 나타난다.

total_available_size를 GB로 변환하면 1.39GB까지 사용가능한 것을 알 수 있다.


node --max-old-space-size=8192 memory_test.js 로 실행하면 다음과 같은 화면이 나타난다.
![WOWS1](./images/memory increase nodejs.png)

기본적으로 실행했을 때와 달리 total heap size가 8GB로 증가 했음을 알 수 있다.

실제 보유하고 있는 물리적 메모리의 크기에 따라 메모리 제한을 정할 수 있다.
