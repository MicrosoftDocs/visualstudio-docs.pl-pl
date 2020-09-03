---
title: Jak działa proces lokalny z usługą Kubernetes
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: conceptual
description: Opisuje procesy związane z używaniem procesu lokalnego z usługą Kubernetes w celu połączenia komputera deweloperskiego z klastrem Kubernetes
keywords: Proces lokalny z Kubernetes, Docker, Kubernetes, Azure, Containers
monikerRange: '>=vs-2019'
manager: jillfra
author: ghogen
ms.author: ghogen
ms.openlocfilehash: 5b6c07d5987c52d818a35babd16681652ddf5830
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "87913263"
---
# <a name="how-local-process-with-kubernetes-works"></a>Jak działa proces lokalny z usługą Kubernetes

Proces lokalny z programem Kubernetes umożliwia uruchamianie i debugowanie kodu na komputerze deweloperskim, przy jednoczesnym połączeniu z klastrem Kubernetes z pozostałą częścią aplikacji lub usług. Na przykład jeśli masz dużą architekturę mikrousług z wieloma zależnymi usługami i bazami danych, replikowanie tych zależności na komputerze deweloperskim może być trudne. Ponadto Kompilowanie i wdrażanie kodu w klastrze Kubernetes dla każdej zmiany kodu podczas programowania w pętli wewnętrznej może być powolne, czasochłonne i trudne do użycia z debugerem.

Proces lokalny z Kubernetes pozwala uniknąć konieczności kompilowania i wdrażania kodu w klastrze przez utworzenie połączenia bezpośrednio między komputerem deweloperskim i klastrem. Połączenie komputera deweloperskiego z klastrem podczas debugowania umożliwia szybkie testowanie i opracowywanie usługi w kontekście pełnej aplikacji bez konieczności tworzenia żadnej konfiguracji platformy Docker lub Kubernetes.

Proces lokalny z Kubernetes przekierowuje ruch między podłączonym klastrem Kubernetes i komputerem deweloperskim. To przekierowywanie ruchu umożliwia kod na komputerze deweloperskim i usługach uruchomionych w klastrze Kubernetes, aby komunikować się tak, jakby znajdowały się w tym samym klastrze Kubernetes. Proces lokalny z usługą Kubernetes umożliwia także replikować zmienne środowiskowe i zainstalowane woluminy dostępne dla zasobników w klastrze Kubernetes na komputerze deweloperskim. Zapewnianie dostępu do zmiennych środowiskowych i zainstalowanych woluminów na komputerze deweloperskim pozwala szybko korzystać z kodu bez konieczności ręcznego replikowania tych zależności.

> [!WARNING]
> Proces lokalny dla Kubernetes jest przeznaczony do użycia tylko w scenariuszach deweloperskich i testowych. Nie jest ona przeznaczona do użycia ani nie jest obsługiwana w przypadku klastrów produkcyjnych lub usług na żywo w aktywnym użytkowaniu.

## <a name="using-local-process-with-kubernetes"></a>Używanie procesu lokalnego z Kubernetes

Aby można było używać procesu lokalnego z programem Kubernetes w programie Visual Studio, wymagany jest [program Visual studio 2019][visual-studio] w wersji 16,7 Preview 4 lub nowszy z systemem Windows 10 z zainstalowanym obciążeniem programu *ASP.NET i sieci Web* oraz zainstalowaną [proces lokalny][lpk-extension] . W przypadku korzystania z procesu lokalnego z usługą Kubernetes w celu nawiązania połączenia z klastrem Kubernetes można przekierować cały ruch do i z istniejącego obszaru klastra na komputer deweloperski.

> [!NOTE]
> W przypadku korzystania z procesu lokalnego z usługą Kubernetes zostanie wyświetlony monit o podanie nazwy usługi, która ma zostać przekierowana na komputer deweloperski. Ta opcja jest wygodnym sposobem identyfikacji pod kątem przekierowania. Wszystkie przekierowania między klastrem Kubernetes a komputerem deweloperskim dotyczą usługi pod.

