---
title: Użycie potoków usługi Azure do testów automatycznych
ms.date: 10/19/2018
ms.topic: conceptual
helpviewer_keywords:
- automated testing, lab management, test lab
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d9bb59a383db46fdfc3b7e5a9a2f429399630873
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55949957"
---
# <a name="use-azure-test-plans-instead-of-lab-management-for-automated-testing"></a>Używanie planów testowych platformy Azure zamiast Lab Management potrzeby testowania automatycznego

Jeśli używasz Microsoft Test Manager i Lab Management do testów automatycznych lub w przypadku usługi automation kompilacja wdrożenie test w tym temacie wyjaśniono, jak można uzyskać te same cele przy użyciu [kompilowania i wydawania](/azure/devops/pipelines/index?view=vsts) funkcji Azure potoków i zespołu Foundation Server (TFS).

## <a name="build-deploy-test-automation"></a>Kompilacja wdrożenie test automatyzacji

Microsoft Test Manager i Lab Management, zależą od definicji kompilacji XAML w celu automatyzacji tworzenia, wdrażania i testowania aplikacji. Kompilacja XAML opiera się na różnych konstrukcji utworzone w Menedżerze testów firmy Microsoft, takich jak środowisko laboratoryjne, zestawy testów i ustawień testowania i na różnych składników infrastruktury, takich jak kontroler kompilacji, agentów kompilacji, kontroler testów i agentów testowych osiągnięcie tego celu. Przy użyciu mniejszej liczby czynności przy użyciu potoków usługi Azure lub na serwerze TFS, można wykonywać takie same.

| Kroki | Z kompilacji XAML | W kompilacji lub wydania |
|-------|----------------------|-----------------|
| Zidentyfikuj maszyny w celu kompilacji, aby wdrażać i uruchamiać testy. | Z tych maszyn, należy utworzyć standardowe środowiska laboratoryjne programu Microsoft Test Manager. | n/d |
| Określ testy do uruchomienia. | Tworzenie zestawu testów w programie Microsoft Test Manager, tworzyć przypadki testowe i kojarzenie automatyzacji z każdego przypadku testowego. Utwórz ustawienia testu w programie Microsoft Test Manager identyfikuje rolę maszyn w środowisku laboratoryjnym, w którym należy uruchomić testy. | Tworzenie zautomatyzowanych testów w programie Microsoft Test Manager w taki sam sposób, jeśli mają być zarządzane, testowanie za pomocą planów testu. Alternatywnie można pominąć to jeśli chcesz uruchamiać testy bezpośrednio z poziomu testu pliki binarne wytworzone przez kompilacji. Nie ma potrzeby tworzenia ustawień testu w obu przypadkach. |
| Automatyzuj wdrażanie i testowanie. | Utwórz definicję kompilacji XAML, za pomocą LabDefaultTemplate.*.xaml. W definicji kompilacji, należy określić kompilację, zestawy testów i środowiska laboratoryjnego. | Tworzenie [kompilacji lub potoku wydania](/azure/devops/pipelines/index?view=vsts) przy użyciu jednego środowiska. Uruchom ten sam skrypt wdrażania (od definicji kompilacji XAML) przy użyciu wiersza polecenia zadania i uruchamiania testów automatycznych za pomocą zadań wdrożenie agenta testowego i uruchom testy funkcjonalne. Określ listę maszyn i poświadczeń jako dane wejściowe z tymi zadaniami. |

Korzyści z używania potoki usługi Azure lub na serwerze TFS, w tym scenariuszu, należą:

* Nie trzeba kontrolera kompilacji lub kontrolera testów.
* Agent testowy jest zainstalowany za pomocą zadania jako część kompilacji lub wydania.
* To można łatwo dostosować procedury wdrażania. Nie jesteś już ograniczone do korzystania z jednego skryptu. Możesz również korzystać z zalet wiele zadań, które są dostępne w ramach produktu, a także jak Visual Studio Marketplace.
* Nie masz Obsługa zestawów testów. Można bezpośrednio uruchomić testy z plików binarnych.
* Uzyskasz bardziej zaawansowane wbudowane, raportowanie środowisko dla testów uruchomionych w ramach każdej kompilacji lub wydania.
* Trwałe, które można śledzić (wydania, tworzenie elementów roboczych, zatwierdzeń) są obecnie wdrożone i przetestowane w każdym środowisku.
* Można dostosować i rozszerzyć automatyzację, aby łatwo wdrożyć do wielu środowisk testowych, a nawet do środowiska produkcyjnego.
* Można zaplanować automatyzacji, który ma być wykonywana zawsze, gdy występuje lub ewidencjonowania zatwierdzenia lub codziennie o określonej godzinie.

## <a name="self-service-management-of-scvmm-environments"></a>Samoobsługowe zarządzanie środowiska SCVMM

[Centrum testów w programie Microsoft Test Manager](/azure/devops/test/mtm/guidance-mtm-usage?view=vsts) obsługuje możliwość bibliotekę szablonów środowiska zarządzania, a także aprowizować środowiska na żądanie przy użyciu [serwera SCVMM](/system-center/vmm/overview?view=sc-vmm-1801).

Samoobsługowe funkcje inicjowania obsługi Centrum laboratoryjnego ma dwa różne cele:

