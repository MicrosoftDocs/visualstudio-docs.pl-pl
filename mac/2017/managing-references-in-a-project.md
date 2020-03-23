---
title: Zarządzanie odwołaniami w projekcie
description: W tym artykule opisano sposób zarządzania odwołaniami w projekcie w programie Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: f9925954083c7fe64ad29c7cfed618a84d7a6386
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984859"
---
# <a name="managing-references-in-a-project"></a>Zarządzanie odwołaniami w projekcie

Program Visual Studio dla komputerów Mac udostępnia dwa sposoby dodawania dodatkowych odwołań do projektu:

![Informacje o projekcie](media/projects-and-solutions-image10.png)

Są to:

* Dokumentacja
* NuGets (Dodano za pośrednictwem folderu Pakiety)

Ponadto odwołania do sieci Web i odwołania natywne można również dodać do dowolnego projektu.

## <a name="assembly-references"></a>Odniesienia do złożenia

Każda struktura w ramach platformy Xamarin jest dostarczana z kilkunastoma zestawami. Nie wszystkie z tych pakietów zestawu są domyślnie odwołuje się do projektu.

Aby edytować pakiety, do których odwołuje się projekt, użyj okna dialogowego **Edytuj odwołania,** które można wyświetlić, klikając dwukrotnie folder Odwołania lub wybierając pozycję Edytuj odwołania w jego **akcjach** menu kontekstowego:

![Okno dialogowe Odwołania do złożenia](media/projects-and-solutions-image11.png)

Aby uzyskać informacje na temat zestawów dostępnych dla każdej platformy Xamarin, zapoznaj się z [przewodnikiem Dostępne zestawy.](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/)

## <a name="nuget"></a>NuGet

NuGet jest najpopularniejszym menedżerem pakietów dla rozwoju platformy .NET. Obsługa nuget w programie Visual Studio for Mac umożliwia wyszukiwanie pakietów do dodania do projektu.

Aby to zrobić, kliknij prawym przyciskiem myszy folder **Pakiet** w panelu rozwiązania i wybierz pozycję Dodaj pakiety.

Więcej informacji na temat korzystania z pakietu NuGet znajduje się w [including pakietu NuGet w](nuget-walkthrough.md) instruktażu projektu.

## <a name="see-also"></a>Zobacz też

- [Zarządzanie odwołaniami (Visual Studio w systemie Windows)](/visualstudio/ide/managing-references-in-a-project)
- [Dodawanie odwołań przy użyciu nuget a sdk rozszerzenia (Visual Studio w systemie Windows)](/visualstudio/ide/adding-references-using-nuget-versus-an-extension-sdk)