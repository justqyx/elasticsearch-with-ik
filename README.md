这不是一个 Project，而是放置了一些文件和包。

[elasticsearch-analysis-ik](https://github.com/medcl/elasticsearch-analysis-ik) 这个是 ElasticSearch 版的 IK Analyzer，下面提及的我自己打包的 deb 包所需要用到的。

[elasticsearch-rtf](https://github.com/medcl/elasticsearch-rtf) 搞了太多，不太喜欢，而且在 Production 出了问题，所以自己才弄了一个 deb 包(下面提及到的)。

== 说明

`packages/elasticsearch-1.1.1.deb` 是 ElasticSearch 官方发布的 deb 包。

`packages/elasticsearch-with-ik-1.1.1.deb` 是将 IK Analyzer 加入了官方发布的 deb 包后重新打包而成，目的是为了能够在服务器上直接安装，而无需额外自己再手动配置中文分词器。

== Build with ik

1. `dpkg -x packages/elasticsearch-1.1.1.deb packages/elasticsearch-1.1.1`
2. `dpkg -e packages/elasticsearch-1.1.1.deb packages/elasticsearch-1.1.1/DEBIAN`
3. 将 `elasticsearch-analysis-ik/config/ik` 文件夹复制到 `packages/elasticsearch-1.1.1/etc/elasticsearch/` 
4. 将 `elasticsearch-analysis-ik/target/elastchsearch-analysis-ik-1.2.6.jar` 复制到 `packages/elasticsearch-1.1.1/usr/share/elastcisearch/plugins/analysis-ik/`
5. 将 `elasticsearch-analysis-ik/config/ik` 文件夹复制到 `packages/elasticsearch-1.1.1/usr/share/elasticsearch/config/` 
6. `dpkg -b packages/elasticsearch-1.1.1 packages/elasticsearch-with-ik-1.1.1.deb`

== Usage

在 Ubuntu 安装

    cd packages
    sudo dpkg -i elasticsearch-with-ik-1.1.1.deb
