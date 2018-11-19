# PHP

[ob_start()](#ob_satrt())
[Prepare Statement SELECT](#Prepare_Statement_SELECT_Query)
[PHP 세션 공유 방법](#PHP_세션_공유)

# ob_start()
출력 버퍼링은 출력물이 php에 파싱되어 echo나 print에 의해 브라우저로 출력되는 방법이 일반적인데, 필요에 의해 출력 결과물을 바로 브라우저로 보내지 않고, 내용물을 잠깐 동안 버퍼에 보관해 두었다가 출력이 필요할 곳에 이를 사용할 수 있습니다.

이를 사용하기 위애서는 ob_start()함수를 호출하고, ob_end_flush로 버퍼링을 비워주면 되는데, 여기서 **비운다는 의미**는 <u>버퍼에 저장되어 있는 내용을 브라우저로 출력하고, 버퍼를 비운다는 뜻</u>입니다.

예제들 : http://blog.habonyphp.com/entry/php-%EC%B6%9C%EB%A0%A5-%EB%B2%84%ED%8D%BC-flush-%ED%95%A8%EC%88%98#.W94hRJMzaUk

# Prepare_Statement_SELECT_Query
```php
$stmt=$connect->prepare("SELECT userID, userPw FROM user WHERE userID=?");
//$stmt->set_charset("utf8");
$stmt->bind_param('s', $userID);
$stmt->execute();
//$stmt->bind_result($ruserID, $ruserPw);
$result=$stmt->get_result();
//$result=mysqli_query($query, $connect);
//$member=mysqli_fetch_array($result);

while ($date=$result->fetch_assoc()){
    echo $date[userID];
}
```
Prepare Statement를 사용하면 대부분의 SQL 인젝션 공격을 막을 수 있다.

# PHP_세션_공유
1. NFS, Samba
특정 서버의 디렉토리를 다수의 웹서버에서 Network를 통해 공유하는 것이다.
그럼 한곳의 디렉토리에 모든 세션 파일이 존재할 것이고 문제는 해결 된다.
그렇지만 NFS나 Samba는 Wirte 효율성이 상당이 떨어지는 데몬이다.
세션은 그 특성상 read/write가 매우 빈번히 일어나기 때문에 효율성 면에서는 좋지 않다.

2. DBMS
세션 데이터를 DBMS와 연동하여 DB에 저장하는 방식이다. 보편적으로 주로 사용되는 방법이지만, 접속자가 매운 많은 환경에서는 DB 서버에 부하가 늘어날 수 밖에 없는 구조이다.
또한 DBMS에서 생기는 lock도 무시못할 변수로 떠오를 수 있다.
![image](https://user-images.githubusercontent.com/41488792/48704348-a1676900-ec39-11e8-8e8e-75389c93a69a.png)
![image](https://user-images.githubusercontent.com/41488792/48704449-ea1f2200-ec39-11e8-918a-3a874cdd157a.png)
DBMS Lock에 대해 : http://wiki.gurubee.net/display/STUDY/1.Lock

3. Daemon
말 그대로 데몬을 이용하여 세션을 공유하는 방식이다.
세션서버를 따로 구축하기에 제일 적절한 방법?

sharedance 데몬 설치 방법 : http://jissp.com/board/view/22/44