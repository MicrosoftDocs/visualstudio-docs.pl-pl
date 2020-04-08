---
title: Używanie środowiska laboratoryjnego dla devops
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- lab environment, test lab
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 499f335edabe77d001a1a2486e7b559abe6c7a8a
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880341"
---
# <a name="use-a-lab-environment-for-your-devops"></a>Użyj środowiska laboratoryjnego dla devops

Środowisko laboratoryjne to zbiór maszyn wirtualnych i fizycznych, których można używać do tworzenia i testowania aplikacji. Środowisko laboratoryjne może zawierać wiele ról potrzebnych do testowania aplikacji wielowarstwowych, takich jak stacje robocze, serwery sieci web i serwery baz danych. Ponadto można użyć przepływu pracy kompilacji i wdrażania testów ze środowiskiem laboratoryjnym, aby zautomatyzować proces tworzenia, wdrażania i uruchamiania automatycznych testów w aplikacji.

* **Użyj planu testów, aby uruchomić testy automatyczne** — można uruchomić kolekcję testów automatycznych, *nazywanych planem testów*i wyświetlić postęp.

* **Użyj przepływu pracy kompilacja-wdrażanie-test** — można użyć przepływu pracy kompilacja-wdrażanie-test do automatycznego testowania aplikacji wielowarstwowych. Typowym przykładem jest przepływ pracy, który uruchamia kompilację, wdraża pliki kompilacji na odpowiednich komputerach w środowisku laboratoryjnym, a następnie wykonuje zautomatyzowane testy. Ponadto można zaplanować przepływ pracy do uruchomienia w określonych odstępach czasu.

* **Zbieraj dane diagnostyczne ze wszystkich maszyn, nawet podczas testowania ręcznego** — możesz zbierać dane diagnostyczne z wielu maszyn jednocześnie. Na przykład podczas jednego przebiegu testowego można zbierać IntelliTrace, wpływ testu i inne formy danych z serwera sieci web, serwera bazy danych i klienta.

Oto przykłady typowych topologii środowiska laboratoryjnego:

| Topologia | Opis |
|---|---|
|![Topologia tylko serwera](../media/topology_backend.png)| To środowisko laboratoryjne ma *topologię serwera*, która jest często używana do uruchamiania testów ręcznych w aplikacjach serwerowych i która umożliwia testerom używanie własnych maszyn klienckich do weryfikacji błędów w środowisku. W topologii wewnętrznej bazy danych środowisko laboratoryjne zawiera tylko serwery. Korzystając z tego typu topologii, zazwyczaj łączysz się z serwerami w środowisku laboratoryjnym przy użyciu komputera klienckiego, który nie jest częścią środowiska.|
|![Środowisko laboratorium w chmurze](../media/topology_cloud.png)| To środowisko laboratoryjne zapewnia podobne możliwości i funkcje jak _topologia serwera_, ale usuwa wymagania dotyczące maszyn fizycznych lub wirtualnych działających w środowisku lokalnym; co może skrócić czas instalacji, uprościć konserwację i zminimalizować koszty. Konfigurowanie wielu witryn sieci Web i maszyn wirtualnych wraz z siecią niestandardową jest szybkie i łatwe w środowisku chmury, takim jak Microsoft Azure.|
|![Środowisko laboratoryjne klient-serwer](../media/topology_clientserver.png)| To środowisko laboratoryjne ma *topologię klient-serwer*, która jest często używana do testowania aplikacji, która ma składniki serwera i klienta. W topologii klienta/serwera wszystkie maszyny klienckie i serwerowe używane do testowania aplikacji znajdują się w środowisku laboratoryjnym. Korzystając z tej topologii, można zbierać dane testowe z każdej maszyny, która wpływa na testy.|

| | |
|---|---|
| ![ikona kamery filmowa dla wideo](../../install/media/video-icon.png) | [Obejrzyj film na temat](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Managing-lab-environments-for-testing) zarządzania środowiskami laboratoryjnymi do testowania. |

## <a name="use-the-cloud-with-azure-pipelines-or-team-foundation-server-build-and-release"></a>Korzystanie z chmury za pomocą potoków platformy Azure lub kompilacji i wersji serwera team foundation

Automatyzację testowania i wdrażania kompilacji i testowania można wykonywać przy użyciu funkcji [kompilacji i wersji](/azure/devops/pipelines/index?view=vsts) w team foundation server (TFS) i planach testów platformy Azure. Niektóre z korzyści są:

* Nie potrzebujesz kontrolera kompilacji ani kontrolera testów.
* Agent testowy jest instalowany za pośrednictwem zadania jako część kompilacji lub wydania.
* Kroki wdrażania można łatwo dostosować. Nie masz już ograniczeń w używaniu pojedynczego skryptu. Można również skorzystać z wielu zadań, które są dostępne w produkcie, a także w programie Visual Studio Marketplace.
* Nie musisz utrzymywać zestawów testowych. Testy można uruchamiać bezpośrednio z plików binarnych.
* Otrzymasz bogatsze środowisko raportowania wbudowanego dla testów, które są uruchamiane w ramach każdej kompilacji lub wersji.
* Można śledzić, które zasoby (wydanie, kompilacja, elementy robocze, zatwierdzenia) są obecnie wdrażane i testowane w każdym środowisku.
* Można dostosować i rozszerzyć automatyzację, aby łatwo wdrożyć do wielu środowisk testowych, a nawet do środowiska produkcyjnego.
* Automatyzację można zaplanować za każdym razem, gdy jest odprawa lub zatwierdzenie lub o określonej godzinie każdego dnia.

