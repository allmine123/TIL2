# Rails 환경설정

- VirtualBox 5.1.30 -window hosts
  -  (https://www.virtualbox.org/wiki/Download_Old_Builds_5_1)
- vagrant_1.9.5.msi
  -  (https://releases.hashicorp.com/vagrant/1.9.5/)
- git bash



1. gitbash

   c/users/student에 `mkdir vagrant`

   `cd vagrant`

   `vagrant init`

   

2. vagrantFile수정

```
 Vagrant::DEFAULT_SERVER_URL.replace('http://vagrantcloud.com')
 Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
 config.vm.box = "ubuntu/xenial64"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  config.vm.network "forwarded_port", guest: 3000, host: 3000
```

3. `vagrant up` 하면 설치
4. 설치완료후 `vagrant ssh` 를 치면 ubuntu에 접속가능

- `vagrant up`컴퓨터 켜기, `vagrant ssh` 컴퓨터 접속,  `vagrant halt` 컴퓨터끄기

`cd /`

`cd vagrant`



5. https://gorails.com/setup/ubuntu/16.04 참고하여 Rails 설치
6. `cd /vagrant`
7. `ralis new 프로젝트이름`
8. `cd 프로젝트이름`
9. `rails s`레일즈 서버 실행

