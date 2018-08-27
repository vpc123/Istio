# Istio
微服务架构Istio实践文档
# Istio 是什么? #
使用云平台可以为组织提供丰富的好处。然而，不可否认的是，采用云可能会给 DevOps 团队带来压力。开发人员必须使用微服务已满足应用的可移植性，同时运营商管理了极其庞大的混合和多云部署。Istio 允许您连接、保护、控制和观测服务。

##
在较高的层次上，Istio 有助于降低这些部署的复杂性，并减轻开发团队的压力。它是一个完全开源的服务网格，可以透明地分层到现有的分布式应用程序上。它也是一个平台，包括允许它集成到任何日志记录平台、遥测或策略系统的 API。Istio 的多样化功能集使您能够成功高效地运行分布式微服务架构，并提供保护、连接和监控微服务的统一方法。
## 什么是服务网格？ ##
在从单体应用程序向分布式微服务架构的转型过程中，开发人员和运维人员面临诸多挑战，使用 Istio 可以解决这些问题。
服务网格（Service Mesh）这个术语通常用于描述构成这些应用程序的微服务网络以及应用之间的交互。随着规模和复杂性的增长，服务网格越来越难以理解和管理。它的需求包括服务发现、负载均衡、故障恢复、指标收集和监控以及通常更加复杂的运维需求，例如 A/B 测试、金丝雀发布、限流、访问控制和端到端认证等。
Istio 提供了一个完整的解决方案，通过为整个服务网格提供行为洞察和操作控制来满足微服务应用程序的多样化需求。


## Istio用处: ##
Istio 提供一种简单的方式来为已部署的服务建立网络，该网络具有负载均衡、服务间认证、监控等功能，而不需要对服务的代码做任何改动。想要让服务支持 Istio，只需要在您的环境中部署一个特殊的 sidecar 代理，使用 Istio 控制平面功能配置和管理代理，拦截微服务之间的所有网络通信：

- HTTP、gRPC、WebSocket 和 TCP 流量的自动负载均衡。


- 通过丰富的路由规则、重试、故障转移和故障注入，可以对流量行为进行细粒度控制。

- 可插入的策略层和配置 API，支持访问控制、速率限制和配额。


- 对出入集群入口和出口中所有流量的自动度量指标、日志记录和跟踪。


- 通过强大的基于身份的验证和授权，在集群中实现安全的服务间通信。



######Istio 旨在实现可扩展性，满足各种部署需求。

##
# 核心功能 #
#### Istio 在服务网络中统一提供了许多关键功能： ##
## - 流量管理 ##
-通过简单的规则配置和流量路由，您可以控制服务之间的流量和 API 调用。Istio 简化了断路器、超时和重试等服务级别属性的配置，并且可以轻松设置 A/B测试、金丝雀部署和基于百分比的流量分割的分阶段部署等重要任务。

通过更好地了解您的流量和开箱即用的故障恢复功能，您可以在问题出现之前先发现问题，使调用更可靠，并且使您的网络更加强大——无论您面临什么条件。

## 安全 ##
Istio 的安全功能使开发人员可以专注于应用程序级别的安全性。Istio 提供底层安全通信信道，并大规模管理服务通信的认证、授权和加密。使用Istio，服务通信在默认情况下是安全的，它允许您跨多种协议和运行时一致地实施策略——所有这些都很少或根本不需要应用程序更改。

虽然 Istio 与平台无关，但将其与 Kubernetes（或基础架构）网络策略结合使用，其优势会更大，包括在网络和应用层保护 pod 间或服务间通信的能力。

## 可观察性 ##
Istio 强大的跟踪、监控和日志记录可让您深入了解服务网格部署。通过 Istio 的监控功能，可以真正了解服务性能如何影响上游和下游的功能，而其自定义仪表板可以提供对所有服务性能的可视性，并让您了解该性能如何影响您的其他进程。

Istio 的 Mixer 组件负责策略控制和遥测收集。它提供后端抽象和中介，将 Istio 的其余部分与各个基础架构后端的实现细节隔离开来，并为运维提供对网格和基础架构后端之间所有交互的细粒度控制。

所有这些功能可以让您可以更有效地设置、监控和实施服务上的 SLO。当然，最重要的是，您可以快速有效地检测和修复问题。

## 平台支持 ##

Istio 是独立于平台的，旨在运行在各种环境中，包括跨云、内部部署、Kubernetes、Mesos 等。您可以在 Kubernetes 上部署 Istio 或具有 Consul 的 Nomad 上部署。Istio 目前支持：

- 在 Kubernetes 上部署的服务


- 使用 Consul 注册的服务


- 在虚拟机上部署的服务

## 集成和定制 ##

策略执行组件可以扩展和定制，以便与现有的 ACL、日志、监控、配额、审计等方案集成。

## 架构 ##

Istio 服务网格逻辑上分为数据平面和控制平面。

数据平面由一组以 sidecar 方式部署的智能代理（Envoy）组成。这些代理可以调节和控制微服务及 Mixer 之间所有的网络通信。
控制平面负责管理和配置代理来路由流量。此外控制平面配置 Mixer 以实施策略和收集遥测数据。
下图显示了构成每个面板的不同组件：

![](https://i.imgur.com/F7Ad4HE.png)

				Istio 架构