Aby uzyskać więcej informacji, zobacz [Używanie zarządzania kompilacją lub wydaniem](use-build-or-rm-instead-of-lab-management.md).

::: moniker range="vs-2017"
## <a name="use-the-visual-studio-lab-management-features-of-microsoft-test-manager"></a>Korzystanie z funkcji zarządzania laboratorium programu Visual Studio w programie Microsoft Test Manager

Podczas korzystania z programu Visual Studio Enterprise edition można tworzyć środowiska laboratoryjne i zarządzać nimi za pomocą funkcji zarządzania laboratorium programu Visual Studio w programie Microsoft Test Manager.

Lab Management automatycznie instaluje agentów testowych na każdym komputerze w twoim środowisku.

Jeśli używasz zarządzania laboratorium w połączeniu z Menedżerem maszyn wirtualnych programu System Center (SCVMM), można również uzyskać następujące korzyści podczas korzystania ze środowisk laboratoryjnych:

* **Szybkie odtwarzanie konfiguracji maszyn** — można przechowywać kolekcje maszyn wirtualnych, które są skonfigurowane do odtwarzania typowych środowisk produkcyjnych. Następnie można wykonać każde uruchomienie testu na nowej kopii przechowywanego środowiska.

* **Odtwórz dokładne warunki błędu** — gdy przebieg testu zakończy się niepowodzeniem, można przechowywać kopię stanu środowiska laboratoryjnego i uzyskać do niego dostęp z wyników kompilacji lub elementu pracy.

* **Uruchom wiele kopii środowiska laboratoryjnego w tym samym czasie** — można uruchomić wiele kopii środowiska laboratoryjnego w tym samym czasie bez konfliktów nazewnictwa.

### <a name="standard-environments-and-scvmm-environments"></a>Środowiska standardowe i środowiska SCVMM

Istnieją dwa typy środowisk laboratoryjnych, które można utworzyć za pomocą programu Visual Studio Lab Management: **środowiska standardowe** i **środowiska SCVMM.** Jednak możliwości każdego typu środowiska są różne.

**Środowiska standardowe:** mogą zawierać kombinację maszyn wirtualnych i fizycznych. Można również dodać maszyny wirtualne do standardowego środowiska, które są zarządzane przez struktury wirtualizacji innych firm. Ponadto środowiska standardowe nie wymagają dodatkowych zasobów serwera, takich jak serwer SCVMM.

**Środowiska SCVMM:** mogą zawierać tylko maszyny wirtualne zarządzane przez PROGRAM SCVMM (Menedżer maszyn wirtualnych centrum systemu), więc maszyny wirtualne w środowiskach SCVMM mogą być uruchamiane tylko w ramach wirtualizacji funkcji Hyper-V. Jednak środowiska SCVMM zapewniają następujące funkcje automatyzacji i zarządzania, które nie są dostępne w środowiskach standardowych:

- **Migawki środowiska:** Migawki środowiska zawierają stan środowiska laboratoryjnego, dzięki czemu można szybko przywrócić czyste środowisko lub zapisać stan środowiska, które zostało zmodyfikowane. Można również użyć przepływu pracy kompilacji i wdrażania-testu, aby zautomatyzować proces zapisywania i przywracania migawek środowiska.

- **Środowiska przechowywane:** Można przechowywać kopię środowiska SCVMM, a następnie wdrożyć wiele kopii tego środowiska.

- **Izolacja sieci:** Izolacja sieci umożliwia jednoczesne uruchamianie wielu identycznych kopii środowiska SCVMM bez konfliktów nazw komputerów.

- **Szablony maszyn wirtualnych:** Szablon maszyny wirtualnej to maszyna wirtualna, która usunęła swoją nazwę i inne identyfikatory. Gdy szablon maszyny Wirtualnej jest wdrażany w środowisku SCVMM, Program Microsoft Test Manager generuje nowe identyfikatory. Dzięki temu można wdrożyć wiele kopii maszyny wirtualnej w tym samym środowisku lub wielu środowiskach, a następnie uruchomić maszyny wirtualne jednocześnie.

- **Przechowywane maszyny wirtualne:** Maszyna wirtualna, która jest przechowywana w bibliotece projektu i zawiera unikatowe identyfikatory.

> [!NOTE]
> Zarządzanie laboratorium nie obsługuje programu SCVMM 2016.

Aby uzyskać informacje o SCVMM, zobacz [Menedżer maszyn wirtualnych](/azure/devops/pipelines/?view=vsts).

