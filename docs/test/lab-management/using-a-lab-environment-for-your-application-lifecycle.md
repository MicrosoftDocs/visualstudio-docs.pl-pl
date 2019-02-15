---
title: Użyć środowiska laboratoryjnego do operacji deweloperskich
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- lab environment, test lab
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 38039bd98ab1a2d8407945f578e47d325475d4cd
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318007"
---
# <a name="use-a-lab-environment-for-your-devops"></a>Użyć środowiska laboratoryjnego dla Twojego metodyki devops

Środowisko laboratoryjne to zbiór maszyn wirtualnych i fizycznych, które służą do tworzenia i testowania aplikacji. Środowisko laboratoryjne może zawierać wiele ról potrzebnych do testowania aplikacji wielowarstwowych, takich jak stacje robocze, serwery sieci web i serwery baz danych. Ponadto umożliwia przepływu pracy kompilacja wdrożenie test ze środowiskiem laboratoryjnym zautomatyzować proces kompilowania, wdrażania i uruchamiania testów automatycznych w swojej aplikacji.

* **Użyj planu testów do uruchamiania testów automatycznych** — możesz uruchomić zbiór testów automatycznych, o nazwie *plan testu*i wyświetlić postęp.

* **Używanie przepływu pracy kompilacja wdrożenie test** — przepływ pracy kompilacja wdrożenie test można użyć do automatycznego testowania aplikacji wielowarstwowych. Typowym przykładem jest przepływ pracy, który uruchamia kompilację, wdroży plików kompilacji na odpowiednich komputerach w środowisku laboratoryjnym, a następnie oblicza testów automatycznych. Ponadto można zaplanować przepływu pracy do uruchamiania w określonych odstępach czasu.

* **Zbieranie danych diagnostycznych z wszystkich maszyn, nawet podczas testowania ręcznego** — umożliwia zbieranie danych diagnostycznych z wiele maszyn jednocześnie. Można na przykład podczas jednego przebiegu testu, zbierania IntelliTrace, test, wpływ i inne formy dane z serwera sieci web, serwer bazy danych i klienta.

Oto przykłady typowych topologii środowiska laboratorium:

| Topologia | Opis |
|---|---|
|![Tylko topologii serwerów](../media/topology_backend.png)| To środowisko laboratoryjne ma *topologii serwerów*, która jest często używana do uruchomienia testów ręcznych w aplikacji serwerowych i pozwalający testerów można zweryfikować usterki w środowisku za pomocą ich własnych komputerów klienckich. W topologii wewnętrznej bazy danych w swoim środowisku laboratoryjnym zawiera tylko serwery. Korzystając z tego typu używanej topologii, zwykle nawiązaniu połączenia z serwerami w środowisku laboratoryjnym nie przy użyciu komputera klienta, który jest częścią środowiska.|
|![Środowisko laboratoryjne chmury](../media/topology_cloud.png)| To środowisko laboratoryjne zapewnia podobne możliwości i funkcji jako _topologii serwerów_, ale eliminuje konieczność fizycznych lub maszyn wirtualnych działających w środowisku lokalnym; można skrócić czas instalacji, Uprość Konserwacja i zminimalizowania kosztów. Konfigurowanie wielu witryn sieci Web i maszyn wirtualnych, wraz z niestandardowych sieci jest szybkie i łatwe w środowisku chmury, takich jak Microsoft Azure.|
|![Środowisko laboratoryjne klient serwer](../media/topology_clientserver.png)| To środowisko laboratoryjne ma *topologii klient serwer*, która jest często używana do testowania aplikacji, która ma składników serwera i klienta. W topologii klient/serwer wszystkich komputerów klienckich i serwerów, umożliwia przetestowanie aplikacji znajdują się w swoim środowisku laboratoryjnym. Gdy używasz tej topologii, możesz zebrać dane testowe z każdej maszynie, która ma wpływ na testy.|

| | |
|---|---|
| ![Ikona aparatu filmu wideo](../../install/media/video-icon.png) | [Obejrzyj film wideo](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Managing-lab-environments-for-testing) na zarządzanie środowiskami laboratoryjnymi na potrzeby testowania. |

## <a name="use-the-cloud-with-azure-pipelines-or-team-foundation-server-build-and-release"></a>Korzystaj z chmury, za pomocą potoków usługi Azure lub kompilacji programu Team Foundation Server i wersji

Można wykonać testów automatycznych i kompilacja wdrożenie test automation za pomocą [kompilowania i wydawania](/azure/devops/pipelines/index?view=vsts) funkcji w Team Foundation Server (TFS) i plany testów platformy Azure. Niektóre z korzyści to:

