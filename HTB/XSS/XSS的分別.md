# XSS

是主要在網站上用payload 的攻擊

stored persistent XSS 

(儲存型XSS)會存在網站

Reflrcted(NON-persistent XSS)

(反射型XSS)不會存在網站，但會到達後端

上面都可以用<script>的


DOM-based XSS

這個不可以，因為innerHTML不允許script 
-> 可以用`<img src='' onerror=alert(doucment.cookie)>`代替

