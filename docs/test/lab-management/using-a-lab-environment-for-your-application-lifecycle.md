---
title: Używanie środowiska laboratoryjnego do DevOps
description: Dowiedz się więcej o środowiskach laboratoryjnych i sposobach używania chmury z Azure Pipelines lub Team Foundation Server kompilowania i wydawania.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: how-to
helpviewer_keywords:
- lab environment, test lab
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: a16b8df2539272f96f0211fdf08e32fe4e4eaac8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887825"
---
# <a name="use-a-lab-environment-for-your-devops"></a>Używanie środowiska laboratoryjnego do DevOps

Środowisko laboratoryjne to zbiór maszyn wirtualnych i fizycznych, które służą do tworzenia i testowania aplikacji. Środowisko laboratoryjne może zawierać wiele ról, które są konieczne do testowania aplikacji wielowarstwowych, takich jak stacje robocze, serwery sieci Web i serwery baz danych. Ponadto można użyć przepływu pracy Kompilacja-Wdrażanie-test w środowisku laboratoryjnym, aby zautomatyzować proces kompilowania, wdrażania i uruchamiania zautomatyzowanych testów w aplikacji.

* **Korzystanie z planu testu do uruchamiania testów automatycznych** — można uruchomić kolekcję zautomatyzowanych testów, nazywanych *planem testu*, i wyświetlić postęp.

* **Użyj przepływu pracy Kompilacja-Wdrażanie-test** — możesz użyć przepływu pracy Kompilacja-Wdrażanie-test do automatycznego testowania aplikacji wielowarstwowych. Typowym przykładem jest przepływ pracy, który uruchamia kompilację, wdraża pliki kompilacji na odpowiednich maszynach w środowisku laboratoryjnym, a następnie wykonuje testy automatyczne. Ponadto można zaplanować uruchamianie przepływu pracy w określonych odstępach czasu.

* **Zbieraj dane diagnostyczne ze wszystkich maszyn, nawet podczas testowania ręcznego** — można zbierać dane diagnostyczne z wielu maszyn jednocześnie. Na przykład podczas jednego przebiegu testu można zbierać IntelliTrace, wpływ testów i inne formy danych z serwera sieci Web, serwera bazy danych i klienta.

Poniżej przedstawiono przykłady typowych topologii środowiska laboratoryjnego:

| Topologia | Opis |
|---|---|
|![Topologia tylko serwera](../media/topology_backend.png)| To środowisko laboratoryjne ma *topologię serwera*, która jest często używana do uruchamiania ręcznych testów w aplikacjach serwerowych, co umożliwia testerom używanie własnych maszyn klienckich do weryfikowania usterek w środowisku. W topologii zaplecza środowisko laboratoryjne zawiera tylko serwery. W przypadku korzystania z tego typu topologii zwykle nawiązuje się połączenie z serwerami w środowisku laboratoryjnym przy użyciu komputera klienckiego, który nie jest częścią środowiska.|
|![Środowisko laboratoryjne w chmurze](../media/topology_cloud.png)| To środowisko laboratoryjne zapewnia podobne funkcje i funkcje, co _topologia serwera_, ale eliminuje wymaganie dla maszyn fizycznych lub wirtualnych działających w środowisku lokalnym; pozwala to skrócić czas instalacji, uprościć konserwację i zminimalizować koszt. Konfigurowanie wielu witryn sieci Web i maszyn wirtualnych wraz z niestandardowymi sieciami jest szybkie i łatwe w środowisku chmury, takim jak Microsoft Azure.|
|![Środowisko programu Client-Server Lab](../media/topology_clientserver.png)| To środowisko laboratoryjne ma *topologię klienta-serwera*, która jest często używana do testowania aplikacji, która ma składniki serwera i klienta. W topologii klient/serwer wszystkie komputery klienckie i serwery używane do testowania aplikacji są w środowisku laboratoryjnym. Korzystając z tej topologii, można zbierać dane testowe z każdego komputera, który ma wpływ na testy.|

:::row:::
    :::column:::
        ![ikona aparatu filmu wideo](../../install/media/video-icon.png)
    :::column-end:::
    :::column:::
        [Obejrzyj wideo,](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Managing-lab-environments-for-testing) aby zarządzać środowiskami laboratoryjnymi na potrzeby testowania.
    :::column-end:::
:::row-end:::

## <a name="use-the-cloud-with-azure-pipelines-or-team-foundation-server-build-and-release"></a>Korzystanie z chmury z Azure Pipelines lub Team Foundation Server kompilowania i wydawania

Można przeprowadzać zautomatyzowane testowanie i automatyzację Kompilacja-Wdrażanie-test przy użyciu funkcji [kompilowania i](/azure/devops/pipelines/index?view=vsts&preserve-view=true) wydawania w Team Foundation Server (TFS) i Azure test Plans. Oto niektóre z korzyści:

