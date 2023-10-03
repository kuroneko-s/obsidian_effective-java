try-finally를 사용하면 Exception 로그가 잡아먹는 문제가 발생함.
그런데 try-with-resource를 사용하면 발생한 로그들은 모두 보여지며 Suppressed로 보여지게 됨.

이외 try-finally가 가지고 있던 문제들은 모두 해결될 수 있으며, 보여지는 코드들도 깔끔하게 보이기 때문에 사용을 안하는게 더 손해가 많음.

try-with-resource도 내부적으로는 try-catch를 중첩해서 사용하게 되는데, 애초에 처음부터 try-catch를 사용했을 때와 동일하게 사용하게 되니깐 간략하게 try-resource를 사용하는게 좋은듯.