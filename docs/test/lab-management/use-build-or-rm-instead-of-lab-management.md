---
title: Użyj Azure Pipelines do testowania automatycznego
ms.date: 10/19/2018
ms.topic: how-to
helpviewer_keywords:
- automated testing, lab management, test lab
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 37455c05a010681eac343287abf25aad642328c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85286846"
---
# <a name="use-azure-test-plans-instead-of-lab-management-for-automated-testing"></a>Użyj Azure Test Plans zamiast Lab Management do testowania automatycznego

Jeśli używasz Microsoft Test Manager i Lab Management do testowania automatycznego lub dla automatyzacji Kompilacja-Wdrażanie-test, w tym temacie wyjaśniono, jak można osiągnąć te same cele przy użyciu funkcji [kompilowania i](/azure/devops/pipelines/index?view=vsts) wydawania w Azure Pipelines i Team Foundation Server (TFS).

> [!NOTE]
> Microsoft Test Manager jest przestarzała w programie Visual Studio 2017 i został usunięty w programie Visual Studio 2019.

## <a name="build-deploy-test-automation"></a>Kompilacja-Wdrażanie-test Automation

Microsoft Test Manager i Lab Management polegają na definicji kompilacji XAML w celu zautomatyzowania kompilowania, wdrażania i testowania aplikacji. Kompilacja XAML bazuje na różnych konstrukcjach utworzonych w Microsoft Test Manager takich jak środowisko laboratoryjne, zestawy testów i ustawienia testowania, a także na różnych składnikach infrastruktury, takich jak kontroler kompilacji, agenci kompilacji, kontroler testów i agenci testowi, aby osiągnąć ten cel. Można to zrobić przy mniejszej liczbie kroków przy użyciu Azure Pipelines lub TFS.

| Kroki | Z kompilacją XAML | W kompilacji lub wersji |
|-------|----------------------|-----------------|
| Zidentyfikuj maszyny, na których ma zostać wdrożona kompilacja, i uruchom testy. | Utwórz standardowe środowisko laboratoryjne w Microsoft Test Manager z tymi maszynami. | nie dotyczy |
| Zidentyfikuj testy do uruchomienia. | Utwórz zestaw testów w Microsoft Test Manager, Utwórz przypadki testowe i skojarz automatyzację z każdym przypadkiem testowym. Utwórz ustawienia testu w Microsoft Test Manager identyfikowania roli maszyn w środowisku laboratoryjnym, w której powinny być uruchamiane testy. | Utwórz zautomatyzowany zestaw testów w Microsoft Test Manager w taki sam sposób, jeśli planujesz zarządzać testowaniem za pomocą planów testów. Alternatywnie możesz pominąć tę funkcję, jeśli chcesz uruchomić testy bezpośrednio z plików binarnych testów produkowanych w ramach kompilacji. Nie ma potrzeby tworzenia ustawień testu w obu przypadkach. |
| Automatyzacja wdrażania i testowania. | Utwórz definicję kompilacji XAML przy użyciu LabDefaultTemplate. *. XAML. Określ środowisko kompilacji, zestawów testów i środowiska laboratoryjnego w definicji kompilacji. | Utwórz [potok kompilacji lub wersji](/azure/devops/pipelines/index?view=vsts) za pomocą jednego środowiska. Uruchom ten sam skrypt wdrażania (z definicji kompilacji XAML) przy użyciu zadania wiersza polecenia i uruchom testy automatyczne przy użyciu wdrożenia agenta testowego i Uruchom zadania testów funkcjonalnych. Określ listę maszyn i ich poświadczenia jako dane wejściowe tych zadań. |

W tym scenariuszu niektóre korzyści wynikające z używania Azure Pipelines lub TFS są następujące:

* Kontroler kompilacji lub kontroler testów nie jest potrzebny.
* Agent testowy jest instalowany za pomocą zadania w ramach kompilacji lub wydania.
* Można łatwo dostosować kroki wdrażania. Nie można już używać pojedynczego skryptu. Możesz również skorzystać z wielu zadań dostępnych w produkcie, jak również w Visual Studio Marketplace.
* Nie musisz obsługiwać zestawów testów. Można bezpośrednio uruchamiać testy z plików binarnych.
* Uzyskasz bogatsze wbudowane środowisko raportowania dla testów, które zostały uruchomione w ramach każdej kompilacji lub wydania.
* Można śledzić, które zasoby (wydanie, kompilacja, elementy robocze, zatwierdzenia) są obecnie wdrażane i testowane w każdym środowisku.
* Możesz dostosować i zwiększyć automatyzację, aby łatwo wdrożyć ją w wielu środowiskach testowych, a nawet w środowisku produkcyjnym.
* Można zaplanować, aby Automatyzacja zaplanował się zawsze, gdy istnieje Zaewidencjonuj lub Zatwierdź lub w określonym czasie każdego dnia.

## <a name="self-service-management-of-scvmm-environments"></a>Samoobsługowe zarządzanie środowiskami SCVMM

[Centrum testowe w Microsoft Test Manager](/azure/devops/test/mtm/guidance-mtm-usage?view=vsts) obsługuje możliwość zarządzania biblioteką szablonów środowiska oraz udostępniania środowisk na żądanie przy użyciu [serwera SCVMM](/system-center/vmm/overview?view=sc-vmm-1801).