* Kontroler kompilacji lub kontroler testów nie jest potrzebny.
* Agent testowy jest instalowany za pomocą zadania w ramach kompilacji lub wydania.
* Można łatwo dostosować kroki wdrażania. Nie można już używać pojedynczego skryptu. Możesz również skorzystać z wielu zadań dostępnych w produkcie, jak również w Visual Studio Marketplace.
* Nie musisz obsługiwać zestawów testów. Można bezpośrednio uruchamiać testy z plików binarnych.
* Uzyskasz bogatsze wbudowane środowisko raportowania dla testów, które są uruchamiane w ramach każdej kompilacji lub wydania.
* Można śledzić, które zasoby (wydanie, kompilacja, elementy robocze, zatwierdzenia) są obecnie wdrażane i testowane w każdym środowisku.
* Możesz dostosować i zwiększyć automatyzację, aby łatwo wdrożyć ją w wielu środowiskach testowych, a nawet w środowisku produkcyjnym.
* Można zaplanować, aby Automatyzacja zaplanował się zawsze, gdy istnieje Zaewidencjonuj lub Zatwierdź lub w określonym czasie każdego dnia.

Aby uzyskać więcej informacji, zobacz Korzystanie z programu [Build lub Release Management](use-build-or-rm-instead-of-lab-management.md).

::: moniker range="vs-2017"
## <a name="use-the-visual-studio-lab-management-features-of-microsoft-test-manager"></a>Użyj Visual Studio Lab Management funkcji Microsoft Test Manager

W przypadku używania Visual Studio Enterprise Edition można tworzyć środowiska laboratoryjne i zarządzać nimi za pomocą funkcji Visual Studio Lab Management Microsoft Test Manager.

Lab Management automatycznie instaluje agentów testowych na każdym komputerze w środowisku.

Jeśli używasz Lab Management w połączeniu z System Center Virtual Machine Manager (SCVMM), uzyskasz również następujące korzyści w przypadku korzystania ze środowisk laboratoryjnych:

* **Szybkie odtwarzanie konfiguracji maszyn** — można przechowywać kolekcje maszyn wirtualnych, które są skonfigurowane do ponownego tworzenia typowych środowisk produkcyjnych. Następnie można wykonać każdy przebieg testu na nowej kopii zapisanego środowiska.

* **Odtworzenie dokładnych warunków błędu** — w przypadku niepowodzenia przebiegu testowego można zapisać kopię stanu środowiska laboratoryjnego i uzyskać do niego dostęp z wyników kompilacji lub elementu pracy.

* **Uruchom wiele kopii środowiska laboratoryjnego w tym samym czasie** — można uruchomić wiele kopii środowiska laboratoryjnego w tym samym czasie bez konfliktów nazw.

### <a name="standard-environments-and-scvmm-environments"></a>Standardowe środowiska i środowiska SCVMM

Istnieją dwa typy środowisk laboratoryjnych, które można utworzyć za pomocą Visual Studio Lab Management: **standardowe środowiska** i **środowiska SCVMM**. Jednak możliwości poszczególnych typów środowiska są różne.

**Środowiska standardowe:** mogą zawierać kombinację maszyn wirtualnych i fizycznych. Możesz również dodać maszyny wirtualne do środowiska standardowego, które są zarządzane przez platformy wirtualizacji innych firm. Ponadto środowiska standardowe nie wymagają dodatkowych zasobów serwera, takich jak serwer SCVMM.

**Środowiska SCVMM:** mogą zawierać tylko maszyny wirtualne, które są zarządzane przez program scvmm (System Center Virtual Machine Manager), dzięki czemu maszyny wirtualne w środowiskach SCVMM mogą działać tylko na platformie wirtualizacji funkcji Hyper-V. Jednak środowiska SCVMM udostępniają następujące funkcje automatyzacji i zarządzania, które nie są dostępne w standardowych środowiskach:

- **Migawki środowiska:** Migawki środowiska zawierają stan środowiska laboratoryjnego, dzięki czemu można szybko przywrócić czyste środowisko lub zapisać stan modyfikowanego środowiska. Możesz również użyć przepływu pracy Kompilacja-Wdrażanie-test, aby zautomatyzować proces zapisywania i przywracania migawek środowiska.

- **Środowiska przechowywane:** Można przechowywać kopię środowiska SCVMM, a następnie wdrożyć wiele kopii tego środowiska.

- **Izolacja sieci:** Izolacja sieci pozwala jednocześnie uruchamiać wiele identycznych kopii środowiska SCVMM bez konfliktów nazw komputerów.

- **Szablony maszyn wirtualnych:** Szablon maszyny wirtualnej jest maszyną wirtualną, której nazwy i inne identyfikatory zostały usunięte. Gdy szablon maszyny wirtualnej jest wdrażany w środowisku SCVMM, Microsoft Test Manager generuje nowe identyfikatory. Pozwala to wdrożyć wiele kopii maszyny wirtualnej w tym samym środowisku lub wielu środowiskach, a następnie uruchamiać maszyny wirtualne jednocześnie.

- **Virtual Machines przechowywane:** Maszyna wirtualna, która jest przechowywana w bibliotece projektu i zawiera unikatowe identyfikatory.

> [!NOTE]
> Lab Management nie obsługuje SCVMM 2016.