* Nie trzeba kontrolera kompilacji lub kontrolera testów.
* Agent testowy jest zainstalowany za pomocą zadania jako część kompilacji lub wydania.
* To można łatwo dostosować procedury wdrażania. Nie jesteś już ograniczone do korzystania z jednego skryptu. Możesz również korzystać z zalet wiele zadań, które są dostępne w ramach produktu, a także jak Visual Studio Marketplace.
* Nie trzeba utrzymywać zestawów testów. Można bezpośrednio uruchomić testy z plików binarnych.
* Uzyskasz bardziej zaawansowane wbudowane, raportowanie środowisko dla testów uruchamianych w każdej kompilacji lub wydania.
* Trwałe, które można śledzić (wydania, tworzenie elementów roboczych, zatwierdzeń) są obecnie wdrożone i przetestowane w każdym środowisku.
* Można dostosować i rozszerzyć automatyzację, aby łatwo wdrożyć do wielu środowisk testowych, a nawet do środowiska produkcyjnego.
* Można zaplanować automatyzacji, który ma być wykonywana zawsze, gdy występuje lub ewidencjonowania zatwierdzenia lub codziennie o określonej godzinie.

Aby uzyskać więcej informacji, zobacz [zarządzania Użyj kompilacji lub wydania](use-build-or-rm-instead-of-lab-management.md).

## <a name="use-the-visual-studio-lab-management-features-of-microsoft-test-manager"></a>Korzystanie z funkcji programu Visual Studio Lab Management programu Microsoft Test Manager

Można tworzyć i zarządzać środowiskami laboratoryjnymi za pomocą funkcji Visual Studio Lab Management programu Microsoft Test Manager, korzystając z programu Visual Studio 2017 Enterprise edition.

Lab Management automatycznie instaluje agentów testowych na każdym komputerze w danym środowisku.

Jeśli używasz programu Lab Management w połączeniu z Menedżera maszyny wirtualnej System Center (SCVMM) możesz również daje następujące korzyści za pomocą środowisk laboratoryjnych:

* **Szybko odtwarzać konfiguracje maszyny** — możesz przechowywać kolekcji maszyn wirtualnych, które są skonfigurowane do odtworzenia środowisk produkcji typowych. Następnie należy wykonać każdy test na nową kopię przechowywanych środowiska.

* **Odtwórz dokładne warunki błędu** — w przypadku testu zakończy się niepowodzeniem, można przechowywać kopię stan środowiska laboratoryjnego i uzyskać do niego dostęp z wyników kompilacji lub elementu roboczego.

* **Uruchamianie wielu kopii środowiska laboratoryjnego w tym samym czasie** — można uruchomić wielu kopii środowiska laboratoryjnego w tym samym czasie bez konfliktów nazw.

### <a name="standard-environments-and-scvmm-environments"></a>Środowiska standardowe oraz środowiska SCVMM

Istnieją dwa rodzaje środowisk laboratoryjnych, które można utworzyć za pomocą programu Visual Studio Lab Management: **standardowych środowisk** i **środowisk SCVMM**. Jednak możliwości każdego typu środowiska są różne.

**Standardowych środowisk:** może zawierać zarówno maszyn wirtualnych i fizycznych. Maszyny wirtualne można również dodać do standardowego środowiska, które są zarządzane przez platformy wirtualizacji innej firmy. Oprócz standardowych środowisk nie wymagają zasobów dodatkowy serwer, taki jak serwer programu SCVMM.

**Środowisk programu SCVMM:** może zawierać tylko maszyny wirtualne, które są zarządzane przez program SCVMM (System Center Virtual Machine Manager), więc maszyn wirtualnych w środowiskach SCVMM mogą działać tylko na środowisku wirtualizacji funkcji Hyper-V. Jednak środowisk SCVMM zapewniają następujące funkcje automatyzacji i zarządzania, które nie są dostępne w standardowych środowisk:

- **Migawki środowiska:** Migawki środowiska zawiera stan środowiska laboratoryjnego, dzięki czemu można szybko przywrócić czystego środowiska lub zapisywania stanu środowiska, który został zmodyfikowany. Przepływ pracy kompilacja wdrożenie test umożliwia również Automatyzowanie zapisywanie i przywracanie migawki środowiska.

- **Przechowywane środowiska:** Możesz zapisać kopię środowiska SCVMM i następnie wdrożono wiele kopii tego środowiska.

- **Izolacja sieci:** Izolacja sieci umożliwia jednoczesne uruchamianie wielu kopii identycznych środowiska SCVMM, bez konfliktów nazw komputerów.

- **Szablony maszyn wirtualnych:** Szablon maszyny wirtualnej jest maszyny wirtualnej, który miał jego nazwy i usunąć innych identyfikatorów. Po wdrożeniu szablonu maszyny Wirtualnej w środowisku SCVMM, Microsoft Test Manager generuje nowych identyfikatorów. Dzięki temu możesz wdrożyć wiele kopii maszyny wirtualnej, w tym samym środowisku, lub do wielu środowisk, a następnie uruchom maszyn wirtualnych jednocześnie.

- **Przechowywane maszyny wirtualne:** Maszyna wirtualna, jest przechowywany w bibliotece projektu, który zawiera unikatowych identyfikatorów.

> [!NOTE]
> Lab Management nie obsługuje programie SCVMM 2016.