Funkcje samoobsługowego inicjowania obsługi programu Lab Center mają dwa różne cele:

* Zapewnienie prostszej metody zarządzania infrastrukturą. Zarządzanie szablonami maszyn wirtualnych i środowiska oraz automatyczne tworzenie sieci prywatnych w celu izolowania klonów środowisk od siebie była przykładami zarządzania infrastrukturą.

* Zapewnienie, że zespoły mogą zużywać maszyny wirtualne w swoich działaniach testowych i wdrożeniowych. Tworzenie środowisk laboratoryjnych dostępnych za pomocą tego samego modelu zabezpieczeń projektu i zintegrowane korzystanie z tych maszyn wirtualnych w scenariuszach testowych było przykładem prostego zużycia.

Jednak w przypadku ewolucji rozbudowanych systemów zarządzania chmurą publiczną i prywatną, takich jak [Microsoft Azure](https://azure.microsoft.com/) i [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/), nie ma ewolucji funkcji zarządzania infrastrukturą w programie TFS 2017 i nowszych wersjach. Zamiast tego należy skoncentrować się na łatwym zużyciu zasobów zarządzanych za pomocą tych infrastruktury chmurowej.

W poniższej tabeli zestawiono typowe działania wykonywane w programie Lab Center oraz sposób ich wykonywania za pomocą programu SCVMM lub platformy Azure (jeśli są to działania związane z zarządzaniem infrastrukturą) lub za pomocą programu TFS i Azure DevOps Services (jeśli są to działania testowe lub wdrożeniowe):

| Kroki | Z centrum laboratoryjne | W kompilacji lub wersji |
|-------|-----------------|-----------------------|
| Zarządzanie biblioteką szablonów środowiska. | Utwórz środowisko laboratoryjne. Zainstaluj wymagane oprogramowanie na maszynach wirtualnych. Program Sysprep i przechowywanie środowiska jako szablonu w bibliotece. | Konsola administracyjna SCVMM służy bezpośrednio do tworzenia szablonów maszyn wirtualnych lub szablonów usług oraz zarządzania nimi. W przypadku korzystania z platformy Azure wybierz jeden z [szablonów szybkiego startu platformy Azure](https://azure.microsoft.com/resources/templates/). |
| Utwórz środowisko laboratoryjne. | Wybierz szablon środowiska w bibliotece i Wdróż go. Podaj niezbędne parametry, aby dostosować konfiguracje maszyn wirtualnych. | Użyj konsoli administracyjnej SCVMM bezpośrednio, aby tworzyć maszyny wirtualne lub wystąpienia usług z szablonów. Użyj Azure Portal bezpośrednio do tworzenia zasobów. Lub Utwórz definicję wydania ze środowiskiem. Aby tworzyć nowe maszyny wirtualne, użyj zadań lub zadań platformy Azure z [rozszerzenia integracji SCVMM](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) . Tworzenie nowej wersji tej definicji jest równoznaczne z utworzeniem nowego środowiska w centrum laboratoryjnym. |
| Połącz z maszynami. | Otwórz środowisko laboratoryjne w podglądzie środowiska. | Użyj konsoli administracyjnej SCVMM, aby nawiązać połączenie z maszynami wirtualnymi. Alternatywnie możesz użyć adresów IP lub nazw DNS maszyn wirtualnych, aby otworzyć sesje pulpitu zdalnego. |
| Utwórz punkt kontrolny środowiska lub Przywróć środowisko do czystego punktu kontrolnego. | Otwórz środowisko laboratoryjne w podglądzie środowiska. Wybierz opcję, aby wykonać punkt kontrolny lub przywrócić poprzedni punkt kontrolny. | Użyj konsoli administracyjnej SCVMM bezpośrednio, aby wykonać te operacje na maszynach wirtualnych. Aby wykonać te kroki w ramach większej automatyzacji, należy uwzględnić zadania punktów kontrolnych z [rozszerzenia integracji SCVMM](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) jako część środowiska w definicji wersji. |

## <a name="create-network-isolated-environments"></a>Tworzenie środowisk izolowanych od sieci

Środowisko laboratoryjne izolowane od sieci to grupa maszyn wirtualnych SCVMM, które można bezpiecznie sklonować bez powodowania konfliktów sieci. Zostało to zrobione w MTM przy użyciu szeregu instrukcji, które używały zestawu kart sieciowych do konfigurowania maszyn wirtualnych w sieci prywatnej i innego zestawu kart sieciowych do konfigurowania maszyn wirtualnych w sieci publicznej.

Jednak Azure Pipelines i TFS, w połączeniu z zadaniami kompilowania i wdrażania SCVMM, mogą służyć do zarządzania środowiskami SCVMM, udostępniania izolowanych sieci wirtualnych i implementowania scenariuszy kompilowania wdrożeń i testowania. Można na przykład użyć zadania, aby:

* Tworzenie, przywracanie i usuwanie punktów kontrolnych
* Tworzenie nowych maszyn wirtualnych przy użyciu szablonu
* Uruchamianie i zatrzymywanie maszyn wirtualnych
* Uruchamianie niestandardowych skryptów programu PowerShell dla programu SCVMM

Aby uzyskać więcej informacji, zobacz [Tworzenie środowiska izolowanego sieci wirtualnej na potrzeby scenariuszy Kompilacja-Wdrażanie-test](/azure/devops/pipelines/targets/create-virtual-network?view=vsts).
