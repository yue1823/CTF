# Burpsuite 分為4種攻擊方法

|攻擊方法|
|----|
|Sniper|
|Battering ram
Pitchfork
Cluster bommb

# Sniper
`不管變數幾個，也是payload list中逐一替換` -> payload list -> `22,12,45,23` , 2個變數`admin``password`

|admin|password|
|----|---|
|22|NULL|       //##第一次
|12|NULL|       //##第二次
|45|NULL|       //##第三次
|23|NULL|  #
|22|22|    #
|22|12|    # 
...        #
