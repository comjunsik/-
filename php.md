# PHP

[ob_start()](#ob_satrt())
[Prepare Statement SELECT](#Prepare_Statement_SELECT_Query)
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