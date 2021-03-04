# 6장 집계 프레임워크

## 집계 프레임워크 개요

<img alt="pipeline" src="./img/pipeline.png"/>

### 파이프라인이란

> 컴퓨터 과학에서 파이프라인(영어: pipeline)은 한 데이터 처리 단계의 출력이 다음 단계의 입력으로 이어지는 형태로 연결된 구조를 가리킨다. 이렇게 연결된 데이터 처리 단계는 한 여러 단계가 서로 동시에, 또는 병렬적으로 수행될 수 있어 효율성의 향상을 꾀할 수 있다. 각 단계 사이의 입출력을 중계하기 위해 버퍼가 사용될 수 있다.

출처 : [위키백과](https://ko.wikipedia.org/wiki/%ED%8C%8C%EC%9D%B4%ED%94%84%EB%9D%BC%EC%9D%B8_(%EC%BB%B4%ED%93%A8%ED%8C%85))

<iframe width="560" height="315" src="https://www.youtube.com/embed/_OGiqCw-J_U?start=28" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### 파이프라인 작업
* `$project` – select, reshape data
* `$match` – filter data
* `$group` – aggregate data
* `$sort` – sorts data
* `$skip` – skips data
* `$limit` – limit data
* `$unwind` – normalizes data
* `$convert` - document 필드 타입 변경하는 operator (from 4.x) 

## 참고자료
* https://www.codeproject.com/Articles/1149682/Aggregation-in-MongoDB
* https://github.com/mongodb/mongo/tree/master/src/mongo/shell