# 변수

반복적으로 사용되는 값을 변수로 지정할 수 있다.
<br>$를 붙여 사용.

    $변수이름: 값;

    $w: 100px;
    $h: 50px;
    $color-primary: #ffffff;

    .box {
        width: $w;
        height: $h;
        background: $color-primary;
    }

### 변수의 유효범위

변수는 선언된 블록 ({}) 안에서만 유효범위를 가진다.

    .box {
        $color: #fff;
        background: $color;
    }

    // Error
    .box2 {
        background: $color;
    }

### 변수 재할당

    $red: #FF0000;
    $blue: #0000FF;

    #color-primary: $blue;
    #color-danger: $red;

    .box {
        color: $color-primary;
        background: $color-danger;
    }

### 전역 설정

' !global ' 플래그를 사용하여 변수의 유효범위를 전역으로 설정할 수 있다.

    .box1 {
        $color: #111 !global;
        background: $color;
    }
    .box2 {
        background: $color;
    }

### 문자 보간

#{} 를 이용해서 코드의 어디든지 변수 값을 넣을 수 있다.

    $family: unquote("Droid+Sans");
    @import url("http://font.googleapis.com/css?family=#{family}");

    =>  @import url("http://font.googleapis.com/css?family=Droid+Sans");

unquote() : 문자에서 따옴표를 제거한다.
