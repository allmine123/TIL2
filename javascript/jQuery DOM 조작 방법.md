### jQuery DOM 조작 방법

1. $('선택자')

   1. $('#선택자') => id를 검색 => ex) $('#pw') => pw가 id인 tag를 찾아서  가져옴

   2. $('.선택자') => class를 검색 => ex) $('.email') => email을 class로 갖는 모든 tag를 찾아서  가져옴

   3. $('[선택자]') => attribute를 검색  => ex) $('[href]') => href특성을 가진 모든 태그를 가져옴

   4. $('텍스트') => 텍스트에 해당하는 html tag를 가져옴 

      - ex) $('span') => 모든 span 태그를 가져옴

   5. $('parent > child >grandchild') => parent 안에 있는 child 안에있는 grandchild를 가져옴

      - ex) $('ul>li>a>span') 

   6. 선택자들 조합 가능

      ```javascript
      $('a.class1.class2') // => class1과 class2를 가진 모든 a tag를 가져옴
      $('[href].class1.class2') // => href 특성을 지니고 class1과 class2를 가진 모든 태그를 가져옴
      $('.class > li.class2 > a[href="www.naver.com"]')
      ```

      

2. eq 메소드

   1. $().eq(index) => jQuery로 선택된 elements들 중에 index에 해당하는 element만 반환함.
      - ex) $('span.an_icon').eq(6).css("display","none") => an_icon을 클래스로 가진 span 태그들 중에서 7번째 태그에 접근해서 style="display:none"을 설정해줌
      - $('span.an_icon:eq(6)').css('display', 'none') //위와 동일하게 동작

3. text, html, val

   1. $().text() => 자식 tag들 안에 있는 text만을 가져옴

      ```javascript
      $('a.an_a.mn_cafe').text()
      //결과값
      "
      						카페
      					"
      ```

   2. $().html() => 자식 tag들을 그대로 가져옴, text로 변환하여 가져옴.

      ```javascript
      $('a.an_a.mn_cafe').html()
      //결과값
      "
      						<span class="an_icon"></span><span class="an_txt">카페</span>
      					"
      ```

   3. $().val() =>  input 태그에 한정해서 쓰는 method.input 태그 안에 있는 값을 가져옴

      ```javascript
      //네이버 검색창에 "좋은아침" 입력 후
      $('input#query').val()
      //결과값
      "좋은아침"
      ```

   4. text("값"), html("값"), val("값") => 값을 해당 element에 넣어줌

4. find

   ```javascript
   $('ul.an_l >li > a> span') //an_l을 클래스로 가진 ul 태그 안에 있는 li 태그 안에 있는 a 태그 안에 있는 span태그들을 전부 찾아서 가져옴
   
   $('ul.an_l').find('span') //an_l을 클래스로 가진 ul 태그 안에서 span 태그들을 전부 찾아서 가져옴
   
   $('ul.an_l > span') //1
   $('ul.an_l >li> span') //2
   $('ul.an_l >li > a> span') //3
   //find ==  1+2+3
   ```

5. first, last, prev, next, parent, children

   ```javascript
   $().first() //=> elements 중에 첫 번째 element를 가져옴
   $().last() //=> elements 중에 마지막 element를 가져옴
   $().prev() //=> 이전 element를 가져옴(형제관계에 있는)
   $().next() //=> 다음 element를 가져옴(형제관계에 있는)
   $().parent() //=> 부모 element를 가져옴
   $().children() //=> 자식 element를 가져옴
   ```

6. append, prepend, before, after

   ```javascript
   //예시
   <ul>
       <li></li>
       <li></li>
       <li></li>
   </ul>
   
   $('ul').append('<li class="new"></li>')
   <ul>
       <li></li>
       <li></li>
       <li class = "new"></li>
   </ul>
   
   $('ul').prepend('<li class="new"></li>')
   <ul>
       <li></li>
       <li></li>
       <li class = "new"></li>
   </ul>
           
   ```

7.  remove(), hide(), show(), toggle()

   ```javascript
   $().remove() //=> element 자체를 지워버림
   $().hide() //=> element를 숨겨줌(화면에서 사라지지만, 지워지지는 않음)
   $().show() //=> element를 보여줌
   $().toggle() //=> element가 숨겨져 있으면 보여주고, 보여져있으면 숨겨줍니다.
   ```

8. replaceWith()

   ```javascript
   $(element).replaceWith(new_element) //=> element가 new_element로 바뀜.
   ```

9. attr()

   ```javascript
   $(element).attr('href') //=> element의 attribute에 있는 값을 가져옴
   $(element).attr('href','http://www.daum.net')
   //element의 attribute 값을 바꿔줌
   ```

10.  on() == addEventListener()

    ```javascript
    $(element).on("event", function(){}) //=> element의 event 발생시 function 실행
    
    $(parent_element).on("event", "child_element", function(){})
    //=> parent_element안에 있는 child_element에서 event 발생시 function 실행 => delegated event handler
    
    //예시
    $(document).on('mouseover','a',function(){alert('왜용?')});
    ```

    