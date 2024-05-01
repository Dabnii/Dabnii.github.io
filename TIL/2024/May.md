## <p align="center">📆5/1</p>

### Python 으로 'the' 찾기,

- 'the' 찾기, 'their,them'등은 제외

```python
sentence = input().split()
# 입력받은 문장을 split

count = 0
for i in sentence:
  if i.strip(',.') == 'the':
  # 각 단어에서 구두점(쉼표, 마침표)를 제거한 후에 그 단어가 "the"인지를 확인
    count += 1
print(count)
```
