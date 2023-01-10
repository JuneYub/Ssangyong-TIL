## 1. 레이블 활용법

</br>
for문 두개를 활용할 때 if문에서 break을 만든다면.
가장 가까운 반복문만을 탈출한다.

</br>

```
for(;;) { // 첫 번째 for문

    for(;;) { // 두 번째 for문
        if~
        else if~
    }
}
```

따라서 위 예시에서 두 번째 for문의 if문에서 첫 번째 for문까지 멈추고 싶다면 어떻게 해야할까?

</br>

```
label labelTest:
for(;;) { // 첫 번째 for문

    for(;;) { // 두 번째 for문
        if() {
            break labelTest;
        }
        else if~
    }
}
```
label을 활용하여 첫번째 for문에 label을 만들어둠으로써 break label명으로 반복문을 종료시킬 수 있다.