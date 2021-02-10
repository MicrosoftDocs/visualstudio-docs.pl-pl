---
title: Korzystanie z programu Visual Studio na maszynie wirtualnej platformy Azure
titleSuffix: ''
description: Dowiedz się, jak używać programu Visual Studio na maszynie wirtualnej platformy Azure
ms.date: 11/17/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- azure services
- virtual machine
- installation
- visual studio
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7111c53a498fe10710ec2b328600052a7d4de0cd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935641"
---
# <a name="visual-studio-images-on-azure"></a><a id="top"></a> Obrazy programu Visual Studio na platformie Azure

Korzystanie z programu Visual Studio we wstępnie skonfigurowanej maszynie wirtualnej platformy Azure jest szybkim i łatwym sposobem na przechodzenie od niczego do środowiska deweloperskiego. Obrazy systemu z różnymi konfiguracjami programu Visual Studio są dostępne w [portalu Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/apps/category/compute?filters=virtual-machine-images%3Bmicrosoft%3Bwindows&page=1&subcategories=application-infrastructure).

Dopiero zaczynasz korzystać z platformy Azure? [Utwórz bezpłatne konto platformy Azure](https://azure.microsoft.com/free).

## <a name="what-configurations-and-versions-are-available"></a>Jakie konfiguracje i wersje są dostępne?

Obrazy dla najnowszych wersji głównych, Visual Studio 2019, Visual Studio 2017 i Visual Studio 2015 można znaleźć w witrynie Azure Marketplace.  Dla każdej wydanej wersji głównej zostanie wyświetlona oryginalna wersja "wydana do sieci Web" (RTW) i najnowsze zaktualizowane wersje.  Każda z tych wersji oferuje Visual Studio Enterprise i wersje społeczności programu Visual Studio.  Te obrazy są aktualizowane co najmniej co miesiąc w celu uwzględnienia najnowszych aktualizacji programu Visual Studio i systemu Windows.  Mimo że nazwy obrazów pozostają takie same, opis każdego obrazu obejmuje wersję zainstalowanego produktu i datę "od do obrazu".

| Wersja wydania                                                                                                                                          | Wersje              |    Wersja produktu    |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------:|:---------------------:|:-----------------------:|
| [Visual Studio 2019: Najnowsze (wersja 16,8)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio2019latest?tab=Overview) | Enterprise, społeczność | 16.8.0 wersja    |
| [Visual Studio 2019: RTW](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio2019?tab=Overview)                         | Przedsiębiorstwa            | 16.0.20 wersja    |
| [Visual Studio 2017: Najnowsze (wersja 15,9)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)           | Enterprise, społeczność | 15.9.29 wersja   |
| [Visual Studio 2017: RTW](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)                             | Enterprise, społeczność | 15.0.28 wersja   |
| [Visual Studio 2015: Najnowsze (Aktualizacja Update 3)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)               | Enterprise, społeczność | 14.0.25431.01 wersja |

> [!NOTE]
> Zgodnie z zasadami obsługi Microsoft pierwotnie wydana wersja (RTW) programu Visual Studio 2015 straciła ważność do obsługi. Program Visual Studio 2015 Update 3 jest jedyną pozostałą wersją oferowaną dla wiersza produktu Visual Studio 2015.

Aby uzyskać więcej informacji, zobacz [zasady obsługi programu Visual Studio](/visualstudio/productinfo/vs-servicing-vs).

## <a name="what-features-are-installed"></a>Jakie funkcje są instalowane?

Każdy obraz zawiera zalecany zestaw funkcji dla tej wersji programu Visual Studio. Zazwyczaj instalacja obejmuje następujące:

* Wszystkie dostępne obciążenia, w tym wszystkie zalecane składniki opcjonalne
* Zestawy SDK .NET 4.6.2 i .NET 4,7, pakiety docelowe i Narzędzia deweloperskie
* Visual F#
* Rozszerzenia GitHub dla programu Visual Studio
* Narzędzia LINQ to SQL

W przypadku tworzenia obrazów w programie Visual Studio używany jest następujący wiersz polecenia:

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

Jeśli obrazy nie zawierają wymaganej funkcji programu Visual Studio, Prześlij opinię za pomocą narzędzia opinii w prawym górnym rogu strony.

## <a name="what-size-vm-should-i-choose"></a>Jaką maszynę wirtualną należy wybrać?

Platforma Azure oferuje szeroką gamę rozmiarów maszyn wirtualnych. Ponieważ program Visual Studio jest zaawansowaną aplikacją wielowątkową, należy użyć rozmiaru maszyny wirtualnej, który zawiera co najmniej dwa procesory i 7 GB pamięci. W przypadku obrazów programu Visual Studio zalecamy używanie następujących rozmiarów maszyn wirtualnych:

* Standardowa_D2_v3
* Standardowa_D2s_v3
* Standardowa_D4_v3
* Standardowa_D4s_v3
* Standardowa_D2_v2
* Standard_D2S_v2
* Standardowa_D3_v2

Aby uzyskać więcej informacji na temat najnowszych rozmiarów maszyn, zobacz [rozmiary maszyn wirtualnych z systemem Windows na platformie Azure](/azure/virtual-machines/windows/sizes).

Na platformie Azure możesz ponownie zrównoważyć początkowy wybór, zmieniając rozmiar maszyny wirtualnej. Można udostępnić nową maszynę wirtualną z bardziej odpowiednim rozmiarem lub zmienić rozmiar istniejącej maszyny wirtualnej na inny, podstawowy sprzęt. Aby uzyskać więcej informacji, zobacz [Zmienianie rozmiaru maszyny wirtualnej z systemem Windows](/azure/virtual-machines/windows/resize-vm).

## <a name="after-the-vm-is-running-whats-next"></a>Co dalej, gdy maszyna wirtualna jest uruchomiona?

Program Visual Studio jest zgodny z modelem "Przenieś własną licencję" na platformie Azure. Podobnie jak w przypadku instalacji na sprzęcie zastrzeżonym, jeden z pierwszych kroków umożliwia Licencjonowanie instalacji programu Visual Studio. Aby odblokować program Visual Studio, należy:
- Zaloguj się przy użyciu konto Microsoft, który jest skojarzony z subskrypcją programu Visual Studio
- Odblokuj program Visual Studio przy użyciu klucza produktu dołączonego do początkowego zakupu

Aby uzyskać więcej informacji, zobacz artykuł [Logowanie do programu Visual Studio](../ide/signing-in-to-visual-studio.md) i [jak odblokować program Visual Studio](../ide/how-to-unlock-visual-studio.md).

## <a name="how-do-i-save-the-development-vm-for-future-or-team-use"></a>Jak mogę zapisać maszynę wirtualną programistyczną do użytku w przyszłości lub w zespole?

Zakres środowisk programistycznych jest duży i istnieje rzeczywisty koszt związany z tworzeniem bardziej złożonych środowisk. Niezależnie od konfiguracji środowiska można zapisać lub przechwycić skonfigurowaną maszynę wirtualną jako "obraz podstawowy" do użytku w przyszłości lub dla innych członków zespołu. Następnie podczas uruchamiania nowej maszyny wirtualnej należy ją udostępnić z obrazu podstawowego, a nie z obrazu portalu Azure Marketplace.

Szybkie podsumowanie: Użyj narzędzia do przygotowywania systemu (Sysprep) i Zamknij uruchomioną maszynę wirtualną, a następnie Przechwyć *(rysunek 1)* maszynę wirtualną jako obraz za pomocą interfejsu użytkownika w Azure Portal. Na platformie Azure jest zapisywany `.vhd` plik zawierający obraz na wybrane konto magazynu. Nowy obraz zostanie następnie wyświetlony jako zasób obrazu na liście zasobów subskrypcji.

![Przechwytywanie obrazu za pomocą interfejsu użytkownika Azure Portal](media/capture-vm.png)

*(Rysunek 1) Przechwyć obraz za pomocą interfejsu użytkownika Azure Portal.*

Aby uzyskać więcej informacji, zobacz [Tworzenie obrazu zarządzanego uogólnionej maszyny wirtualnej na platformie Azure](/azure/virtual-machines/windows/capture-image-resource).

> [!IMPORTANT]
> Nie zapomnij użyć programu Sysprep, aby przygotować maszynę wirtualną. Jeśli ten krok zostanie pominięty, platforma Azure nie będzie mogła zainicjować obsługi administracyjnej maszyny wirtualnej na podstawie obrazu.

> [!NOTE]
> Nadal są naliczane pewne koszty magazynowania obrazów, ale koszt przyrostowy może być nieistotny w porównaniu z kosztami kosztów, aby odbudować maszynę wirtualną od początku dla każdego członka zespołu, który go potrzebuje. Na przykład kosztem jest kilka dolarów, aby utworzyć i zapisać obraz 127 GB na miesiąc, który jest wielokrotnego użytku przez cały zespół. Jednak te koszty są nieznaczące w porównaniu z godzinami każdego pracownika inwestującego w celu utworzenia i zweryfikowania prawidłowo skonfigurowanego pola dev do użytku osobistego.

Ponadto zadania programistyczne lub technologie mogą wymagać większej skali, takich jak różne konfiguracje deweloperskie i konfiguracje wielu maszyn. Za pomocą Azure DevTest Labs można utworzyć _przepisy_ , które automatyzują Konstruowanie "złota obrazu". Za pomocą DevTest Labs można także zarządzać zasadami dla uruchomionych maszyn wirtualnych Twojego zespołu. [Używanie Azure DevTest Labs dla deweloperów](/azure/devtest-lab/devtest-lab-developer-lab) jest najlepszym źródłem do uzyskania dodatkowych informacji na temat DevTest Labs.

## <a name="next-steps"></a>Następne kroki

Teraz, gdy znasz wstępnie skonfigurowane obrazy programu Visual Studio, następnym krokiem jest utworzenie nowej maszyny wirtualnej:

* [Tworzenie maszyny wirtualnej za pomocą Azure Portal](/azure/virtual-machines/windows/quick-create-portal)
* [Przegląd Windows Virtual Machines](/azure/virtual-machines/windows/overview)
