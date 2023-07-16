# Burpsuite 分為4種攻擊方法

|攻擊方法|
|----|
|Sniper|
|Battering ram
Pitchfork
Cluster bommb

# Sniper
`不管變數幾個，也是payload list中逐一替換` -> payload list -> `22,12,45,23` , 2個變數`admin` `password`

|admin|password|
|----|---|
|22|NULL|       //##第一次
|12|NULL|       //##第二次
|45|NULL|       //##第三次
|23|NULL|  #
|22|22|    #
|22|12|    # 
...        #

# Battering ram 
`把所有變數的值一起換` -> 2個變數 ， 同樣payload 

|admin|password|
|----|---|
|22|22|       //##第一次
|12|12|       //##第二次
|45|45|       //##第三次
|23|23|  #

# Pitchfork 
`每一個變數都要有自己的payload list` -> 兩個變數就要兩個list -> `admin`:`list 1` `password`:`list 2`

|admin|password|
|----|---|
|list 1 [1] |list 2 [1] |       //##第一次
|list 1 [2] |list 2 [2] |       //##第二次
|list 1 [3] |list 2 [3] |       //##第三次
|list 1 [4] |list 2 [4] |  #

### #注意list中的個數要一樣

#Cluster bomb 
`每一個變數都要有自己的payload list,但是逐一試試` -> `admin`:`list 1` `password`:`list 2`

|admin|password|
|----|---|
|list 1 [1] |list 2 [1] |       //##第一次
|list 1 [1] |list 2 [2] |       //##第二次
|list 1 [1] |list 2 [3] |       //##第三次
|list 1 [1] |list 2 [4] |  #
|list 1 [2] |list 2 [1] |       //##
|list 1 [2] |list 2 [2] |       //##
|list 1 [2] |list 2 [3] |       //##
|list 1 [2] |list 2 [4] |
|...||
