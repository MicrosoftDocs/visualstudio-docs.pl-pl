---
title: Zarządzanie odwołaniami w projekcie
description: W tym artykule opisano sposób zarządzania odwołań w projekcie w programie Visual Studio dla komputerów Mac
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: a14630c5448632a939e1768040b910caf6276c2a
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67692920"
---
# <a name="managing-references-in-a-project"></a>Zarządzanie odwołaniami w projekcie

Program Visual Studio for Mac oferuje dwa sposób dodawania dodatkowych odwołania do projektu:

![Informacje o projekcie](media/projects-and-solutions-image10.png)

Są to:

* Odwołania
* Rozszerzeń Nuget (dodane za pośrednictwem Packages folder)

Ponadto odwołania sieci Web i odwołania natywne również można dodać do każdego projektu.

## <a name="assembly-references"></a>Odwołania do zestawów

Każdy struktury platformy Xamarin jest dostarczany z ponad tuzina zestawów. Nie wszystkie te pakiety zestawu w projekcie są określone przez domyślny.

Aby edytować pakietów, do których istnieją odwołania w projekcie, należy użyć **Edytuj odwołania** okno dialogowe, które można wyświetlić, klikając dwukrotnie plik w folderze odwołania lub wybierając **Edytuj odwołania** na kontekst menu Akcje:

![Okno dialogowe odwołania do zestawu](media/projects-and-solutions-image11.png)

Aby uzyskać informacji na temat zestawów dostępności dla każdej platformy Xamarin, zobacz [dostępnych zestawów](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/) przewodnik.

## <a name="nuget"></a>NuGet

NuGet jest najbardziej popularnych Menedżer pakietów dla programowania na platformie .NET. Program Visual Studio dla komputerów Mac, obsługę pakietów NuGet umożliwia wyszukiwanie pakiety do dodania do projektu.

Aby to zrobić, kliknij prawym przyciskiem myszy **pakietu** folderu w konsoli rozwiązania, a następnie wybierz opcję Dodaj pakiety.

Więcej informacji na temat korzystania z pakietu NuGet jest podawany jako [pakietu w tym NuGet w projekcie](nuget-walkthrough.md) wskazówki.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie odwołaniami (Visual Studio Windows)](/visualstudio/ide/managing-references-in-a-project)
- [Dodawaniem odwołań za pomocą NuGet a extension SDK (Visual Studio Windows)](/visualstudio/ide/adding-references-using-nuget-versus-an-extension-sdk)