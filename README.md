Sunum

    Package.json:
    Burada bazı vue için default paketleri yükledim. Bunlar vue-loader, vue-template-compiler. .vue formatlarını derlerken kullanılıyor. https://vuejs.org/v2/guide/installation.html#Runtime-Compiler-vs-Runtime-only
    webpack.config.js' in içerisinde linkleri de ekledim.

    Paket yöneticisi:
    Paket yöneticisi olarak normalde ReactJs yazdığım için aşina olduğum webpack'i kullandım. Webpack'in kendi standartları dışında örnekleri inceleyerek ve sitesindeki (https://vuejs.org/v2/guide/installation.html#Webpack) webpack configlerini de inceleyerek basit bir yapı oluşturdum. Scss kullanacağım için ona göre ayar yaptım. Herhangi bir resim kullanmayacağımdan dolayı image formatlarından hiçbirisini eklemedim. Normalde herhangi bir başlangıç node enviroment'ı kullanamayacaktım ama derleme için cross-env paketini kullandım. ES6 ile yazacağım için de Babel kullanıyorum.

    Son örneklerde ve vue-cli da browserslist için kullanılan özellikleri aldım. Babel settingslerini .babelrc olarak ekledim.

    Projeyi başlatma:
        ```npm run dev kodunu terminale yazarak başlatabilirsiniz.```
    Projeyi derlemek:
        ```npm run build kodunu terminale yazarak production env. derleyebilirsiniz.```