Gdy proces lokalny z usługą Kubernetes nawiązuje połączenie z klastrem,:

* Zostanie wyświetlony komunikat z prośbą o skonfigurowanie usługi do zamiany na klaster, port na komputerze deweloperskim, który będzie używany w kodzie, oraz zadanie uruchamiania dla kodu jako akcję jednorazową.
* Zastępuje kontener w obszarze na klastrze z kontenerem zdalnego agenta, który przekierowuje ruch do komputera deweloperskiego.
* Uruchamia funkcję [polecenia kubectl port-forward][kubectl-port-forward] na komputerze deweloperskim, aby przekazywać ruch z komputera deweloperskiego do zdalnego agenta działającego w klastrze.
* Zbiera informacje o środowisku z klastra przy użyciu zdalnego agenta. Informacje o środowisku obejmują zmienne środowiskowe, widoczne usługi, instalacje woluminów i instalacje tajne.
* Konfiguruje środowisko w programie Visual Studio, aby usługa na komputerze deweloperskim mogła uzyskiwać dostęp do tych samych zmiennych, tak jakby były one uruchomione w klastrze.  
* Aktualizuje plik hosts w celu mapowania usług w klastrze na lokalne adresy IP na komputerze deweloperskim. Te wpisy plików hostów umożliwiają uruchamianie kodu na komputerze deweloperskim w celu wykonywania żądań do innych usług uruchomionych w klastrze. Aby można było zaktualizować plik hosts, proces lokalny z usługą Kubernetes będzie pytał o dostęp administratora na komputerze deweloperskim podczas nawiązywania połączenia z klastrem.
* Uruchamia uruchamianie i debugowanie kodu na komputerze deweloperskim. W razie potrzeby proces lokalny z usługą Kubernetes będzie zwalniać wymagane porty na komputerze deweloperskim przez zatrzymywanie usług lub procesów, które aktualnie korzystają z tych portów.

Po nawiązaniu połączenia z klastrem można uruchomić i debugować kod natywnie na komputerze bez kontenerach, a kod może bezpośrednio współdziałać z resztą klastra. Każdy ruch sieciowy odbierany przez agenta zdalnego jest przekierowywany do portu lokalnego określonego podczas połączenia, dzięki czemu kod natywnie uruchomiony może zaakceptować i przetworzyć ten ruch. Zmienne środowiskowe, woluminy i wpisy tajne z klastra są udostępniane w kodzie uruchomionym na komputerze deweloperskim. Ponadto ze względu na to, że wpisy pliku Hosts i przekazywanie portów zostały dodane do komputera dewelopera przez proces lokalny z Kubernetes, kod może wysyłać ruch sieciowy do usług uruchomionych w klastrze przy użyciu nazw usług z klastra, a ruch jest przesyłany do usług uruchomionych w klastrze. Ruch jest kierowany między komputerem deweloperskim i klastrem przez cały czas, gdy masz połączenie.

Ponadto proces lokalny z Kubernetes zapewnia sposób replikowania zmiennych środowiskowych i zainstalowanych plików dostępnych dla zasobników w klastrze na komputerze deweloperskim za pomocą `KubernetesLocalProcessConfig.yaml` pliku. Możesz również użyć tego pliku, aby utworzyć nowe zmienne środowiskowe i instalacje woluminów.

> [!NOTE]
> Na czas trwania połączenia z klastrem (plus dodatkowe 15 minut) proces lokalny z usługą Kubernetes uruchamia proces o nazwie *endpointmanager* z uprawnieniami administratora na komputerze lokalnym.

## <a name="additional-configuration-with-kuberneteslocalprocessconfigyaml"></a>Dodatkowa konfiguracja z KubernetesLocalProcessConfig. YAML

