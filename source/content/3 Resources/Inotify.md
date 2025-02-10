---
created: 20220627-1001
tags:
  - Resources/http
  - Resources/monitoring
---

# Inotify

### Monitorea eventos en archivos

es un módulo del kernel y se instala un api para usarlo

	inotifywait -m /path/to/folder/

Podés usar cosas útiles como notificarte por mail los cambios

	inotifywait -r -m /path/to/folder/ -e modify | \
	 while read path action file; do echo \
	 "Change detected date $(date) in ${path} action ${action} in file ${file}" \
	| mail -s "Modification detected, check ASAP" emailsample@example.com; done

Podés guardar un log en un archivo con los cambios

	inotifywait -r -m /home/bob/sandbox/ -e modify | \
	 while read path action file;do echo \
	 "Change detected date $(date) in ${path} action ${action} in file ${file}" \
	 > inotifyhistory done

---
# References
[Monitorizando modificaciones en el sistema de ficheros](https://www.elarraydejota.com/inotify-monitorizando-modificaciones-en-el-sistema-de-ficheros/)
