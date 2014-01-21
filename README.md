这不是一个 Project，而是放置了一些文件和包。

[elasticsearch-analysis-ik](https://github.com/medcl/elasticsearch-analysis-ik) 这个是 ElasticSearch 版的 IK Analyzer，下面提及的我自己打包的 deb 包所需要用到的。

[elasticsearch-rtf](https://github.com/medcl/elasticsearch-rtf) 搞了太多，不太喜欢，而且在 Production 出了问题，所以自己才弄了一个 deb 包(下面提及到的)。

== 说明

`packages/elasticsearch-0.90.10.deb` 是 ElasticSearch 官方发布的 deb 包。

`packages/elasticsearch-with-ik-0.90.10.deb` 是我将 IK Analyzer 加入了官方发布的 deb 包后重新打包而成，目的是为了能够在服务器上直接安装，而无需额外自己再手动配置中文分词器。

== Usage

在 Ubuntu 安装

    cd packages
    sudo dpkg -i elasticsearch-with-ik-0.90.10.deb