`KubernetesLocalProcessConfig.yaml`Plik umożliwia replikowanie zmiennych środowiskowych i zainstalowanych plików dostępnych dla Twojego zasobnika w klastrze. Więcej informacji o dodatkowych opcjach konfiguracji znajduje się w temacie [Configure Local Process with Kubernetes][using-config-yaml].

## <a name="using-routing-capabilities-for-developing-in-isolation"></a>Korzystanie z funkcji routingu do programowania w izolacji

Domyślnie proces lokalny z usługą Kubernetes przekierowuje cały ruch dla usługi do komputera deweloperskiego. Istnieje również możliwość użycia funkcji routingu do przekierowywania tylko żądań do usługi pochodzącej z poddomeny do komputera deweloperskiego. Dzięki tym funkcjom routingu można korzystać z procesu lokalnego z Kubernetes, aby rozwijać izolację i unikać zakłócania innego ruchu w klastrze.

Poniższe animacje przedstawiają dwóch deweloperów pracujących nad tym samym klastrem w izolacji:

![Animowanie izolowania obrazu GIF](media/local-process-kubernetes/lpk-graphic-isolated.gif)

Po włączeniu pracy w trybie izolacji proces lokalny z programem Kubernetes wykonuje następujące czynności oprócz nawiązywania połączenia z klastrem Kubernetes:

* Sprawdza, czy klaster Kubernetes nie ma włączonej Azure Dev Spaces.
* Replikuje wybraną usługę w klastrze w tej samej przestrzeni nazw i dodaje etykietę *Routing.VisualStudio.IO/Route-from=service_name* i *Routing.VisualStudio.IO/Route-on-header=Kubernetes-Route-as: GENERATED_NAME* adnotację.
* Konfiguruje i uruchamia Menedżera routingu w tej samej przestrzeni nazw klastra Kubernetes. Menedżer routingu używa selektora etykiet do wyszukiwania etykiet *Routing.VisualStudio.IO/Route-from=service_name* i  *Routing.VisualStudio.IO/Route-on-header=Kubernetes-Route-as: GENERATED_NAME* adnotacji podczas konfigurowania routingu w przestrzeni nazw.

Jeśli proces lokalny z Kubernetes wykryje, że Azure Dev Spaces jest włączona w klastrze Kubernetes, zostanie wyświetlony monit o wyłączenie Azure Dev Spaces przed użyciem procesu lokalnego z Kubernetes.

Podczas uruchamiania Menedżer routingu wykonuje następujące czynności:
* Duplikuje wszystkie ingresses Znalezione w przestrzeni nazw za pomocą *GENERATED_NAME* dla domeny podrzędnej. 
* Tworzy wysłannika pod dla każdej usługi skojarzonej z powielonym ingresses z poddomeną *GENERATED_NAME* .
* Tworzy dodatkowy wysłannika pod względem usługi, w której pracujesz w izolacji. Pozwala to na kierowanie żądań z poddomeną do komputera deweloperskiego.
* Konfiguruje reguły routingu dla każdego wysłannika pod względem obsługi routingu dla usług z poddomeną.

Gdy w klastrze zostanie odebrane żądanie z poddomeną *GENERATED_NAME* , do żądania zostanie dodany nagłówek *Kubernetes-Route-as = GENERATED_NAME* . Wysłannika, które obsługują Routing, który żąda odpowiedniej usługi w klastrze. Jeśli żądanie jest kierowane do usługi, która jest przetwarzana w izolacji, żądanie jest przekierowywane do komputera deweloperskiego przez agenta zdalnego.

Gdy w klastrze zostanie odebrane żądanie bez poddomeny *GENERATED_NAME* , nagłówek nie zostanie dodany do żądania. Wysłannika, które obsługują Routing, który żąda odpowiedniej usługi w klastrze. Jeśli żądanie jest kierowane do usługi, która jest zastępowana, to żądanie jest wysyłane do oryginalnej usługi zamiast agenta zdalnego.

