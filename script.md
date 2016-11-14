# Script

Voici un script que j'utilise et que je modifie frequenment pour la recherche de IOC
(Indicator Of Compromise). Oui, il sort des *faux positif* mais il c'est un outil qu'on
ne peut ignorer dans la recherche.

Voir scan.sh

Voici aussi des notes que j'ai pris au courant de mes experiences.

Malware detect and analysis.

- File modified in the last 7 days;
`find /home/mywebsite -type f -ctime -7`

- PHP file modified in the last 30 days:
`find /home/mywebsite -type f -name "*.php" -ctime -30`

- Finding base64 coded text, look for (php):
`base64_decode
gzinflate(base64_decode
eval(gzinflate(base64_decode
eval(base64_decode`

- Finding backdoors code, look for (php):
`phpinfo
system
php_uname
chmod
fopen
flclose
readfile
edoced_46esab
passthru`

- Look for `<script>` tags

- Simple usefull grep:
`grep -Rn “shell_exec *(” /var/www
grep -Rn “include *(” /var/www
grep -Rn “require *(” /var/www
grep -Rn “include_once *(” /var/www
grep -Rn “require_once *(” /var/www
grep -Rn “shell_exec *(” /var/www
grep -Rn “base64_decode *(” /var/www
grep -Rn “phpinfo *(” /var/www
grep -Rn “system *(” /var/www
grep -Rn “php_uname *(” /var/www
grep -Rn “chmod *(” /var/www
grep -Rn “fopen *(” /var/www
grep -Rn “fclose *(” /var/www
grep -Rn “readfile *(” /var/www
grep -Rn “edoced_46esab *(” /var/www
grep -Rn “eval *(” /var/www
grep -Rn “passthru *(” /var/www

grep -RPn “(passthru|shell_exec|system|phpinfo|base64_decode|chmod|mkdir|fopen|fclose|readfile|php_uname|eval|tcpflood|udpflood|edoced_46esab) *\(” /var/www

grep -RPl --include=*.{php,txt,asp} "(passthru|shell_exec|system|phpinfo|base64_decode|chmod|mkdir|fopen|fclose|readfile) *\(" /var/www/`