* Zapewnia prostszy sposób zarządzania infrastrukturą. Automatyczne tworzenie sieci prywatnych do izolowania klony środowiska od siebie nawzajem i zarządzanie nimi szablonów maszyn wirtualnych i środowisku zostały przykłady zarządzania infrastrukturą.

* Prostsze umożliwiają zespołom korzystanie z maszyn wirtualnych w swoich działaniach testowanie i wdrażanie. Podejmowanie środowisk laboratoryjnych, dostępne za pośrednictwem tego samego modelu zabezpieczeń projektu i zintegrowane korzystanie z tych maszyn wirtualnych w scenariuszach testowych, były przykłady łatwość użycia.

Jednak ze względu ewolucji bogatsze chmur publicznych i prywatnych systemów zarządzania takie jak [Microsoft Azure](https://azure.microsoft.com/) i [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/), nie ma żadnych rozwój funkcji zarządzania infrastrukturą w Serwer TFS 2017 i nowszych. Zamiast tego kontynuuje skoncentrować się na łatwość użycia zasobów zarządzanych przy użyciu takich infrastruktur chmury.

W poniższej tabeli podsumowano typowych działań, które wykonujesz w Centrum laboratoryjnego i jak można wykonać je za pomocą programu SCVMM lub na platformie Azure (jeśli są działania związane z zarządzaniem infrastrukturą) lub TFS i usługom DevOps platformy Azure (jeśli są one testu lub wdrożenia czynności):

| Kroki | Przy użyciu Centrum laboratoryjnego | W kompilacji lub wydania |
|-------|-----------------|-----------------------|
| Zarządzaj bibliotekę szablonów środowiska. | Utwórz środowisko laboratoryjne. Niezbędne oprogramowanie należy zainstalować na maszynach wirtualnych. Narzędzie Sysprep i magazynu środowisko jako szablon w bibliotece. | Użyj konsoli administracji SCVMM bezpośrednio do tworzenia i zarządzania nimi, szablony maszyn wirtualnych lub szablonów usług. Korzystając z platformy Azure, wybierz jedną z [szablony szybkiego startu platformy](https://azure.microsoft.com/resources/templates/). |
| Utwórz środowisko laboratoryjne. | Wybierz szablon środowiska w bibliotece, a następnie wdrożyć ją. Podaj niezbędne parametry, aby dostosować konfiguracje maszyny wirtualnej. | Bezpośrednio za pomocą konsoli administracyjnej SCVMM za pomocą szablonów można tworzyć maszyny wirtualne lub wystąpienia usługi. Bezpośrednio za pomocą witryny Azure portal utworzyć zasoby. Lub Utwórz definicję wersji ze środowiskiem. Użycie platformy Azure, zadania lub zadania z [rozszerzeniu integracji programu SCVMM](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) umożliwia tworzenie nowych maszyn wirtualnych. Tworzenie nowej wersji ta definicja jest odpowiednikiem Tworzenie nowego środowiska w laboratorium. |
| Łączyć się z maszynami. | Otwórz środowisko laboratoryjne w podglądu środowiska. | Bezpośrednio za pomocą konsoli administracyjnej SCVMM nawiązać połączenie z maszynami wirtualnymi. Można również użyć adresu IP lub nazwy DNS maszyn wirtualnych, aby otworzyć sesji pulpitu zdalnego. |
| Punkt kontrolny środowiska lub przywrócić środowiska do czystego punktu kontrolnego. | Otwórz środowisko laboratoryjne w podglądu środowiska. Wybierz opcję Utwórz punkt kontrolny lub przywrócić do poprzedniego punktu kontrolnego. | Bezpośrednio za pomocą konsoli administracyjnej SCVMM wykonywać te operacje na maszynach wirtualnych. Lub, jako część większych automatyzacji, należy wykonać te kroki, obejmują zadania punkt kontrolny z [rozszerzeniu integracji programu SCVMM](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) jako część środowiska w definicji wydania. |

## <a name="create-network-isolated-environments"></a>Utwórz środowiska izolacji sieciowej

Środowisko laboratorium izolowane sieci to grupa maszyn wirtualnych programu SCVMM, które można bezpiecznie sklonować bez powodowania konfliktów sieci. W programie MTM stało się przy użyciu szereg instrukcji, które umożliwiają skonfigurowanie maszyn wirtualnych w sieci publicznej zbiór kart interfejsu sieciowego, aby skonfigurować maszyn wirtualnych w sieci prywatnej, a inny zbiór kart interfejsu sieciowego.

Jednak potoki usługi Azure i TFS, w połączeniu z programem SCVMM kompilacji zadanie wdrażania, może służyć do zarządzania środowisk SCVMM, udostępniania izolowanych sieci wirtualnej i implementowanie scenariuszy kompilacja wdrożenie test. Na przykład można użyć zadania:

* Tworzenie, przywracania i usunąć punkty kontrolne
* Tworzenie nowych maszyn wirtualnych przy użyciu szablonu
* Uruchamianie i zatrzymywanie maszyn wirtualnych
* Uruchamianie niestandardowych skryptów środowiska PowerShell dla programu SCVMM

Aby uzyskać więcej informacji, zobacz [Utwórz środowisko wirtualne sieci izolowanej scenariuszach kompilacja wdrożenie test](/azure/devops/pipelines/targets/create-virtual-network?view=vsts).