> [!IMPORTANT]
> Każda usługa w klastrze musi przesłać dalej nagłówek *Kubernetes-Route-as = GENERATED_NAME* podczas wykonywania dodatkowych żądań. Na przykład gdy *Usługa Service* w odbierze żądanie, wysyła żądanie *serviceB* przed zwróceniem odpowiedzi. W tym przykładzie *Usługa Service* . musi przesłać dalej nagłówek *Kubernetes-Route-as = GENERATED_NAME* w żądaniu do *serviceB*. Niektóre języki, takie jak [ASP.NET][asp-net-header], mogą mieć metody obsługi propagacji nagłówka.

Po rozłączeniu z klastrem domyślnie proces lokalny z programem Kubernetes usunie wszystkie wysłannikay i powieloną usługę. 

> KORYGUJĄC Wdrożenie i usługa Menedżera routingu pozostaną uruchomione w Twojej przestrzeni nazw. Aby usunąć wdrożenie i usługę, uruchom następujące polecenia dla swojej przestrzeni nazw.
>
> ```azurecli
> kubectl delete deployment routingmanager-deployment -n NAMESPACE
> kubectl delete service routingmanager-service -n NAMESPACE
> ```

## <a name="diagnostics-and-logging"></a>Diagnostyka i rejestrowanie

W przypadku korzystania z procesu lokalnego z Kubernetes w celu nawiązania połączenia z klastrem dzienniki diagnostyczne z klastra są rejestrowane w katalogu *tymczasowym* komputera deweloperskiego w *procesie lokalnym z* folderem Kubernetes.

## <a name="limitations"></a>Ograniczenia

Proces lokalny z Kubernetes ma następujące ograniczenia:

* Proces lokalny z usługą Kubernetes przekierowuje ruch dla jednej usługi do komputera deweloperskiego. Nie można użyć procesu lokalnego z usługą Kubernetes w celu przekierowania wielu usług w tym samym czasie.
* Aby można było połączyć się z tą usługą, usługa musi być objęta usługą. Nie można nawiązać połączenia z usługą z wieloma zasobnikami, takimi jak usługa z replikami.
* W przypadku procesu lokalnego z usługą Kubernetes w celu pomyślnego nawiązania połączenia na komputerze może znajdować się tylko jeden kontener uruchomiony w tym pod. Proces lokalny z usługą Kubernetes nie może połączyć się z usługami za pomocą zasobników z dodatkowymi kontenerami, takimi jak kontenery przyczepek z systemem.
* Proces lokalny z Kubernetes wymaga podniesionych uprawnień do uruchamiania na komputerze deweloperskim, aby można było edytować plik Hosts.
* Nie można używać procesu lokalnego z usługą Kubernetes w przypadku klastrów z włączonym Azure Dev Spaces.

### <a name="local-process-with-kubernetes-and-clusters-with-azure-dev-spaces-enabled"></a>Proces lokalny z Kubernetes i klastrami z włączonym Azure Dev Spaces

Nie można użyć procesu lokalnego z Kubernetes w klastrze z włączonym Azure Dev Spaces. Jeśli chcesz użyć procesu lokalnego z Kubernetes w klastrze z włączonym Azure Dev Spaces, musisz wyłączyć Azure Dev Spaces przed nawiązaniem połączenia z klastrem.

## <a name="next-steps"></a>Następne kroki

Aby rozpocząć korzystanie z procesu lokalnego z usługą Kubernetes w celu nawiązania połączenia z lokalnym komputerem deweloperskim z klastrem, zobacz [Korzystanie z procesu lokalnego z Kubernetes](local-process-kubernetes.md).

[asp-net-header]: https://www.nuget.org/packages/Microsoft.AspNetCore.HeaderPropagation/
[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest
[local-process-kubernetes-vs]: local-process-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[lpk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[using-config-yaml]: configure-local-process-with-kubernetes.md