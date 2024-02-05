# js_04
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>jquery ajax</title>
    <script>
        $(document).ready(function () {
            $("#bnt").click(function () {
                //$.ajax 함수는 비동기적으로 http요청을 수행하는데 사용됨.
                // 다양한 파라미터를 설정할 수 있어서 매우 유연함.
                $.ajax({
                    //:요청 url, type:요청타임(GET,POST,PUT,DELETE)
                    //data:전송데티러, dataType:리턴타임,success:요청성공시 호출된 콜백함수
                    url: "https://api.upbit.com/vl/market/all"
                    , type: "GET"
                    , dataType: "json"
                    , success: function (res) {
                        console.log(res);
                    }, error(e){
                        console.log(e);
                    }
                });
            });
        });

    </script>
</head>

<body>
    <input type="button" id="btn" value="요청" ></body>

</html>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://code.jquery.com/jquery-3.7.1.js"></script>
    <title>Document</title>
    <script>
 //let url = "https://dapi.kakao.com/v2/search/web?sort=accuracy&page=1&size=50&query=" + encoding_query;
           // var ajax = new XMLHttpRequest();
           // ajax.open('GET', url, true);
            //alert(url);
            //ajax.setRequestHeader('Authorization', 'KakaoAK d19ff3792221cef6e84db883f2e657ac');
            //ajax.setRequestHeader('Content-type', 'application/json; charset=utf-8')
       $(document).ready(function(){
        let TOKEN = "d19ff3792221cef6e84db883f2e657ac";
        $("#btn").click(function(){
            let q =$("#keyword").val(); //입력값
            $.ajax({
                url:"https://dapi.kakao.com/v2/search/web"
               ,type:"GET"
               ,data:{"query":q
                     ,"page": 2
                     ,"size": 50}
                ,contentType : "application/json; charset=utf-8"
                ,headers :{'Authorization': 'KakaoAK ' + TOKEN}
                ,success : function(res){
                    console.log(res);
                    let docs = res['documents'];
                    $.each(docs, function(i, item){
                        console.log(item['title']);
                    });
                    },error : function(e){
                        console.log(e);
                    }
                });

            });

        });

     



    </script>
</head>
<body>
    <input type="text" id="keyword" placeholder="검색어를 입력하세요">
    <input type="button" id="btn" value="검색">
    <div id="content"></div>
    
</body>
</html>
