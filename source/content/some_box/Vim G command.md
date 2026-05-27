20220624-1229
Status: #idea

Tags: [[Vim commands]]

# Vim G command
##### g stands for global
It searches through a file for some pattern and then executes a command OwO

With this one I searched product codes that had a '-' character somewhere in the middle   
and then used a macro to delete the '-'

    g/^[0-9]\+\-[0-9]\+/normal @x

Obtener en todas las líneas el código que empieza con números
hasta que encontrás un ' - '

    g/^[0-9]\+ - 

Obtener en todas las líneas el código que empieza con números o letras
hasta encontrar un ' ' o un '/'

    g/^[0-9a-zA-Z]\+ 
    g/^[0-9a-zA-Z]\+ /
    g/^[0-9a-zA-Z]\+ / s/ //g
    g/^[0-9a-zA-Z]\+ / s/ //
    g/^[0-9a-zA-Z]\+\/
    g/^[0-9a-zA-Z]\+\/ 



---
# References
[Power of g](https://vim.fandom.com/wiki/Power_of_g)