# KluczeSSH

## bezhasłowe logowanie za pomocą kluczy SSH pomiędzy user1 oraz user2 w kali Linux
**user1**
```
ssh-keygen -b 521 -t ecdsa #stworzenie pary kluczy w oparciu o algorytm krzywych eliptycznych, jeżeli chcemy, aby nie pytało nas o hasło nie należy podawać żadnej frazy do klucza(nacisnąć enter bez wpisywania czegokolwiek)
#należy przejść teraz do folderu .ssh w katalogu domowym user1
cd .ssh
ssh-copy-id -i id_ecdsa.pub user1@[adres ip user1] #adres ip można sprawidzić komendą ip addr
ssh-copy-id -i id_ecdsa.pub user2@[adres ip user2]
ssh user1 #za pierwszym razem trzeba będzie podać hasło
exit #zamykamy sesje
```
**user2**
```
ssh-keygen -b 521 -t ecdsa #stworzenie pary kluczy w oparciu o algorytm krzywych eliptycznych
#należy przejść teraz do folderu .ssh w katalogu domowym user2
cd .ssh
ssh-copy-id -i id_ecdsa.pub user2@[adres ip user2]
ssh-copy-id -i id_ecdsa.pub user1@[adres ip user1]
ssh user2
exit
```
Po wykonaniu tych czynność można zalogować się z konta user1 na konto user2 lub odwrotnie bez użycia haseł

