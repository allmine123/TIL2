### Rails ajax 구현

AJAX = Asynchronous JavaScript And XML.

1) Asynchronous => 비동기적인

2) JavaScript => 자바스크립트를 이용

3) XML => XML형태의 자료가 오갔기 때문. 현재는 xml뿐만 아니라, json, text등 다양한 자료 형태로 오감.

XHR(XMLHttpRequest - 자바스크립트로 구현한 객체) 객체를 통해 오감.



```javascript
var csrf_token = $('[name="csrf-token"]').attr('content')
```



#### 글 생성시 ajax

1. data-remote = ture (html 태그 기준)

   ```javascript
   <form action="/posts/<%= @post.id%>/comments" method="post" data-remote=true>
     <input type="text" name="content" /><br />
     <input type="hidden" name="authenticity_token" value="<%= form_authenticity_token %>">
     <input type="submit" />
   </form>
   ```

2. commentsController =>  create action

   ```ruby
   def create
       @comment = Post.find(params[:post_id]).comments.new(comment_params)
       @comment.user_id = current_user.id
       if @comment.save
   
         respond_to do |format|#요청에 따라 html 혹은 js 파일 리턴
           format.html {redirect_to :back}
           format.js {render 'create_temp'}
         end
       else
         redirect_to :back
       end
     end
   ```

3. create.js.erb 파일 작성 **(escape_javascript 약어: j)**

   ```ruby
   $("div#comments").append(`<p><%= escape_javascript(@comment.content) %>
   <%= escape_javascript(link_to '댓삭', destroy_comment_path(@comment.id), method: :delete, remote: true, class: 'delete_comment') %>
   </p><hr />`);
   ```

4. ajax 결과에 따른 eventhandler 작성 (show.html.erb)

   ```ruby
   <script>
     $('form').on('ajax:success',function(){
       $('input[name="content"]').val('');
     });
   </script>
   ```



#### 글 삭제 시 ajax 구현

1. remote = true (rails 코드 기준)

   ```ruby
   <%= link_to '댓삭', destroy_comment_path(comment.id), remote: true, method: :delete, class:"delete_comment" %>
   ```

2. CommentsController => destroy action

   ```ruby
     def destroy
       @comment = Comment.find(params[:comment_id])
       @comment.destroy
       respond_to do |format|
         format.html {redirect_to :back}
         format.js {}
       end
     end
   ```

3. destroy.js.erb 작성

   ```ruby
   var parent = $('a[href="/comments/<%= params[:comment_id] %>"]').parent();
   var hr = parent.next();
   parent.remove();
   hr.remove();
   ```

   

#### jQuery로 ajax 구현

##### 글 생성시 ajax 구현

1. script 생성

```javascript
$('input[type="submit"]').on('click', function(e){
    e.preventDefault();
    alert('start!!');
    $.ajax({
      url: $('form').attr('action'),
      type: "POST",
      data:{content:$('input[name="content"]').val(),
      authenticity_token:$('[name="csrf-token"]').attr('content')},
      dataType: 'script',
      success: function(){
        alert('success');
        $('input[name="content"]').val('');
      },
      error: function(){
        alert('fail');
      }

    });
  });
```

2. 이후 rails의 ajax 구현 순서(2,3,4)와 동일



##### 글 삭제시 ajax 구현

1. script 생성

   ```javascript
   $('.delete_comment').on('click', function(e){
       e.preventDefault();
       $.ajax({
         url: this.href,//<a></a>
         type: "DELETE",
         data: {authenticity_token:$('[name="csrf-token"]').attr('content')},
         dataType:"script",
         success: function(){
           alert('delete_complete!');
         },
         error: function(){
           alert('delete_error!');
         }
       });
     });
   ```

2. 이후 rails의 ajax 구현 순서(2, 3)와 동일