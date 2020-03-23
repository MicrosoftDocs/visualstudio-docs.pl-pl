---
title: Użyj potoków platformy Azure do automatycznego testowania
ms.date: 10/19/2018
ms.topic: conceptual
helpviewer_keywords:
- automated testing, lab management, test lab
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: bd6e9b2d9ea408e451b7032a00c3c96fb0ef2b58
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566829"
---
# <a name="use-azure-test-plans-instead-of-lab-management-for-automated-testing"></a>Użyj planów testów platformy Azure zamiast usługi Lab Management do automatycznego testowania

Jeśli używasz Microsoft Test Manager i Lab Management do automatycznego testowania lub automatyzacji kompilacji i wdrażania testów, w tym temacie wyjaśniono, jak można osiągnąć te same cele przy użyciu funkcji [kompilacji i wersji](/azure/devops/pipelines/index?view=vsts) w potokach platformy Azure i Team Foundation Server (TFS).

## <a name="build-deploy-test-automation"></a>Automatyzacja kompilacji i wdrażania i testowania

Program Microsoft Test Manager i zarządzanie laboratorium polegają na definicji kompilacji XAML w celu automatyzacji tworzenia, wdrażania i testowania aplikacji. Kompilacja XAML opiera się na różnych konstrukcjach utworzonych w Menedżerze testów firmy Microsoft, takich jak środowisko laboratoryjne, zestawy testów i ustawienia testowania, oraz na różnych składnikach infrastruktury, takich jak kontroler kompilacji, agenci kompilacji, kontroler testów i agenci testowi, aby osiągnąć ten cel. Można osiągnąć to samo z mniejszą liczbą kroków przy użyciu usługi Azure Potoki lub TFS.

| Kroki | Z kompilacją XAML | W kompilacji lub wersji |
|-------|----------------------|-----------------|
| Identyfikowanie maszyn do wdrażania kompilacji i uruchamiania testów. | Tworzenie standardowego środowiska laboratoryjnego w programie Microsoft Test Manager z tych maszyn. | Nie dotyczy |
| Zidentyfikuj testy do uruchomienia. | Utwórz zestaw testów w menedżerze testów firmy Microsoft, utwórz przypadki testowe i skojarz automatyzację z każdym przypadkiem testowym. Utwórz ustawienia testów w programie Microsoft Test Manager identyfikując rolę komputerów w środowisku laboratoryjnym, w którym należy uruchomić testy. | Utwórz zestaw testów automatycznych w Programie Microsoft Test Manager w taki sam sposób, jeśli planujesz zarządzać testowaniem za pomocą planów testów. Alternatywnie można pominąć to, jeśli chcesz uruchomić testy bezpośrednio z plików binarnych testów produkowanych przez kompilacje. Nie ma potrzeby tworzenia ustawień testu w obu przypadkach. |
| Automatyzacja wdrażania i testowania. | Utwórz definicję kompilacji XAML przy użyciu labdefaulttemplate.*.xaml. Określ kompilacji, zestawów testów i środowiska laboratoryjne w definicji kompilacji. | Utwórz [potok kompilacji lub wydania](/azure/devops/pipelines/index?view=vsts) z jednego środowiska. Uruchom ten sam skrypt wdrażania (z definicji kompilacji XAML) za pomocą zadania wiersza polecenia i uruchom zautomatyzowane testy przy użyciu zadań wdrażania i uruchamiania testów funkcjonalnych agenta. Określ listę maszyn i ich poświadczenia jako dane wejściowe do tych zadań. |

Niektóre z zalet korzystania z usługi Azure Potoki lub TFS w tym scenariuszu są:

* Nie potrzebujesz kontrolera kompilacji ani kontrolera testów.
* Agent testowy jest instalowany za pośrednictwem zadania jako część kompilacji lub wydania.
* Kroki wdrażania można łatwo dostosować. Nie masz już ograniczeń w używaniu pojedynczego skryptu. Można również skorzystać z wielu zadań, które są dostępne w produkcie, a także w programie Visual Studio Marketplace.
* Nie trzeba utrzymywać zestawy testów. Testy można uruchamiać bezpośrednio z plików binarnych.
* Otrzymasz bogatsze środowisko raportowania wbudowanego dla testów, które zostały przeprowadzone w ramach każdej kompilacji lub wydania.
* Można śledzić, które zasoby (wydanie, kompilacja, elementy robocze, zatwierdzenia) są obecnie wdrażane i testowane w każdym środowisku.
* Można dostosować i rozszerzyć automatyzację, aby łatwo wdrożyć do wielu środowisk testowych, a nawet do środowiska produkcyjnego.
* Automatyzację można zaplanować za każdym razem, gdy jest odprawa lub zatwierdzenie lub o określonej godzinie każdego dnia.

## <a name="self-service-management-of-scvmm-environments"></a>Samoobsługowe zarządzanie środowiskami SCVMM

[Centrum testów w programie Microsoft Test Manager](/azure/devops/test/mtm/guidance-mtm-usage?view=vsts) obsługuje możliwość zarządzania biblioteką szablonów środowiska, a także środowiska obsługi administracyjnej na żądanie przy użyciu serwera [SCVMM](/system-center/vmm/overview?view=sc-vmm-1801).

Funkcje samoobsługowej obsługi administracyjnej Centrum laboratorium mają dwa odrębne cele:

