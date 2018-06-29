Test case sunum

Package.json:

Burada bazı vue için default paketleri yükledim. Bunlar vue-loader, vue-template-compiler. .vue formatlarını derlerken kullanılıyor. https://vuejs.org/v2/guide/installation.html#Runtime-Compiler-vs-Runtime-only
webpack.config.js' in içerisinde linkleri de ekledim.

Modül paketleme:

Modül paketlemek içinse ReactJs'den aşina olduğum webpack'i kullandım. Webpack'in kendi standartları dışında örnekleri inceleyerek ve sitesindeki (https://vuejs.org/v2/guide/installation.html#Webpack) webpack configlerini de inceleyerek basit bir yapı oluşturdum. Scss kullanacağım için ona göre ayar yaptım. Herhangi bir resim kullanmayacağımdan dolayı image formatlarından hiçbirisini eklemedim. ES6 ile yazacağım için de Babel kullanıyorum.

Son örneklerde ve vue-cli da browserslist için kullanılan özellikleri aldım. Babel settingslerini .babelrc olarak ekledim.

Proje kurulumu:
    ```npm install```

Projeyi başlatma:
    ```npm start``` kodunu terminale yazarak başlatabilirsiniz

Projeyi derlemek:
    ```npm run build``` kodunu terminale yazarak production env. derleyebilirsiniz

Kullanılan özel paketler:
Api call için axios kullandım. Standart bir fetch paketidir. Herhangi bir configürasyona gerek yok.

Yeni proje için de normalize ve reset.css paketlerini yükledim.

Kazanım olarak; normalde flexbox ile pek bir işim olmazdı ama bu proje için özellikle araştırdım ve öğrenmiş oldum. Normalde ihtiyaç olana kadar bakmayacaktım. Vue bildiğimi söylemem biraz zor ama daha önceden küçük bir proje yaptığım için oradan bilgim vardı. Bu proje ile de tekrar araştırma imkanım oldu. BEM kullanmıyordum, onu da kullanmaya başladım.




