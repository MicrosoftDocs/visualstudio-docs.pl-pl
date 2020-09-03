---
title: Używanie KubernetesLocalProcessConfig. YAML do dodatkowej konfiguracji w przypadku procesu lokalnego z usługą Kubernetes
services: azure-dev-spaces
ms.date: 07/28/2020
ms.topic: conceptual
description: Opisuje dodatkowe opcje konfiguracji dla procesu lokalnego z Kubernetes za pomocą KubernetesLocalProcessConfig. YAML
keywords: Proces lokalny z Kubernetes, Azure Dev Spaces, dev Spaces, Docker, Kubernetes, Azure, AKS, Azure Kubernetes Service, Containers
monikerRange: '>=vs-2019'
author: ghogen
ms.author: ghogen
manager: jillfra
ms.openlocfilehash: 234eacedbc08007ede6bb5745a1a289aa838cccb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "87508304"
---
# <a name="configure-local-process-with-kubernetes"></a>Konfigurowanie procesu lokalnego z platformą Kubernetes

`KubernetesLocalProcessConfig.yaml`Plik umożliwia replikowanie zmiennych środowiskowych i zainstalowanych plików dostępnych dla Twojego zasobnika w KLASTRZE AKS. W pliku można określić następujące akcje `KubernetesLocalProcessConfig.yaml` :

* Pobierz wolumin i Ustaw ścieżkę do tego woluminu jako zmienną środowiskową.
* Utwórz usługę działającą w klastrze jako dostępną do procesów uruchomionych na komputerze deweloperskim.
* Utwórz zmienną środowiskową o stałej wartości.

Plik domyślny `KubernetesLocalProcessConfig.yaml` nie jest tworzony automatycznie, dlatego należy ręcznie utworzyć plik w katalogu głównym projektu.

## <a name="download-a-volume"></a>Pobieranie woluminu

W obszarze *ENV*Określ *nazwę* i *wartość* dla każdego woluminu, który chcesz pobrać. *Nazwa* to zmienna środowiskowa, która będzie używana na komputerze deweloperskim. *Wartość* jest nazwą woluminu i ścieżką na komputerze deweloperskim. Wartość parametru *Value* przyjmuje postać *$ (volumeMounts: VOLUME_NAME)/Path/to/Files*.

Na przykład:

```yaml
version: 0.1
env:
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
```

Powyższy przykład pobiera wolumin *listy dozwolonych* z kontenera i ustawia tę lokalizację oraz ścieżkę do zmiennej środowiskowej *ALLOW_LIST_PATH*. Domyślnym zachowaniem jest pobranie plików do określonej ścieżki w katalogu tymczasowym na komputerze deweloperskim. W powyższym przykładzie *ALLOW_LIST_PATH* jest ustawiona na `/TEMPORARY_DIR/allow-list` . 

> [!NOTE]
> Pobranie woluminu spowoduje pobranie całej zawartości tego woluminu niezależnie od ustawionej ścieżki. Ścieżka służy tylko do ustawiania zmiennej środowiskowej do użycia na komputerze deweloperskim. Dodanie */Allow-list* lub */Path/to/Files* na końcu tokenu nie wpływa na miejsce utrwalania woluminu. Zmienna środowiskowa jest tylko wygodą w przypadku, gdy aplikacja wymaga odwołania do określonego pliku w tym woluminie.

