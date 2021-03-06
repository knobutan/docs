---

copyright:
years: 2016

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# 네트워크 랜드스케이프
{: #etn_overview}
마지막 업데이트 날짜: 2016년 10월 13일
{: .last-updated}

IBM Blockchain on Bluemix 스타터 개발자 계획 및 고급 보안 비즈니스 네트워크 계획은 Hyperledger Fabric v0.5의 최신판, PBFT(Practical Byzantine Fault Tolerance) 합의 프로토콜 및 HFC(Hyperledger Fabric Client) SDK for Node.js를 활용합니다. 두 플랜 모두 네 개의 네트워크 노드와 하나의 인증 기관으로 구성됩니다. 인증 기관은 디지털 인증서의 발행을 통해 ID, 네트워크 권한 및 기밀 트랜잭션을 관리하는 "멤버십 서비스"를 통제합니다.
{:shortdesc}

다음의 블록체인 기능을 두 플랜 모두에서 사용할 수 있습니다. 

* PBFT 합의 프로토콜은 공유 원장에 쓰여진 모든 트랜잭션의 순서 지정을 관리합니다. 4개 노드의 PBFT 블록체인 네트워크는 하나의 비잔틴(결함) 노드에도 불구하고 합의에 도달할 수 있습니다. PBFT 합의 테스트 세부사항은 [합의 및 가용성 테스트](etn_pbft.html)를 참조하십시오. 
* HFC SDK for Node.js는 클라이언트 측 Node.js 애플리케이션이 블록체인 네트워크와 상호작용할 수 있도록 허용합니다. 클라이언트 측 앱은 멤버십 서비스를 통해 안전하게 사용자를 등록접수하고 트랜잭션을 발행하며 tCerts를 사용하여 자산을 암호화하여 교환할 수 있습니다. 멤버십 서비스 및 사용자 개인정보 보호정책에 대한 자세한 정보는 [HFC SDK for Node.js](etn_sdk.html) 섹션 및 Hyperledger Fabric [프로토콜 스펙](https://github.com/hyperledger/fabric/blob/master/docs/protocol-spec.md)을 참조하십시오. 
* [Bluemix 모니터 대시보드](ibmblockchainmonitor.html)를 통해 블록체인 네트워크 환경에 대한 세부사항에 액세스할 수 있습니다.   

<br>
## 용어

다음 용어와 그 뒤에 나오는 다이어그램을 통해 IBM Blockchain 네트워크 컴포넌트에 대해 이해할 수 있습니다.

* 멤버(Member) - 블록체인 네트워크에 참여하기 위한 ID입니다. 사용자, 피어, 유효성 검증자 및 감사자를 포함하여 서로 다른 클래스의 멤버가 있습니다. 
* 멤버십 서비스(Membership services) - 멤버 ID 가져오기 및 관리와 연관된 서비스입니다. 멤버십 서비스는 인증 기관에 의해 관리됩니다.   
* 등록(Registration) - 네트워크에 새 멤버 ID를 추가하는 행위입니다. 멤버는 '등록자' 권한의 사용자에 의해 동적으로 네트워크에 추가될 수 있습니다. 또한 멤버에게는 네트워크의 액세스 및 권한을 제어하는 역할 및 속성이 지정됩니다. 역할 또는 속성 중 어느 것도 동적으로 지정될 수 없습니다. 대신 membersrvc.yaml 파일을 직접 편집해야 합니다. 
* 등록접수(Enrollment) - 새 멤버가 블록체인 네트워크에 액세스할 수 있도록 허용하여 등록 프로세스를 완료합니다. 등록접수는 등록자로부터 시크릿을 가져온 이후 새 멤버에 의해 수행되거나(외부(out-of-band)에서), 새 멤버 대신 행동할 위임 권한이 있는 중간자에 의해 수행될 수 있습니다.   

<br>
## 네트워크 아키텍처

그림 1 및 이의 후속 설명은 IBM Blockchain 네트워크 아키텍처와 멤버 서비스, 트랜잭션, 합의, 원장 추가의 데이터 플로우를 보여줍니다.

![전용 네트워크](images/Architecture_BMX_dedicated.png "IBM Blockchain 네트워크 아키텍처")
그림 1.

다음 단계는 그림 1의 네트워크 플로우를 자세히 설명합니다. 

1. 등록된 사용자는 PKI(멤버십 서비스)를 통해 네트워크에 등록접수하며 장기 등록접수 인증서(eCert) 및 트랜잭션 인증서(tCerts)의 일괄처리를 수신합니다. 
2. 사용자는 체인코드를 네트워크에 배치합니다. 체인코드(스마트 계약)는 비즈니스 로직, 즉 규칙을 인코딩하며, 특정 유형의 트랜잭션을 규정합니다. 각 트랜잭션(배치, 호출 또는 조회)에서는 고유 tCert가 필요하며, 사용자의 개인 키로 서명되어야 합니다. 사용자는 지정된 tCerts에서 자체 개인 키를 유도합니다. 
3. 사용자는 인코딩된 로직을 자체 실행하도록 계약을 트리거하는 스마트 계약을 호출합니다. 
4. 트랜잭션은 네트워크 피어에 제출됩니다. 일단 피어가 트랜잭션 요청을 수신하면, 이는 네트워크의 기본 피어(그림 1의 VP1)에 대해 요청을 제출합니다. 기본 피어는 트랜잭션 블록을 순서 지정하며 이 순서를 동료 피어에게 브로드캐스트합니다. 
5. 피어는 네트워크 합의 프로토콜(PBFT)을 사용하여 제출된 트랜잭션의 순서에 동의합니다. 트랜잭션을 집합적으로 순서 지정하는 이 프로세스를 합의라고 합니다.   
6. 일단 피어가 합의에 도달하면, 트랜잭션 요청이 실행되며 블록이 공유 원장에 추가됩니다.   

<!---Both the developer and high-security networks unlock several features in the Hyperledger fabric which robustly enhance security, confidentiality and privacy.  The only fundamental difference between the two is their operating/hosting environment.  The developer network runs in a shared multi-tenant environment on Softlayer, whereas the high-security network exists as an isolated single-tenant running in a secure services container.  Each network leverages the same capabilities from the fabric, including a PBFT consensus protocol and the enhanced Node.js SDK.~~

~~The High-Security business network runs in an isolated and highly secured environment, distinguishing it from other cloud-hosted offerings. The operating system, fabric, and nodes all exist in a secure services container (SSC), providing your enterprise with the security and impregnability that customers have come to expect from system Z technology.  The SSC delivers performance optimization in - peer to peer communication, availability, scalability, hardware encryption, tamper-proof crypto keys, and securely encrypted VMs.  See the [Secure Services Container](etn_ssc.html) section for more details on the security features provided through the SSC.  Additionally, the high security network unlocks numerous features of the Hyperledger fabric (unavailable in the developer service), which robustly enhance security, confidentiality and privacy.  The configuration is such that you are able to test and affirm these features.~~  
{:shortdesc}

~~The high security plan augments the developer plan by delivering several enhancements that help meet the security requirements and concerns of an enterprise-level participant:~~--->

<!---The environment (LinuxONE on z) consists of a four-peer network implementing PBFT with Membership Services enabled, running in an application container.  The application container protects blockchain software, chaincode, and data running within the system. The blockchain software within the secure boot can be signed, attested, and encrypted; and once installed in the application container, is tamper-resistant.  Root users of the platform and system administrators cannot access or see z secure container contents.  In addition, the LinuxOne on z provides you with FIPS compliance, high Evaluation Assurance Level protection, a highly auditable operating environment, and crypto optimization--->
