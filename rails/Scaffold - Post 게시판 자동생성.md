### Scaffold - Post 게시판 자동생성

```console
$ rails new scaffold_test
$ cd scaffold_test
$ rails g scaffold post title:string content:text
$ rake db:migrate
$ rails s -b 0.0.0.0
```