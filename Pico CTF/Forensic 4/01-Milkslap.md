## Descripción 
[🥛](http://mercury.picoctf.net:16940/)

Hint:
1. Look at the problem category
## Solución 1

Descargamos la imagen y después vamos a necesitar el comando zsteg de ruby para analizar la imagen, la imagen es demasiado pesada, entonces, usamos un comando para aumentar el límite del tamaño de la pila de Ruby y luego utilizamos de nuevo zsteg

```
omarsalazar@DESKTOP-H97NF1C:~$ wget http://mercury.picoctf.net:16940/concat_v.png
omarsalazar@DESKTOP-H97NF1C:~$ ls
concat_v.png
omarsalazar@DESKTOP-H97NF1C:~$ zsteg concat_v.png
/var/lib/gems/3.2.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:303:in `upto': stack level too deep (SystemStackError)
        from /var/lib/gems/3.2.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:303:in `decoded_bytes'
        from /var/lib/gems/3.2.0/gems/zpng-0.4.5/lib/zpng/scan_line/mixins.rb:17:in `prev_scanline_byte'
        from /var/lib/gems/3.2.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:377:in `prev_scanline_byte'
        from /var/lib/gems/3.2.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:319:in `block in decoded_bytes'
        from /var/lib/gems/3.2.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:318:in `upto'
        from /var/lib/gems/3.2.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:318:in `decoded_bytes'
        from /var/lib/gems/3.2.0/gems/zpng-0.4.5/lib/zpng/scan_line/mixins.rb:17:in `prev_scanline_byte'
        from /var/lib/gems/3.2.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:377:in `prev_scanline_byte'
         ... 9483 levels...
        from /var/lib/gems/3.2.0/gems/zsteg-0.2.13/lib/zsteg.rb:26:in `run'
        from /var/lib/gems/3.2.0/gems/zsteg-0.2.13/bin/zsteg:8:in `<top (required)>'
        from /usr/local/bin/zsteg:25:in `load'
        from /usr/local/bin/zsteg:25:in `<main>'

omarsalazar@DESKTOP-H97NF1C:~$ export RUBY_THREAD_VM_STACK_SIZE=5000000
omarsalazar@DESKTOP-H97NF1C:~$ zsteg concat_v.png
imagedata           .. text: "\n\n\n\n\n\n\t\t"
b1,b,lsb,xy         .. text: "picoCTF{imag3_m4n1pul4t10n_sl4p5}\n"
b1,bgr,lsb,xy       .. /var/lib/gems/3.2.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s': stack level too deep (SystemStackError)
        from /var/lib/gems/3.2.0/gems/iostruct-0.5.0/lib/iostruct.rb:180:in `inspect'
        from /var/lib/gems/3.2.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
        from /var/lib/gems/3.2.0/gems/iostruct-0.5.0/lib/iostruct.rb:180:in `inspect'
        from /var/lib/gems/3.2.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
        from /var/lib/gems/3.2.0/gems/iostruct-0.5.0/lib/iostruct.rb:180:in `inspect'
        from /var/lib/gems/3.2.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
        from /var/lib/gems/3.2.0/gems/iostruct-0.5.0/lib/iostruct.rb:180:in `inspect'
        from /var/lib/gems/3.2.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
         ... 48072 levels...
        from /var/lib/gems/3.2.0/gems/zsteg-0.2.13/lib/zsteg.rb:26:in `run'
        from /var/lib/gems/3.2.0/gems/zsteg-0.2.13/bin/zsteg:8:in `<top (required)>'
        from /usr/local/bin/zsteg:25:in `load'
        from /usr/local/bin/zsteg:25:in `<main>'
omarsalazar@DESKTOP-H97NF1C:~$

flag: picoCTF{imag3_m4n1pul4t10n_sl4p5}

```

