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
      avatar: "https://s2.loli.net/2023/06/21/Y3RTZSom2qABtrj.png",
      name: "眰恦",
      limit: 10,
      useLoadingImg: false,
      baseURL: "https://my-qexo-roeq3f2l3-18080866236.vercel.app/",
    }).then(function (){
      console.log("Daodao加载完成");
    })
  </script>
</body>


