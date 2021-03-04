# 6장 집계 프레임워크

## 집계 프레임워크 개요

<img alt="pipeline" src="./img/pipeline.png"/>

기존에 맵-리듀스를 통해 뽑아내던 데이터를 집계 프레임워크를 이용해 쉽게 뽑아낼 수 있다.

### 파이프라인이란

> 컴퓨터 과학에서 파이프라인(영어: pipeline)은 한 데이터 처리 단계의 출력이 다음 단계의 입력으로 이어지는 형태로 연결된 구조를 가리킨다. 이렇게 연결된 데이터 처리 단계는 한 여러 단계가 서로 동시에, 또는 병렬적으로 수행될 수 있어 효율성의 향상을 꾀할 수 있다. 각 단계 사이의 입출력을 중계하기 위해 버퍼가 사용될 수 있다.

출처 : [위키백과](https://ko.wikipedia.org/wiki/%ED%8C%8C%EC%9D%B4%ED%94%84%EB%9D%BC%EC%9D%B8_(%EC%BB%B4%ED%93%A8%ED%8C%85))

#### 예시
``ps -ef | grep java``
`|` 파이프라인 기호 앞의 `ps -ef` 출력이 `grep` 의 입력으로 이어지는 형태

### 집계 파이프라인 연산자 (대표적인 것들 요약)
* `$project` – select, reshape data (sql - select, * -> 출력 필드 명시)
* `$match` – filter data (sql - where)
* `$group` – aggregate data (sql - group by)
* `$sort` – sorts data (sql - order by)
* `$skip` – skips data (sql - offset)
* `$limit` – limit data (sql - limit)
* `$unwind` – normalizes data (sql - join?)
* `$convert` - document 필드 타입 변경하는 연산자 (from 4.x)

비슷한 것 - [과일 선별기 유튜브 영상](https://www.youtube.com/embed/_OGiqCw-J_U?start=28)

## 집계 파이프라인 동작

```javascript
db.products.aggregate([
  {$match: {}}, // 1
  {$group: {}}, // 2
  {$sort: {}} // 3
]);
```

aggregate 에 파라미터로 전달된 배열의 순서대로 동작(1 > 2 > 3) 후 최종 결과가 반환된다.

* 생각해볼 점
1. match > group 순서가 group > match 로 변경되면 ?

## 집계 파이프라인 연산자

책에는 자주 사용되는 10개 소개, 현재 4.4 기준으로 약 20여개의 연산자가 있다. 참고, [Aggregation Pipeline Stages](https://docs.mongodb.com/manual/reference/operator/aggregation-pipeline/#aggregation-pipeline-stages)

제약 사항이 있는데, `$out`, `$merge`, `$geoNear` 연산자는 파이프라인에서 여러번 사용할 수 없다. 나머지는 다 여러번 사용이 가능하다.






## 참고자료
* https://www.codeproject.com/Articles/1149682/Aggregation-in-MongoDB
* https://github.com/mongodb/mongo/tree/master/src/mongo/shell