Środowiska standardowe i środowiska SCVMM obsługują wiele tych samych funkcji. Istnieją jednak pewne istotne różnice do rozważenia. W poniższej tabeli porównano funkcje, które są dostępne dla środowisk standardowych i środowisk SCVMM.

|Możliwości|Środowiska SCVMM|Środowiska standardowe|
|-|------------------------|-|
|**Testowanie**|||
|Uruchamianie testów ręcznych|Obsługiwane|Obsługiwane|
|Uruchamianie kodowanych interfejsów użytkownika i innych zautomatyzowanych testów|Obsługiwane|Obsługiwane|
|Błędy bogate w pliki przy użyciu kart diagnostycznych|Obsługiwane|Obsługiwane|
|**Tworzenie wdrożenia**|||
|Przepływy pracy automatycznego wdrażania i wdrażania podczas testów|Obsługiwane|Obsługiwane|
|**Tworzenie środowiska i zarządzanie nimi**|||
|Używanie maszyn fizycznych oprócz maszyn wirtualnych|Nieobsługiwane|Obsługiwane|
|Korzystanie z maszyn wirtualnych innych firm|Nieobsługiwane|Obsługiwane|
|Automatyczne instalowanie agentów testowych na maszynach w środowisku laboratoryjnym|Obsługiwane|Obsługiwane|
|Zapisywanie i wdrażanie stanu środowiska laboratoryjnego przy użyciu migawek środowiska|Obsługiwane|Nieobsługiwane|
|Tworzenie środowisk laboratoryjnych na podstawie szablonów maszyn wirtualnych|Obsługiwane|Nieobsługiwane|
|Środowisko start/stop/migawka|Obsługiwane|Nieobsługiwane|
|Łączenie się ze środowiskiem przy użyciu Przeglądarki środowiska|Obsługiwane|Obsługiwane|
|Uruchamianie wielu kopii środowiska w tym samym czasie przy użyciu izolacji sieci|Obsługiwane|Nieobsługiwane|

### <a name="lab-management-concepts"></a>Koncepcje zarządzania laboratorium

Oto kilka dodatkowych pojęć, które należy zapoznać się z przed kontynuowaniem:

|Termin|Opis|
|-|-----------------|
|Centrum laboratorium|Obszar programu Microsoft Test Manager, w którym tworzysz środowiska laboratoryjne i zarządzasz nimi.|
|Laboratorium projektu programu Azure DevOps|Kolekcja środowisk laboratoryjnych, które zostały skonfigurowane, dzięki czemu można połączyć się z nimi i uruchomić ich maszyn wirtualnych.|
|Biblioteka projektów programu Azure DevOps|Archiwum przechowywanych maszyn wirtualnych, szablonów i przechowywanych środowisk laboratoryjnych, które zostały zaimportowane do grupy hostów projektu. Elementy w bibliotece można używać w środowiskach SCVMM; jednak nie można dodać ich bezpośrednio do standardowego środowiska. Nie można uruchomić elementów w bibliotece; zamiast tego można ich używać do wdrażania nowego środowiska.|
|Wdrożone środowisko|Środowisko laboratoryjne, które zostało wdrożone w laboratorium projektu, dzięki czemu można połączyć się z nim i uruchomić jego maszyny.|

Aby uzyskać więcej informacji na temat zarządzania laboratorium, zobacz:

* [Zaplanuj swoje laboratorium](https://msdn.microsoft.com/library/ff756575%28v=vs.140%29.aspx)
* [Administrowanie laboratorium](https://msdn.microsoft.com/library/dd936084%28v=vs.140%29.aspx)
* [Konfiguracja dla środowisk SCVMM](https://msdn.microsoft.com/library/dd380687%28v=vs.140%29.aspx)
* [Zarządzanie uprawnieniami](https://msdn.microsoft.com/library/dd380760%28v=vs.140%29.aspx)
* [Zmienianie konfiguracji](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx)
* [Rozwiązywanie problemów](https://msdn.microsoft.com/library/ee853230%28v=vs.140%29.aspx)

Aby uzyskać informacje na temat konfigurowania środowisk, zobacz:

* [Tworzenie i zwalnianie środowisk w chmurze](use-build-or-rm-instead-of-lab-management.md)
* [Standardowe środowiska laboratoryjne](https://msdn.microsoft.com/library/ee390842.aspx)
* [Środowiska SCVMM (wirtualne)](https://msdn.microsoft.com/library/ee943322.aspx)
* [Tworzenie i używanie środowiska izolowanego sieci](https://msdn.microsoft.com/library/ee518924.aspx)
::: moniker-end

## <a name="see-also"></a>Zobacz też

* [Instalowanie i konfigurowanie agentów testowych](../../test/lab-management/install-configure-test-agents.md)
* [Przewodnik po zarządzaniu laboratorium w programie Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2015/04/22/library-of-tooling-and-guidance-solutions-aka-msvsarsolutions/)
* [Blog usługi Microsoft DevOps](https://devblogs.microsoft.com/devops/)
