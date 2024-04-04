## <p align="center">📆4/4</p>

## Python Dict!

```python
keys = input().split()
values = list(map(float, input().split()))

res = dict(zip(keys, values))
# print(res)
keys, values = zip(*res.items())
# 무려 unzip도 할 수 있다고요?
print(keys, values)

# health mana melee attack_speed magic_resistance
# 573.6 308.8 600 0.625 35.7

#### Zip ####
### key, values를 매치하여 dict로 만들어준다
# {'health': 573.6, 'mana': 308.8, 'melee': 600.0, 'attack_speed': 0.625, 'magic_resistance': 35.7}

#### Unzip ####

# ('health', 'mana', 'melee', 'attack_speed', 'magic_resistance') (573.6, 308.8, 600.0, 0.625, 35.7)


```
