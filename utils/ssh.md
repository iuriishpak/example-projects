## Zkratky

V souboru `~/.ssh/config` mají formát:

```
Host ex

HostName example.com
User user
Port 123
ServerAliveInterval 30
ServerAliveCountMax 120
```

## Generování paru klíčů
Klíč se vším všudy vygenerujeme tímto příkazem:
`ssh-keygen -C 'some comment' -b 2048  -t rsa -f filename`
Budeme ještě dotázani na passphare, důrazně ji doporučuji vyplnit. Také je dobré rozumně popsat komentář.


## Přihlašování na server pomocí klíče
Na serveru vložíme do `~/.ssh/authorized_keys` náš veřejný klíč. Např. tímto příkazem:
```bash
ssh USER@HOST "mkdir -p ~/.ssh"
cat ~/.ssh/id_rsa.pub | ssh USER@HOST "cat >> ~/.ssh/authorized_keys"
```
## Známé servery
Pokud se připojujeme k serveru poprvé, tak se nás SSH zeptá, zda odpovídá fingerprint, což v budoucnu může zabránit MIM útoku. Známe servery vy
~                             