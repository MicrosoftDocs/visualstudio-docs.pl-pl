---
title: Projekty i rozwiązania
description: Ten dokument zawiera omówienie projektów i rozwiązań w Visual Studio dla komputerów Mac.
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 8254505D-D96E-48BD-8A5E-CF6A917897EA
ms.openlocfilehash: c52b8513937505b40d17f7cd9fc05d9cf6a47941
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493403"
---
# <a name="projects-and-solutions-in-visual-studio-for-mac"></a>Projekty i rozwiązania w Visual Studio dla komputerów Mac

Ten artykuł zawiera omówienie pojęć dotyczących *projektu* i *rozwiązania* w Visual Studio dla komputerów Mac.

> [!NOTE] 
> Ten temat ma zastosowanie do Visual Studio dla komputerów Mac. W przypadku programu Visual Studio w systemie Windows Zapoznaj [się z tematem projekty i rozwiązania w programie Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="projects"></a>Projekty

Podczas tworzenia nowej aplikacji, witryny sieci Web itd. w Visual Studio dla komputerów Mac Zacznij od projektu. Projekt zawiera wszystkie wymagane pliki (kod źródłowy, obrazy, pliki danych itp.), które są potrzebne do skompilowania pliku wykonywalnego, biblioteki lub witryny sieci Web.

Projekt jest definiowany przez plik (np. `.csproj` dla projektów C#), który zawiera kod XML, który definiuje hierarchię plików i folderów, ścieżki do plików i ustawienia specyficzne dla projektu, takie jak ustawienia kompilacji.

Gdy projekt jest ładowany przez Visual Studio dla komputerów Mac, okno rozwiązanie używa pliku projektu do wyświetlania plików i folderów w projekcie. Podczas kompilacji program MSBuild odczytuje ustawienia z pliku projektu w celu utworzenia pliku wykonywalnego.

## <a name="solutions"></a>Rozwiązania

*Rozwiązanie* jest kontenerem, który grupuje jednocześnie jeden lub więcej powiązanych projektów. Rozwiązania są opisane przez plik tekstowy (rozszerzenie `.sln` ) z własnym unikatowym formatem; nie jest przeznaczony do edycji.

## <a name="managing-projects-in-the-solution-window"></a>Zarządzanie projektami w oknie rozwiązania

Po utworzeniu lub załadowaniu projektu można użyć okna rozwiązanie do wyświetlania projektu lub rozwiązania i zarządzania nim oraz plikami zawartymi w programie. Na poniższej ilustracji przedstawiono okno rozwiązania z rozwiązaniem .NET Core, które zawiera dwa projekty:

![Przykładowe rozwiązanie z wieloma projektami](media/solution-example.png)

Właściwościami projektów i rozwiązań można zarządzać przez dwukrotne kliknięcie projektu lub nazwy rozwiązania lub kliknięcie prawym przyciskiem myszy i wybranie **opcji**.

Więcej informacji na temat tych opcji znajduje się w artykule [zarządzanie rozwiązaniami i właściwościami projektu](managing-solutions-and-project-properties.md) .

## <a name="see-also"></a>Zobacz też

- [Rozwiązania i projekty w programie Visual Studio (Windows)](/visualstudio/ide/solutions-and-projects-in-visual-studio)
