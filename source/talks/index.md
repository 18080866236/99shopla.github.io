<head>
  <!-- ... -->
  <script src="//cdn.jsdelivr.net/gh/Uyoahz26/daodao@main/dist/qexo-dao.min.js"></script>
  <!-- ... -->
</head>
<body>
  <!-- ... -->
  <div id="DaoDao"></div>
  <script>
    qexoDaodao?.init({
      el: "#DaoDao",
      avatar: "https://bg.99shopla.com/touxiang.png",
      name: "眰恦",
      limit: 10,
      useLoadingImg: false,
      baseURL: "https://qexo.99shopla.com/",
    }).then(function (){
      console.log("Daodao加载完成");
    })
  </script>
</body>


