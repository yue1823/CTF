|Payload type|
|----|
|Simple list|
|Runtime file|
|Custom iterator|
|Charcter suvstitution|
|Recursive grep|
|lllegal Unicode|
|Character blocks|
|Number|
|Datas|
|Brute Force|
|Null Payloads|
|Character frobber|
|Username generator|
|ECB block shuffler|

# Simpple list
`最基本的，直接手動加`

# Runtime file
`匯入字典檔案`

# Custom iterator
`不同payload的組合` -> `payload 1 : 1,3` `payload 2 : a,b` `payload 3 : ss,gl`

|結果 |= payload 1 + payload 2 + payload 3|
|---|---|
||1ass|
||3ass|
||1bss|
||3bss|
||1agl|
||3agl|
||1bgl|
||3bgl|

# Character substitution
`payload list 中的字元替換` -> `a>2` `b>5` `c>0` -> `abcd`

|結果 |
|---|
|abcd|
|2bcd|
|a5cd|
|ab0d|
|a50d|
|250d|

# Recursive grep
不會
# lllegal Unicode
same
# Character blocks
`插入N個字元，常用於測試overflow`
# Number

# Datas

# Brute Force 

# Null Payloads
# Character frobber
# Username generator
# ECB block shuffler