Aby uzyskać informacje o programie SCVMM, zobacz [Virtual Machine Manager](/azure/devops/pipelines/?view=vsts&preserve-view=true).

Środowiska standardowe i środowiska SCVMM obsługują wiele z tych samych funkcji. Należy jednak wziąć pod uwagę pewne istotne różnice. Poniższa tabela zawiera porównanie funkcji dostępnych w środowiskach standardowych i środowiskach SCVMM.

|Możliwość|Środowiska SCVMM|Standardowe środowiska|
|-|------------------------|-|
|**Testowanie**|||
|Uruchom testy ręczne|Obsługiwane|Obsługiwane|
|Uruchamianie kodowanego interfejsu użytkownika i innych testów automatycznych|Obsługiwane|Obsługiwane|
|Rozbudowane błędy plików przy użyciu adapterów diagnostycznych|Obsługiwane|Obsługiwane|
|**Wdrożenie kompilacji**|||
|Automatyczne Kompilowanie — wdrażanie testów — przepływy pracy|Obsługiwane|Obsługiwane|
|**Tworzenie środowiska i zarządzanie nim**|||
|Oprócz maszyn wirtualnych używaj maszyn fizycznych|Nieobsługiwane|Obsługiwane|
|Korzystanie z maszyn wirtualnych innych firm|Nieobsługiwane|Obsługiwane|
|Automatycznie Instaluj agentów testowych na maszynach w środowisku laboratoryjnym|Obsługiwane|Obsługiwane|
|Zapisz i Wdróż stan środowiska laboratoryjnego za pomocą migawek środowiska|Obsługiwane|Nieobsługiwane|
|Tworzenie środowisk laboratoryjnych na podstawie szablonów maszyn wirtualnych|Obsługiwane|Nieobsługiwane|
|Środowisko uruchamiania/zatrzymywania/migawek|Obsługiwane|Nieobsługiwane|
|Nawiązywanie połączenia ze środowiskiem za pomocą podglądu środowiska|Obsługiwane|Obsługiwane|
|Uruchom wiele kopii środowiska w tym samym czasie, używając izolacji sieci|Obsługiwane|Nieobsługiwane|

### <a name="lab-management-concepts"></a>Koncepcje dotyczące zarządzania laboratorium

Poniżej przedstawiono kilka dodatkowych koncepcji, z którymi należy się zapoznać przed kontynuowaniem:

|Okres|Opis|
|-|-----------------|
|Centrum laboratoryjne|Obszar Microsoft Test Manager, w którym tworzysz środowiska laboratoryjne i zarządzaj nimi.|
|Laboratorium projektowe platformy Azure DevOps|Kolekcja środowisk laboratoryjnych, które zostały skonfigurowane, aby można było połączyć się z nimi i uruchamiać maszyny wirtualne.|
|Biblioteka projektu usługi Azure DevOps|Archiwum przechowywanych maszyn wirtualnych, szablonów i przechowywanych środowisk laboratorium, które zostały zaimportowane do grupy hostów projektu. Elementy w bibliotece można używać ze środowiskami SCVMM; nie można jednak dodawać ich bezpośrednio do standardowego środowiska. Nie można uruchamiać elementów w bibliotece; Zamiast tego należy użyć ich do wdrożenia nowego środowiska.|
|Wdrożone środowisko|Środowisko laboratoryjne, które zostało wdrożone w laboratorium projektu, aby można było połączyć się z nim i uruchamiać jego maszyny.|

Aby uzyskać więcej informacji na temat programu Lab Management, zobacz:

* [Planowanie laboratorium](/previous-versions/ff756575(v=vs.140))
* [Administrowanie laboratorium](/previous-versions/dd936084(v=vs.140))
* [Konfiguracja dla środowisk SCVMM](/previous-versions/dd380687(v=vs.140))
* [Zarządzanie uprawnieniami](/previous-versions/dd380760(v=vs.140))
* [Zmień konfigurację](/previous-versions/ee704508(v=vs.140))
* [Rozwiązywanie problemów](/previous-versions/ee853230(v=vs.140))

Aby uzyskać informacje o konfigurowaniu środowisk, zobacz:

* [Tworzenie i wydawanie środowisk w chmurze](use-build-or-rm-instead-of-lab-management.md)
* [Standardowe środowiska laboratoryjne](/previous-versions/ee390842(v=vs.140))
* [Środowiska SCVMM (wirtualne)](/previous-versions/ee943322(v=vs.140))
* [Tworzenie środowiska izolowanego od sieci i korzystanie z niego](/previous-versions/ee518924(v=vs.140))
::: moniker-end

## <a name="see-also"></a>Zobacz też

* [Instalowanie i konfigurowanie agentów testowych](../../test/lab-management/install-configure-test-agents.md)
* [Przewodnik Visual Studio Lab Management](/archive/blogs/visualstudioalmrangers/library-of-tooling-and-guidance-solutions-aka-msvsarsolutions)
* [Blog usługi Microsoft DevOps](https://devblogs.microsoft.com/devops/)