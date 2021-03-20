---
title: Często zadawane pytania
description: Często zadawane pytania dotyczące narzędzia devinit.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 603d09de5a37ea7ea4f0ff10c377c56eb9a3d63e
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672194"
---
# <a name="frequently-asked-questions-for-devinit"></a>Często zadawane pytania dotyczące devinit

> [!IMPORTANT]
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. W ramach tego `devinit` i skojarzonych narzędzi nie będą już dostępne. Zachęcamy do pracy na naszym forum społeczności deweloperów dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami.

## <a name="is-devinit-just-for-github-codespaces"></a>Czy devinit tylko dla Codespaces GitHub?

Na razie devinit jest dostępna tylko w ramach prywatnej wersji beta usługi GitHub Codespaces. Mamy jednak plany, aby uwzględnić devinit w nadchodzącym wydaniu programu Visual Studio 2019.

## <a name="is-it-windows-only"></a>Czy jest tylko system Windows?
Tak, devinit koncentruje się na tworzeniu środowisk deweloperskich, które działają dla deweloperów korzystających z programu Visual Studio, co oznacza, że system Windows. Rozważamy inne platformy, ale wiele z nich ma już wspaniałe rozwiązania, więc chcemy zacząć od programu Visual Studio i systemu Windows.

## <a name="theres-no-tool-for-the-dependency-i-need"></a>Nie ma narzędzia dla zależności, czego potrzebuję!

Przepraszamy! Jeśli jesteś częścią prywatnej wersji beta usługi GitHub Codespaces, możesz wrócić do nas za pośrednictwem kanału opinii dla prywatnej wersji beta. Jeśli nie jesteś częścią prywatnego programu w wersji beta, będziemy nadal poznamy Twoją opinię na temat tego, czego potrzebujesz, i możesz rozwiązać problem w naszej dokumentacji [programu Visual Studio](https://github.com/MicrosoftDocs/visualstudio-docs/) za pomocą etykiety, `devinit` Aby zażądać pomocy technicznej dla potrzebnego narzędzia.

## <a name="something-went-wrong-how-do-i-debug"></a>Coś poszło źle, jak debugować?

Jeśli devinit zakończy się niepowodzeniem, najpierw należy wykonać `--verbose / -v` flagę, aby uzyskać więcej informacji. Prawdopodobnie wystąpił problem z podstawowym narzędziem, które wywołuje devinit. Informacje o dziennikach pełnych powinny zawierać wskazówki dotyczące miejsca, w którym ma wyglądać dalej.

## <a name="why-not-just-a-script"></a>Dlaczego nie tylko skrypt?

Konfigurowanie środowisk za pośrednictwem skryptu jest przestarzałą techniką i może być świetna. Jeśli jest to możliwe, użyj! devinit jest kolejną opcją dla deweloperów, gdy skrypty nie są najlepszym wyborem.

## <a name="why-not-a-container"></a>Dlaczego nie kontener?

Kontenery i Aparat Docker to doskonałe narzędzia do wdrażania środowiska za pośrednictwem kodu. Istnieje kilka powodów, dla których kontenery mogą nie być odpowiednim rozwiązaniem:

1. Jeśli chcesz użyć środowiska deweloperskiego opartego na komputerze z systemem Windows.
1. Jeśli masz już system operacyjny, a po prostu chcesz go dostosować, zamiast wdrożyć nowe środowisko.

Z tych powodów devinit się na dostosowanie środowiska systemu Windows, które jest obecnie dostępne.

## <a name="what-about-other-vm-creation-tools-for-example-terraform-packer-chef-vagrant-etc"></a>Co z innymi narzędziami do tworzenia maszyn wirtualnych (na przykład Terraform, Packer, Chef, Vagrant itp.)

Istnieje wiele doskonałych narzędzi do tworzenia obrazów systemu Windows i należy ich używać. Jednak nie udało nam się znaleźć takiego, który spełnił wszystkie scenariusze, z których mamy świadomość. Chcemy, aby devinit to narzędzie dla deweloperów, które dostosowuje swoje środowisko, w zależności od tego, co jest potrzebne dla określonego repozytorium i ma doskonałą integrację z programem Visual Studio, a nie narzędzia do tworzenia obrazów maszyn wirtualnych.

## <a name="what-about-winget"></a>Co z Winget?

devinit nie jest menedżerem pakietów, takim jak Winget, i nie chcemy go. Chcemy, aby móc korzystać z usługi Winget z devinit i pracujemy nad narzędziem w taki sam sposób.

## <a name="how-are-restarts-handled"></a>Jak są obsługiwane ponowne uruchomienia?

Jeśli wszystkie elementy instalowane przez program devinit wymagają ponownego uruchomienia systemu operacyjnego, w konsoli zostanie wyświetlony komunikat o błędzie. Konieczne będzie ponowne uruchomienie systemu operacyjnego w odpowiednim czasie. Po ponownym uruchomieniu programu może być konieczne ponowne uruchomienie programu devinit, jeśli nie zainstalowano wszystkich zależności.

## <a name="working-with-others"></a>Praca z innymi

devinit wszystko o umożliwieniu korzystania z całego ekosystemu, w którym można wdrażać i konfigurować zależności aplikacji. Mimo że devinit ma opinię na temat tego, co dostarcza, devinit jest przede wszystkim na umożliwienie wykonywania innych narzędzi z deklaracyjnego pliku JSON.

Już dziś devinit jest wprowadzenie i nasza [Lista narzędzi](devinit-tool-list.md) jest tylko na początku.
