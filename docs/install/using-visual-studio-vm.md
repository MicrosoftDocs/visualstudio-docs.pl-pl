---
title: Za pomocą programu Visual Studio na maszynie wirtualnej platformy Azure
titleSuffix: ''
description: Dowiedz się, jak używać programu Visual Studio na maszynie wirtualnej platformy Azure
ms.date: 09/12/2018
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- azure services
- virtual machine
- installation
- visual studio
author: PhilLee-MSFT
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a1dbda84c1e8eee48c4a442e922c1852496155ac
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55952908"
---
# <a id="top"> </a> Obrazów programu Visual Studio w systemie Azure

Przy użyciu programu Visual Studio w wstępnie skonfigurowanych maszyn wirtualnych (VM) to szybki i łatwy sposób skalują się od pozycji środowisko projektowe w górę i uruchomiona. Obrazy systemu z różnymi konfiguracjami programu Visual Studio są dostępne w [portalu Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/apps?search=%22visual%20studio%202017%22&page=1).

Jesteś nowym użytkownikiem platformy Azure? [Utwórz bezpłatne konto platformy Azure](https://azure.microsoft.com/free).

## <a name="what-configurations-and-versions-are-available"></a>Jakie konfiguracje i wersje są dostępne?

Obrazy do najnowszej wersji głównych, Visual Studio 2017 i Visual Studio 2015 można znaleźć w witrynie Azure Marketplace.  Niedawno Dodaliśmy obsługę wersji zapoznawczych mającej się ukazać wersji głównych — Visual Studio 2019 r.  Dla każdej wydanej wersji głównych Zobacz oryginalnie wydana wersja (RTW) i najnowsze zaktualizowane wersje.  Każda z tych wersji oferuje wersje programu Visual Studio Community i program Visual Studio Enterprise.  Te obrazy są aktualizowane co miesiąc, obejmujący najnowsze aktualizacje programu Visual Studio i Windows.  Gdy nazwy obrazów pozostają takie same, każdy obraz w opisie wersję zainstalowanego produktu i "dzień" obraz.

| Wersja                                              | Wersje                     |     Wersja produktu      |
|:------------------------------------------------------------:|:----------------------------:|:------------------------:|
|    Visual Studio 2019: (Wersja zapoznawcza 2) w wersji zapoznawczej                   |           Enterprise         | Wersji 16.0.0 Preview 2 |
| Visual Studio 2017: Najnowsze (w wersji 15.9)                    |    Enterprise, Community     |      Wersja 15.9.4      |
|         Visual Studio 2017: RTW                              |    Enterprise, Community     |      Wersja 15.0.20     |
|   Visual Studio 2015: Najnowsze (Aktualizacja 3)                      |    Enterprise, Community     |  Wersja 14.0.25431.01   |
|         Visual Studio 2015: RTW                              |             Brak             | (Wygasłe obsługi)  |

> [!NOTE]
> Zgodnie z zasady obsługi firmy Microsoft pierwotnie (RTW) wersji programu Visual Studio 2015 zakończył się okres obsługi. Visual Studio 2015 Update 3 jest jedynie wersja pozostałe oferowana w przypadku linii produktów Visual Studio 2015.

Aby uzyskać więcej informacji, zobacz [Visual Studio obsługi zasad](/visualstudio/productinfo/vs-servicing-vs).

## <a name="what-features-are-installed"></a>Jakie funkcje są zainstalowane?

Każdy obraz zawiera zalecane funkcji, ustaw dla tej wersji programu Visual Studio. Ogólnie rzecz biorąc instalacja obejmuje:

* Wszystkie dostępne obciążeń, w tym każde obciążenie zalecane składniki opcjonalne
* .NET 4.6.2 i .NET 4.7 zestawów SDK i Targeting Pack, narzędzia dla deweloperów
* Visual F#
* Rozszerzenie GitHub dla programu Visual Studio
* LINQ to SQL Tools

Stosujemy następujące polecenie w wierszu instalacji programu Visual Studio, podczas tworzenia obrazów:

```shell
    vs_enterprise.exe --allWorkloads --includeRecommended --passive ^
       --add Microsoft.Net.Component.4.7.SDK ^
       --add Microsoft.Net.Component.4.7.TargetingPack ^
       --add Microsoft.Net.Component.4.6.2.SDK ^
       --add Microsoft.Net.Component.4.6.2.TargetingPack ^
       --add Microsoft.Net.ComponentGroup.4.7.DeveloperTools ^
       --add Microsoft.VisualStudio.Component.FSharp ^
       --add Component.GitHub.VisualStudio ^
       --add Microsoft.VisualStudio.Component.LinqToSql
```

Jeśli obrazy nie obejmują funkcji programu Visual Studio, która jest wymagana, przekazują opinie za pośrednictwem narzędzia opinii, w prawym górnym rogu strony.

## <a name="what-size-vm-should-i-choose"></a>Rozmiar maszyny Wirtualnej należy wybrać?

Platforma Azure oferuje szeroką gamę rozmiarów maszyn wirtualnych. Ponieważ program Visual Studio jest zaawansowanym wielowątkowa aplikacja, ma rozmiar maszyny Wirtualnej, która zawiera co najmniej dwóch procesorów i 7 GB pamięci. Firma Microsoft zaleca następujących rozmiarów maszyn wirtualnych dla obrazów programu Visual Studio:

   * Maszyna wirtualna Standard_D2_v3
   * Standard_D2s_v3
   * Maszyna wirtualna Standard_D4_v3
   * Standard_D4s_v3
   * Maszyna wirtualna Standard_D2_v2
   * Standard_D2S_v2
   * Maszyna wirtualna Standard_D3_v2

Aby uzyskać więcej informacji na temat najnowszych rozmiarów maszyny, zobacz [rozmiary dla Windows maszyn wirtualnych na platformie Azure](/azure/virtual-machines/windows/sizes).

Za pomocą platformy Azure można ponownie zrównoważyć początkowy wybór, zmieniając rozmiar maszyny Wirtualnej. Możesz aprowizować nową maszynę Wirtualną o rozmiarze bardziej odpowiednie lub zmienić rozmiar istniejącej maszyny Wirtualnej na inny sprzęt w podstawowej. Aby uzyskać więcej informacji, zobacz [zmienić rozmiar maszyny Wirtualnej z systemem Windows](/azure/virtual-machines/windows/resize-vm).

## <a name="after-the-vm-is-running-whats-next"></a>Po uruchomieniu maszyny Wirtualnej, co przyniesie przyszłość?

Program Visual Studio następuje modelu "bring your own license" na platformie Azure. Podobnie jak w przypadku instalacji na sprzęcie, na jednym z pierwszych kroków jest licencjonowanie instalację programu Visual Studio. Aby odblokować programu Visual Studio, albo:
- Zaloguj się przy użyciu konta Microsoft, która jest skojarzona z subskrypcji programu Visual Studio
- Odblokuj programu Visual Studio za pomocą klucza produktu, dostarczone z Twojej początkowej kwoty zakupu

Aby uzyskać więcej informacji, zobacz [Zaloguj się do programu Visual Studio](../ide/signing-in-to-visual-studio.md) i [jak odblokować program Visual Studio](../ide/how-to-unlock-visual-studio.md).

## <a name="how-do-i-save-the-development-vm-for-future-or-team-use"></a>Jak mogę zapisać deweloperskiej maszynie Wirtualnej w przyszłości lub zespołu używać?

Spektrum środowisk deweloperskich jest bardzo duży i jest prawdziwy koszt związany z kompilowania bardziej złożonych środowiskach. Niezależnie od konfiguracji w danym środowisku można zapisać lub przechwycenia maszyny Wirtualnej skonfigurowanej jako "obrazu podstawowego" do użycia w przyszłości lub dla innych członków zespołu. Następnie podczas rozruchu nową maszynę Wirtualną, możesz aprowizować je z obrazu podstawowego zamiast obrazu z witryny Azure Marketplace.

Krótkie podsumowanie: Za pomocą narzędzia przygotowywania systemu (Sysprep) i Zamknij uruchomioną maszynę Wirtualną, a następnie przechwycić *(rysunek 1)* maszynę Wirtualną jako obraz przy użyciu interfejsu użytkownika w witrynie Azure portal. Zapisuje Azure `.vhd` pliku zawierającego obraz wybrane na koncie magazynu. Nowy obraz następnie wyświetlany jako zasób obrazu w Twojej subskrypcji listy zasobów.

<img src="media/capture-vm.png" alt="Capture an image through the Azure portal’s UI" style="border:3px solid Silver; display: block; margin: auto;"><center>*(Rysunek 1) Przechwycenie obrazu przy użyciu interfejsu użytkownika witryny Azure portal.*</center>

Aby uzyskać więcej informacji, zobacz [utworzenie obrazu zarządzanego uogólnionej maszyny wirtualnej na platformie Azure](/azure/virtual-machines/windows/capture-image-resource).

> [!IMPORTANT]
> Należy pamiętać przygotować maszynę Wirtualną przy użyciu narzędzia Sysprep. Jeśli pominiesz ten krok, Azure, nie można aprowizować Maszynę wirtualną z obrazu.

> [!NOTE]
> Nadal naliczane pewien koszt związany z magazynu obrazów, ale rosnących kosztów można nieznaczące w porównaniu do kosztów ogólnych odbudować maszyny Wirtualnej od zera dla każdego członka zespołu, który musi mieć jeden. Na przykład koszty kilka dolarów, można utworzyć i zapisać obraz 127 GB na miesiąc, będącego wielokrotnego użytku przez całego zespołu. Jednak te koszty są nieistotne względem godzin, w których każdemu pracownikowi inwestuje do skompilowania i sprawdzanie poprawności pola dev prawidłowo skonfigurowane, do ich użytku osobistego.

Ponadto zadania rozwoju lub technologii potrzebować więcej skali, takie jak różne typy konfiguracji rozwoju i wielu konfiguracji maszyny. Azure DevTest Labs umożliwia tworzenie _przepisy_ , automatyzacja konstrukcji swoje "złotego obrazu." DevTest Labs umożliwia także zarządzanie zasadami dla Twojego zespołu działających maszyn wirtualnych. [Dla deweloperów przy użyciu usługi Azure DevTest Labs](/azure/devtest-lab/devtest-lab-developer-lab) jest najlepsze źródło, aby uzyskać więcej informacji na temat usługi DevTest Labs.

## <a name="next-steps"></a>Następne kroki

Teraz, gdy wiesz o wstępnie skonfigurowanych obrazów programu Visual Studio, następnym krokiem jest do utworzenia nowej maszyny Wirtualnej:

* [Utwórz Maszynę wirtualną za pośrednictwem witryny Azure portal](/azure/virtual-machines/windows/quick-create-portal)
* [Omówienie maszyn wirtualnych Windows](/azure/virtual-machines/windows/overview)
