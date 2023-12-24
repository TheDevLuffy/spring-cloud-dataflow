<p align="center">
  <a href="https://dataflow.spring.io/">
    <img alt="Spring Data Flow Dashboard" title="Spring Data Flow" src="https://i.imgur.com/hpeKaRk.png" width="450" />
  </a>
</p>

<p align="center">
  <a href="https://dataflow.spring.io/getting-started/">
    <img src="https://spring.io/badges/spring-cloud-dataflow/ga.svg"
         alt="Latest Release Version" />
  </a>
  <a href="https://dataflow.spring.io/getting-started/">
    <img src="https://spring.io/badges/spring-cloud-dataflow/snapshot.svg"
         alt="Latest Snapshot Version" />
  </a>
  <br>
  <a href="https://build.spring.io/browse/SCD-BMASTER">
    <img src="https://build.spring.io/plugins/servlet/wittified/build-status/SCD-BMASTER"
         alt="Build Status" />
  </a>
</p>

*Spring Cloud Data Flow* 는 [Cloud Foundry](https://www.cloudfoundry.org/) 와 Kubernetes 에서 스트리밍과 대량 데이터 일괄 처리 파이프라인을 만들기 위한 마이크로서비스 기반의 도구입니다. 

데이터 처리 파이프라인은 [Spring Cloud Stream](https://spring.io/projects/spring-cloud-stream/#overview) 또는 [Spring Cloud Task](https://spring.io/projects/spring-cloud-task/#overview) 마이크로서비스 프레임워크를 사용하여 구축된 Spring Boot 앱으로 구성됩니다.

이로 인해 Spring Cloud Data Flow는 데이터 가져오기/내보내기부터 이벤트 스트리밍, 예측 분석에 이르기까지 다양한 데이터 처리 사용 사례에 이상적입니다.

----

## 컴포넌트 (Components)

**아키텍처 (Architecture)** : Spring Cloud Data Flow 서버는 RESTful API 와 REST 클라이언트(Shell, 대시보드, Java DSL)를 제공하는 Spring Boot 어플리케이션입니다.

단일 Spring Cloud Data Flow 설치는 로컬, Cloud Foundry, Kubernetes에 스트림과 작업을 오케스트레이션하는 배포를 지원할 수 있습니다.

Spring Cloud Data Flow [아키텍처](https://dataflow.spring.io/docs/concepts/architecture/)
와 [기능 능력?(feature capabilities)](https://dataflow.spring.io/features/)에 친숙해지세요.

**배포자 SPI(Deployer SPI)** : 서비스 제공자 인터페이스 (SPI) 는 [Spring Cloud Deployer](https://github.com/spring-cloud/spring-cloud-deployer)에 정의되어 있습니다. 배포자 SPI 는 주어진 스트리밍 혹은 배치 데이터 파이프라인을 위한 앱들을 배포하고, 어플리케이션 라이프사이클은 관리하기 위하여 추상화 계층을 제공합니다.

Spring Cloud Deployer 구현:

* [Local](https://github.com/spring-cloud/spring-cloud-deployer-local)
* [Cloud Foundry](https://github.com/spring-cloud/spring-cloud-deployer-cloudfoundry)
* [Kubernetes](https://github.com/spring-cloud/spring-cloud-deployer-kubernetes)

**도메인 모델(Domain Model)** : Spring Cloud Data Flow [domain module](https://github.com/spring-cloud/spring-cloud-dataflow/tree/master/spring-cloud-dataflow-core)은 *소스(source)* 에서 *싱크(sink)* 까지 선형 데이터 파이프라인에 Spring Cloud Stream 애플리케이션들을 구성하는 스트림 개념이 포함되어 있습니다. 이는 필요에 따라 중간에 *프로세서(processor)* 애플리케이션들을 포함할 수 있습니다. 또한, SCDF의 도메인에는 무한정 실행되지 않는 모든 프로세스를 포함할 수 있는 *작업(task)* 개념도 포함되어 있으며, 이에는 [Spring Batch](https://github.com/spring-projects/spring-batch) 작업도 포함됩니다.


**어플리케이션 레지스트리(Application Registry)** : [App Registry](https://github.com/spring-cloud/spring-cloud-dataflow/tree/master/spring-cloud-dataflow-registry)는 재사용 가능한 어플리케이션들의 카탈로그 메타데이터를 관리합니다. 예를 들어 Maven 좌표에 의존하는 경우, 어플리케이션 URI 는 이와 같은 형식입니다: `maven://<groupId>:<artifactId>:<version>`.

**Shell/CLI**: [Shell](https://github.com/spring-cloud/spring-cloud-dataflow/tree/master/spring-cloud-dataflow-shell)은 Spring Cloud Data Flow 서버의 REST API 에 연결하고, 스트림이나 작업을 정의하고 그 수명 주기를 관리하는 과정을 단순화하는 DSL(도메인 특화 언어)을 지원합니다.

----

## Building

레포지토리를 clone 하고 아래를 입력하세요. 

    $ ./mvnw -s .settings.xml clean install 

더 많은 정보를 찾고 있다면 [이 링크](https://github.com/spring-cloud/spring-cloud-dataflow/blob/master/spring-cloud-dataflow-docs/src/main/asciidoc/appendix-building.adoc)를 참고하세요.

### Building on Windows

생략

----

## Running Locally w/ Oracle 

(생략)


----

## Running Locally w/ Microsoft SQL Server

(생략)

----

## Running Locally w/ IBM DB2

(생략)


----

## Contributing

We welcome contributions! See the [CONTRIBUTING](./CONTRIBUTING.adoc) guide for details.

----

## Code formatting guidelines

* The directory ./src/eclipse has two files for use with code formatting, `eclipse-code-formatter.xml` for the majority of the code formatting rules and `eclipse.importorder` to order the import statements.

* In eclipse you import these files by navigating `Windows -> Preferences` and then the menu items `Preferences > Java > Code Style > Formatter` and `Preferences > Java > Code Style > Organize Imports` respectfully.

* In `IntelliJ`, install the plugin `Eclipse Code Formatter`.  You can find it by searching the "Browse Repositories" under the plugin option within `IntelliJ` (Once installed you will need to reboot Intellij for it to take effect).
Then navigate to `Intellij IDEA > Preferences` and select the Eclipse Code Formatter.  Select the `eclipse-code-formatter.xml` file for the field `Eclipse Java Formatter config file` and the file `eclipse.importorder` for the field `Import order`.
Enable the `Eclipse code formatter` by clicking `Use the Eclipse code formatter` then click the *OK* button.
** NOTE: If you configure the `Eclipse Code Formatter` from `File > Other Settings > Default Settings` it will set this policy across all of your Intellij projects.

## License

Spring Cloud Data Flow is Open Source software released under the [Apache 2.0 license](https://www.apache.org/licenses/LICENSE-2.0.html).
