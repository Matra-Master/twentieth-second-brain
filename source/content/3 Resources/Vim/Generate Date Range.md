
Ah bueeeno, con esto genero las fechas en un rango. Ido de podeeer

``` vimscript
function! GenerateDateRange(start_date, end_date)
  let start = strptime('%Y%m%d', a:start_date)
  let end = strptime('%Y%m%d', a:end_date)
  let dates = []

  while start >= end
    call add(dates, strftime('%Y%m%d', start))
    let start -= 24 * 60 * 60 " Subtract one day in seconds
  endwhile

  call setline('.', dates)
endfunction
```