Aby uzyskać informacji na temat programu SCVMM, zobacz [programu Virtual Machine Manager](/azure/devops/pipelines/?view=vsts).

Środowiska standardowe oraz środowiska SCVMM obsługuje wiele z tych samych funkcji. Istnieją jednak pewne ważne różnice wziąć pod uwagę. W poniższej tabeli porównano funkcje, które są dostępne dla środowiska standardowe oraz środowiska SCVMM.

|Możliwość|Środowiska SCVMM|Środowisk standardowych|
|-|------------------------|-|
|**Testowanie**|||
|Uruchamianie testów ręcznych|Obsługiwane|Obsługiwane|
|Uruchom kodowane interfejsu użytkownika i innych testów automatycznych|Obsługiwane|Obsługiwane|
|Zgłaszanie poważnych usterek za pomocą adapterów diagnostycznych|Obsługiwane|Obsługiwane|
|**Tworzenie wdrożenia**|||
|Automatyczne przepływy pracy kompilacja wdrażanie testy|Obsługiwane|Obsługiwane|
|**Tworzenie środowiska i zarządzanie nimi**|||
|Maszyny fizyczne użycie oprócz maszyn wirtualnych|Nieobsługiwane|Obsługiwane|
|Użyj maszyn wirtualnych innych firm|Nieobsługiwane|Obsługiwane|
|Automatycznie zainstalować agentów testowych na komputerach w środowisku laboratoryjnym|Obsługiwane|Obsługiwane|
|Zapisz i wdróż stan środowiska laboratoryjnego, korzystanie z environment snapshots|Obsługiwane|Nieobsługiwane|
|Tworzenie środowisk laboratoryjnych z szablonów maszyny Wirtualnej|Obsługiwane|Nieobsługiwane|
|Start/stop/wykonaj migawkę środowiska|Obsługiwane|Nieobsługiwane|
|Połącz ze środowiskiem za pomocą podglądu środowiska|Obsługiwane|Obsługiwane|
|Uruchamianie wielu kopii środowiska, w tym samym czasie przy użyciu izolacji sieciowej|Obsługiwane|Nieobsługiwane|

### <a name="lab-management-concepts"></a>Pojęcia dotyczące usługi Lab management

Poniżej przedstawiono niektóre dodatkowe pojęcia, które należy poznać przed kontynuowaniem:

|Termin|Opis|
|-|-----------------|
|Centrum laboratoryjnego|Obszar programu Microsoft Test Manager którym tworzyć i zarządzać środowiskami laboratoryjnymi.|
|Laboratorium projektu DevOps platformy Azure|Kolekcja środowiska laboratoryjne, które tak skonfigurowany, można połączyć z nich i uruchamianie maszyn wirtualnych.|
|Biblioteki projektu DevOps platformy Azure|Archiwum przechowywanych maszyn wirtualnych, szablonów i środowisk laboratoryjnych przechowywanych, które zostały zaimportowane do grupy hostów projektu. Można użyć elementów w bibliotece z SCVMM environments; jednak nie możesz dodać je bezpośrednio do standardowego środowiska. Nie można uruchomić elementy w bibliotece; Zamiast tego możesz użyć je do wdrożenia nowego środowiska.|
|Wdrożonego środowiska|Środowisko laboratoryjne, które zostaną wdrożone do środowiska laboratoryjnego projektu tak, że możesz nawiązać z nim i uruchomić swoich komputerów.|

Aby uzyskać więcej informacji o programie lab management zobacz:

* [Planowanie środowiska laboratoryjnego](https://msdn.microsoft.com/library/ff756575%28v=vs.140%29.aspx)
* [Administrowanie środowiska laboratoryjnego](https://msdn.microsoft.com/library/dd936084%28v=vs.140%29.aspx)
* [Konfigurowanie na potrzeby środowisk programu SCVMM](https://msdn.microsoft.com/library/dd380687%28v=vs.140%29.aspx)
* [Zarządzaj uprawnieniami](https://msdn.microsoft.com/library/dd380760%28v=vs.140%29.aspx)
* [Ustawienia zmian](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx)
* [Rozwiązywanie problemów](https://msdn.microsoft.com/library/ee853230%28v=vs.140%29.aspx)

Aby uzyskać informacji na temat konfigurowania środowiska zobacz:

* [Kompilowania i wydawania środowisk w chmurze](use-build-or-rm-instead-of-lab-management.md)
* [Standardowe środowiska laboratoryjne](https://msdn.microsoft.com/library/ee390842.aspx)
* [Środowiska (wirtualne) SCVMM](https://msdn.microsoft.com/library/ee943322.aspx)
* [Tworzenie i używanie izolowane środowisko sieciowe](https://msdn.microsoft.com/library/ee518924.aspx)

## <a name="see-also"></a>Zobacz także

* [Instalowanie i konfigurowanie agentów testowych](../../test/lab-management/install-configure-test-agents.md)
* [Podręcznik programu Visual Studio Lab Management](https://aka.ms/vsarsolutions)
* [Microsoft DevOps Blog](https://devblogs.microsoft.com/devops/)
