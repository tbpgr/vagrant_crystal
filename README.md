## 概要
Crystal環境構築用Vagrantflie

## 利用手順
### VMの起動
```bash
$ vagrant up --provider virtualbox
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Importing base box 'AntonioMeireles/coreos-stable'...
# 中略
==> default: Download complete
==> default: Status: Downloaded newer image for manastech/crystal:latest

# ssh 接続の確認
$ vagrant ssh
# 中略
CoreOS stable (766.3.0)
core@localhost ~ $ docker --version
Docker version 1.7.1, build 2c2c52b-dirty
```

### Crystalコンテナの実行
```bash
$ docker run -it manastech/crystal
root@c383cdca3bec:/opt/crystal# crystal --version
Crystal 0.7.7 [170f859] (Sat Sep  5 03:00:48 UTC 2015)
```

### FizzBuzzしてみる
```bash
root@c383cdca3bec:/opt/crystal# cat << EOS > fizzbuzz.cr
> def fizzbuzz(limit)
>   (1..limit).each do |e|
>     print case
>     when e % 15 == 0 then "FizzBuzz"
>     when e % 5 == 0 then "Buzz"
>     when e % 3 == 0 then "Fizz"
>     else e.to_s
>     end
>   end
> end
>
> fizzbuzz(100)
> EOS
root@c383cdca3bec:/opt/crystal# crystal fizzbuzz.cr
12Fizz4BuzzFizz78FizzBuzz11Fizz1314FizzBuzz1617Fizz19BuzzFizz2223FizzBuzz26Fizz2829FizzBuzz3132Fizz34BuzzFizz3738FizzBuzz41Fizz4344FizzBuzz4647Fizz49BuzzFizz5253FizzBuzz56Fizz5859FizzBuzz6162Fizz64BuzzFizz6768FizzBuzz71Fizz7374FizzBuzz7677Fizz79BuzzFizz8283FizzBuzz86Fizz8889FizzBuzz9192Fizz94BuzzFizz9798FizzBuzz
```
