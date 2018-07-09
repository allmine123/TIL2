# Ruby

### 0. 개요

1. 루비는 순수 객체 지향 언어이다.
2. 모든 것이 객체
3. Ruby on Rails 프레임 워크 등장으로 유명



### 1. puts vs. print

```ruby
3.times{print "hello"} # => hellohellohello
3.times{puts "hello"} # => hello
					#	 hello
					#	 hello 
```

> puts 는 개행문자(/n) 포함



### 2. p vs. puts

```ruby
string = "hello"
puts string # hello => nil
p string # "hello" => "hello"
```



### 3. Naming conventions

- 변수
  - snake_case
- 상수
  - CONSTANT
- 클래스
  - CamelCase



### 4. pry

- 설치
  - `gem install pry` 
- 실행
  - `pry`



### 5. Inline statement

```ruby
# if 문

puts "a=0" if a == 0 # "a=0"
puts "a=0" if a == 0 # 출력 안됨

# while 문
c = 0
rusult = c += 2 while c < 50
puts result # 50
    
puts "hi" if 0 #hi
#0은 true
 

```



> false / nil 을 제외한 모두는 true



### 6. case

```ruby
case name
    when "Son" then puts "hi Son"
    when "tak" then puts "hi tak"
    else puts "hi"
    end
```



### 7. method

- 대부분의 언어
  - 클래스 밖 : function
  - 클래스 안 : method
- 루비에서는 모든 function은 method

```ruby
# 루비에서의 method 선언
def simple
 	puts"simple!!"
end  

#루비에서의 method는 괄호를 명시적으로 적어 줄 수도 있습니다.
def simple()
 	puts"simple!!"
end 
```

- return 키워드는 선택적으로 사용

```ruby
def add (a, b)
   return a + b
end  

add 1,2 #  3

# return이 없을 때 마지막 연산 값을 return
def add2(a,b)
   a+b
end  
add2(1,2) # 3

#return을 선택적으로 사용할 수 있습니다.
def divide(a,b)
return "I don't think so" if b == 0
a / b
end  

divide(4, 0)
#  "I don't think so"
divide(4, 1)
#  4
```

- 기본 매개 변수

```ruby
# true일때 : false일때
def factorial4(n)
  n == 0 ? 1 : n*factorial4(n-1)
end  

factorial4(5) # 120
factorail4 # => ArgumentError: wrong number of arguments (given 0, expected 1) from (pry):1:in `factorial4'

# default 값을 정해주면 매개변수 없이 호출가능
def factorial_default(n=10)
 n == 0 ? 1 : n*factorial_default(n-1)  
end  

factorial_default # 3628800
```



### 9. block

```ruby
3.times {puts "hello"}

3.times do |asdf|
	puts asdf # 이 부분이 block
end  

# 0
# 1
# 2
# => 3
```

```ruby
def hihi
	return "No block" unless block_given?
	yield
end  

hihi # "No block"

hihi {puts "hihi"} # hihi
```



###  10. String

- 'single quote' : 거의 있는 그대로 저장

- "double quote" : 개행문자 사용가능

  ```ruby
  a = "안녕하세요. \n 반가워용" 
  # => "안녕하세요. \n 반가워용"
   b = '안녕하세용 \n 반가워용'
  #=> "안녕하세용 \\n 반가워용"
  
  puts a
  #안녕하세요. 
  # 반가워용
  
  puts b
  #안녕하세용 \n 반가워용
  
  name = "allmine123"
  
  a = "#{name}님 안녕하세요"                      
  # => "allmine123님 안녕하세요"
  
  b = '#{name}님 안녕하세요'
  # => "\#{name}님 안녕하세요\"\nb = "
  ```

  

```ruby
my_name = "son seong eun"
my_name.upcase #"SON SEONG EUN"
my_name #"son seong eun"
my_name.upcase!
my_name # "SON SEONG EUN"
```



### 11. array

- 이질배열 생성 가능

  `["string", :s, true, 123]`



### 12. Hash

- key, value로 이루어져 있다!!! *** 매우 중요 ***
- 생성
  - Hash.new(0)
  - {key1:val1, ..}

```ruby
hash1 = {:key => value, key: value}
hash2 = {key: value}
hash3 = {"key" => value}
```

- each 반복하기

  ```ruby
  hash1.each do |k,v| # k, v 변수명 상관없음. 
      puts "#{k} : #{v}"
  end 
  ```

  >  |key, value| 순서



### 13. 추가정보 

- <https://gist.github.com/nacyot/7624036>