Istnieje również możliwość określenia lokalizacji do pobrania instalacji woluminu na komputerze deweloperskim, a nie przy użyciu katalogu tymczasowego. W obszarze *volumeMounts*Określ *nazwę* i *LocalPath* dla każdej określonej lokalizacji. *Nazwa* jest nazwą woluminu, która ma być zgodna, a *LocalPath* jest ścieżką bezwzględną na komputerze deweloperskim. Na przykład:

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
```

Powyższy przykład używa wpisu w *ENV* , aby pobrać wolumin pasujący do *domyślnego- \* *token-, taki jak *default-token-1111* lub *default-token-1234-5678-90abcdef*. W przypadku, gdy wiele woluminów jest zgodnych, używany jest pierwszy pasujący wolumin. Wszystkie pliki są pobierane na `/var/run/secrets/kubernetes.io/serviceaccount` komputer deweloperski przy użyciu wpisu w *volumeMounts*. Zmienna środowiskowa *KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE* jest ustawiona na `/var/run/secrets/kubernetes.io/serviceaccount` .

## <a name="make-a-service-available"></a>Udostępnianie usługi

W obszarze *ENV*Określ *nazwę* i *wartość* dla każdej usługi, która ma być dostępna na komputerze deweloperskim. *Nazwa* to zmienna środowiskowa, która będzie używana na komputerze deweloperskim. *Wartość* jest nazwą usługi z klastra i ścieżką. Wartość parametru *Value* przyjmuje postać *$ (Services: service_name)/Path*.

Na przykład:

```yaml
version: 0.1
env:
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
```

W powyższym przykładzie usługa *myapp1* jest dostępna dla komputera deweloperskiego, a zmienna środowiskowa *MYAPP1_SERVICE_HOST* jest ustawiona na lokalny adres IP usługi *myapp1* z `/api/v1` ścieżką (czyli `127.1.1.4/api/v1` ). Usługa *myapp1* jest dostępna przy użyciu zmiennej środowiskowej, *myapp1*lub *myapp1. svc. Cluster. Local*.

> [!NOTE]
> Udostępnienie usługi na komputerze deweloperskim spowoduje udostępnienie całej usługi niezależnie od ustawionej ścieżki. Ścieżka służy tylko do ustawiania zmiennej środowiskowej do użycia na komputerze deweloperskim.
Można również udostępnić usługę z określonej przestrzeni nazw Kubernetes za pomocą *$ (Services: service_name. NAMESPACE_NAME)*. Na przykład:

```yaml
version: 0.1
env:
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
```

Powyższy przykład sprawia, że *myapp2* z przestrzeni nazw obszaru *nazw* jest dostępny na komputerze deweloperskim i ustawia zmienną środowiskową *MYAPP2_SERVICE_HOST* na lokalny adres IP *myapp2* *z przestrzeni nazw obszaru nazw.*

## <a name="create-an-environment-variable-with-a-constant-value"></a>Utwórz zmienną środowiskową z wartością stałą

W obszarze *ENV*Określ *nazwę* i *wartość* dla każdej zmiennej środowiskowej, którą chcesz utworzyć na komputerze deweloperskim. *Nazwa* to zmienna środowiskowa, która będzie używana na komputerze deweloperskim, a *wartość* jest wartością. Na przykład:

```yaml
version: 0.1
env:
  - name: DEBUG_MODE
    value: "true"
```

W powyższym przykładzie jest tworzona zmienna środowiskowa o nazwie *DEBUG_MODE* o wartości *true*.

## <a name="example-kuberneteslocalprocessconfigyaml"></a>Przykład KubernetesLocalProcessConfig. YAML

Oto przykład kompletnego `KubernetesLocalProcessConfig.yaml` pliku:

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
  - name: DEBUG_MODE 
    value: "true"
```

## <a name="next-steps"></a>Następne kroki

Aby rozpocząć korzystanie z procesu lokalnego z usługą Kubernetes w celu nawiązania połączenia z lokalnym komputerem deweloperskim z klastrem, zobacz [Używanie procesu lokalnego z usługą Kubernetes with Visual Studio Code][local-process-kubernetes-vs-code] i [Używanie procesu lokalnego z programem Kubernetes za pomocą programu Visual Studio][local-process-kubernetes-vs].

[local-process-kubernetes-vs-code]: https://code.visualstudio.com/docs/containers/local-process-kubernetes
[local-process-kubernetes-vs]: local-process-kubernetes.md