* Zapewnij prostszy sposób zarządzania infrastrukturą. Zarządzanie szablonami maszyn wirtualnych i środowiska oraz automatyczne tworzenie sieci prywatnych w celu izolowania klonów środowisk od siebie nawzajem były przykładami zarządzania infrastrukturą.

* Zapewnij zespołom prostszy sposób korzystania z maszyn wirtualnych w ich działaniach testowych i wdrożeniowych. Udostępnianie środowisk laboratoryjnych za pośrednictwem tego samego modelu zabezpieczeń projektu oraz zintegrowane korzystanie z tych maszyn wirtualnych w scenariuszach testowych były przykładami łatwego użycia.

Jednak biorąc pod uwagę ewolucję bogatszych systemów zarządzania chmurą publiczną i prywatną, takich jak [Microsoft Azure](https://azure.microsoft.com/) i Microsoft [Azure Stack,](https://azure.microsoft.com/overview/azure-stack/)nie ma ewolucji funkcji zarządzania infrastrukturą w TFS 2017 i później. Zamiast tego nadal koncentruje się na łatwym zużyciu zasobów zarządzanych za pośrednictwem takiej infrastruktury chmury.

W poniższej tabeli podsumowano typowe działania wykonywane w Centrum laboratorium oraz sposób ich wykonywania za pośrednictwem programu SCVMM lub platformy Azure (jeśli są to działania związane z zarządzaniem infrastrukturą) lub za pośrednictwem usług TFS i Azure DevOps (jeśli są testem lub wdrożeniem działalności):

| Kroki | Z Centrum laboratorium | W kompilacji lub wersji |
|-------|-----------------|-----------------------|
| Zarządzanie biblioteką szablonów środowiska. | Tworzenie środowiska laboratoryjnego. Zainstaluj niezbędne oprogramowanie na maszynach wirtualnych. Sysprep i przechowywać środowisko jako szablon w bibliotece. | Bezpośrednio za pomocą konsoli administracyjnej SCVMM można tworzyć szablony maszyn wirtualnych lub szablony usług i zarządzać nimi. Korzystając z platformy Azure, wybierz jeden z [szablonów szybkiego startu platformy Azure](https://azure.microsoft.com/resources/templates/). |
| Tworzenie środowiska laboratoryjnego. | Wybierz szablon środowiska w bibliotece i wdrożyć go. Podaj parametry niezbędne do dostosowania konfiguracji maszyny wirtualnej. | Bezpośrednio użyj konsoli administracyjnej SCVMM do tworzenia maszyn wirtualnych lub wystąpień usługi na podstawie szablonów. Bezpośrednio użyj witryny Azure portal do tworzenia zasobów. Lub utworzyć definicję wydania ze środowiskiem. Użyj zadań platformy Azure lub zadań z [rozszerzenia integracji SCVMM,](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) aby utworzyć nowe maszyny wirtualne. Tworzenie nowej wersji tej definicji jest równoznaczne z utworzeniem nowego środowiska w Centrum laboratorium. |
| Podłącz do maszyn. | Otwórz środowisko laboratoryjne w przeglądarce środowiska. | Użyj konsoli administracyjnej SCVMM bezpośrednio do łączenia się z maszynami wirtualnymi. Alternatywnie należy użyć adresu IP lub nazw DNS maszyn wirtualnych, aby otworzyć sesje pulpitu zdalnego. |
| Weź punkt kontrolny środowiska lub przywrócić środowisko do czystego punktu kontrolnego. | Otwórz środowisko laboratoryjne w przeglądarce środowiska. Wybierz opcję, aby wziąć punkt kontrolny lub przywrócić do poprzedniego punktu kontrolnego. | Użyj konsoli administracyjnej SCVMM bezpośrednio do wykonywania tych operacji na maszynach wirtualnych. Lub, aby wykonać te kroki w ramach większej automatyzacji, należy uwzględnić zadania punktu kontrolnego z [rozszerzenia integracji SCVMM](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) jako część środowiska w definicji wydania. |

## <a name="create-network-isolated-environments"></a>Tworzenie środowisk izolowanych przez sieć

Izolowane środowisko laboratoryjne sieci to grupa maszyn wirtualnych SCVMM, które można bezpiecznie sklonować bez powodowania konfliktów sieciowych. Zostało to zrobione w mtm przy użyciu serii instrukcji, które używane zestaw kart interfejsu sieciowego do konfigurowania maszyn wirtualnych w sieci prywatnej i inny zestaw kart interfejsu sieciowego do konfigurowania maszyn wirtualnych w sieci publicznej.

Jednak potoki platformy Azure i TFS, w połączeniu z scvmm kompilacji i wdrażania zadania, mogą służyć do zarządzania środowiskami SCVMM, inicjowania obsługi administracyjnej izolowanych sieci wirtualnych i implementowania scenariuszy kompilacji i wdrażania testów. Na przykład można użyć zadania do:

* Tworzenie, przywracanie i usuwanie punktów kontrolnych
* Tworzenie nowych maszyn wirtualnych przy użyciu szablonu
* Uruchamianie i zatrzymywania maszyn wirtualnych
* Uruchamianie niestandardowych skryptów programu PowerShell dla programu SCVMM

Aby uzyskać więcej informacji, zobacz [Tworzenie środowiska izolowanego sieci wirtualnej dla scenariuszy kompilacji i wdrażania testów](/azure/devops/pipelines/targets/create-virtual-network?view=vsts).
