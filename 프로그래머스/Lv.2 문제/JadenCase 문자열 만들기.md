# 📖 프로그래머스 Lv.2
## 📌 문제 정의
JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열입니다.</br>
단, 첫 문자가 알파벳이 아닐 때에는 이어지는 알파벳은 소문자로 쓰면 됩니다. (첫 번째 입출력 예 참고)</br>
문자열 s가 주어졌을 때, s를 JadenCase로 바꾼 문자열을 리턴하는 함수, solution을 완성해주세요.</br>

</br>

### 제한사항
- s는 길이 1 이상 200 이하인 문자열입니다.
- s는 알파벳과 숫자, 공백문자(" ")로 이루어져 있습니다.
  - 숫자는 단어의 첫 문자로만 나옵니다.
  - 숫자로만 이루어진 단어는 없습니다.
  - 공백문자가 연속해서 나올 수 있습니다.


</br>

### 출력

|s	|return|
|---|---|
|"3people unFollowed me"	|"3people Unfollowed Me"|
|"for the last week"	|"For The Last Week"|

</br>


## 📌 나의 풀이
~~~python
def solution(s):
    answer = []
    s = s.lower()
    s = list(s.split(' ')) #단어사이에 공백이 2개이상이면 해당 공백 유지한채로 쪼개야 하니깐
    
    for i in s:
        if i == '': #빈 문자열을 하나의 문자라고 생각하고, answer리스트에 넣기
            answer.append('')
        else:
            answer.append(i[0].upper()+i[1:])

    answer  = ' '.join(answer) #공백 포함 리스트를 합쳐주기
    
    
    
    return answer

~~~
### 💡문제 분석
- 문자열 내에서 띄어쓰기 한 부분도 하나의 문자로 취급해야함 --> 띄어쓰기가 2번 이상 되어 있는 곳이 있을 수 있음
  - 따라서, ('') 빈 문자열도 하나의 문자로 취급되어야 하니깐, s.split(' ') 로 나누기
  - 마지막에 answer 도출시에 ' '.join을 하니깐 일반적인 띄어쓰기 공백을 같이 가져가면서, 빈 문자열(하나의 문자로 취급)의 공백도 같이 고려해줄수 있음 
