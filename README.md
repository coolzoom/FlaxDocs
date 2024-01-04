# Flax Engine 绯蓝引擎说明文档

![Flax Engine Docs](manual/graphics/post-effects/media/postFx.png)

欢迎来到绯蓝文档存储库。这个存储库包含绯蓝文档的所有源文件(https://docs.flaxengine.com/)。欢迎任何人做翻译贡献!

## 编辑

我们使用[DocFX](https://github.com/dotnet/docfx)工具在线构建和托管文档。它支持markdown样式文件(`.md`)，因为它是一种非常标准化和流行的格式。使用markdown风格编写技术文档既简单又高效。

要编辑文档，我们建议您使用以下工具 [Zettlr](https://www.zettlr.com/) 或者 [Typora](https://typora.io/) 或者 [Visual Studio Code](https://code.visualstudio.com/).

## 构建和测试

文档可以在Linux和Windows上构建和托管。DocFx可以在.Net或Mono上运行。默认情况下，默认站点地址托管在`localhost:8080`上，但可以很容易地配置和进行变更。

### Windows系统

* 下载存储库 (或者用如下命令克隆 `git clone https://github.com/FlaxEngine/FlaxDocs.git`)
* 执行 `build_manual.bat` 来构建说明文档，或者执行 `build_all.bat` 来构建所有文档（包括API），当然这样需要花费更长的时间来完成。
* 执行 `run_local_website.bat` 来预览站点

### Linux

* 安装Mono框架 [Mono](http://www.mono-project.com/docs/getting-started/install/linux/)
* 克隆存储库 (`git clone https://github.com/FlaxEngine/FlaxDocs.git`)
* 执行 `chmod +x docs.sh`. 这将修改 `docs.sh` 的权限以便稍后能够执行它。
* 执行 `./docs.sh rebuild`

## 技术摘要

C#和C++ API参考页面是通过下载和构建引擎来生成的，在文件`commit.txt`中指定了一个给定的版本。C# API通过`docfx metadata` 提取到 `api` 文件夹中。C++ API是通过我们的自定义分支[code2yaml](https://github.com/FlaxEngine/code2yaml)提取的，它用`doxygen`解析引擎头文件，生成元数据到`api-cpp`文件夹。

关键配置文件:
* `docfx.json` - 用于构建docfx文档的配置文件。
* `code2yaml.json` - 用于提取C++ API文档的code2yaml配置。
* `doxyfile` - 配置doxygen以输出带有引擎API的XML文件，并由code2yaml处理。
* `commit.txt` - 包含用于构建API的[FlaxEngine](https://github.com/FlaxEngine/FlaxEngine)修订的提交哈希。
* `.github\workflows\docs-publish.yml` - Github Actions工作流在git标签`update-<version>`时触发，它用api构建整个文档，并将它们发布到[FlaxDocsHost](https://github.com/FlaxEngine/FlaxDocsHost)上，以便在Github Pages上静态托管。
* `.github\workflows\docs-build.yml` - 在检测到push/pr动作时触发Github Actions工作流，构建没有api的说明文档来验证修改文档的完整性(例如：警告无效链接或丢失文件)。

## 开源代码许可协议

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">FlaxDocs</span> 代码库是在 <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License 协议下许可的。</a>.
