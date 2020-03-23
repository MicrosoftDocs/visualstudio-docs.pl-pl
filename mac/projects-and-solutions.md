---
title: Projekty i rozwiązania
description: Ten dokument zawiera omówienie projektów i rozwiązań w programie Visual Studio dla komputerów Mac.
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/23/2019
ms.assetid: 8254505D-D96E-48BD-8A5E-CF6A917897EA
ms.openlocfilehash: 92e7a47f7ea2b931c0b923d10e115843d315d024
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "70107819"
---
# <a name="projects-and-solutions-in-visual-studio-for-mac"></a>Projekty i rozwiązania w programie Visual Studio dla komputerów Mac

Ten artykuł zawiera omówienie *koncepcji projektu* i *rozwiązania* w programie Visual Studio dla komputerów Mac.

> [!NOTE] 
> W tym temacie stosuje się do programu Visual Studio dla komputerów Mac. W programie Visual Studio w systemie Windows zobacz [Projekty i rozwiązania w programie Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="projects"></a>Projekty

Podczas tworzenia nowej aplikacji, witryny sieci Web itp. Projekt zawiera wszystkie wymagane pliki (kod źródłowy, obrazy, pliki danych itp.), które są potrzebne do skompilowania pliku wykonywalnego, biblioteki lub witryny sieci Web.

Projekt jest definiowany przez plik (np. dla projektów C#), `.csproj` który zawiera xml, który definiuje hierarchię plików i folderów, ścieżki do plików i ustawienia specyficzne dla projektu, takie jak ustawienia kompilacji.

Gdy projekt jest ładowany przez program Visual Studio dla komputerów Mac, Solution Pad używa pliku projektu do wyświetlania plików i folderów w projekcie. Podczas kompilacji MSBuild odczytuje ustawienia z pliku projektu, aby utworzyć plik wykonywalny.

## <a name="solutions"></a>Rozwiązania

*Rozwiązanie* jest kontenerem, który grupuje jeden lub więcej powiązanych projektów. Rozwiązania są opisane przez plik tekstowy (rozszerzenie) `.sln`z własnym unikalnym formatem; nie jest przeznaczony do edycji ręcznie.

## <a name="managing-projects-in-the-solution-pad"></a>Zarządzanie projektami w panelu rozwiązań

Po utworzeniu lub załadowaniu projektu można użyć panelu rozwiązania do wyświetlania projektu lub rozwiązania oraz zarządzania nimi oraz plików zawartych w nim. Na poniższej ilustracji przedstawiono klawiaturę solution pad z rozwiązaniem .NET Core, które zawiera dwa projekty:

![Przykładowe rozwiązanie z wieloma projektami](media/solution-example.png)

Właściwości zarówno projektów, jak i rozwiązań można zarządzać, klikając dwukrotnie nazwę projektu lub rozwiązania lub klikając prawym przyciskiem myszy i wybierając polecenie **Opcje**.

Więcej informacji na temat tych opcji znajduje się w [artykule Zarządzanie rozwiązaniami i właściwościami projektu.](managing-solutions-and-project-properties.md)

## <a name="see-also"></a>Zobacz też

- [Rozwiązania i projekty w programie Visual Studio (Windows)](/visualstudio/ide/solutions-and-projects-in-visual-studio)
