---
title: Projekty i rozwiązania
description: Ten dokument zawiera omówienie projektów i rozwiązań w programie Visual Studio dla komputerów Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/23/2019
ms.assetid: 8254505D-D96E-48BD-8A5E-CF6A917897EA
ms.openlocfilehash: ec62e9c0b449f5f2aed568735c2a10d1f6634eed
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66820959"
---
# <a name="projects-and-solutions-in-visual-studio-for-mac"></a>Projekty i rozwiązania w programie Visual Studio dla komputerów Mac

Ten artykuł zawiera omówienie *projektu* i *rozwiązania* koncepcje w programie Visual Studio dla komputerów Mac.

> [!NOTE] 
> Ten temat dotyczy programu Visual Studio dla komputerów Mac. Dla programu Visual Studio, Windows, zobacz [projektów i rozwiązań w programie Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="projects"></a>Projekty

Podczas tworzenia nowej aplikacji, witryny sieci Web, itp. w programie Visual Studio dla komputerów Mac należy uruchomić z projektem. Projekt zawiera wszystkie pliki wymagane (kod źródłowy, obrazów, plików danych itp.), które są wymagane do kompilowania pliku wykonywalnego, biblioteki lub witryny sieci Web.

Projekt został zdefiniowany w pliku (np. `.csproj` dla C# projektów) zawierającą kod xml, który definiuje plik i hierarchii folderów, ścieżek do plików i ustawień specyficznych dla projektu, takich jak ustawienia kompilacji.

Gdy projekt jest ładowany przez program Visual Studio dla komputerów Mac, w konsoli rozwiązania użyto pliku projektu, aby wyświetlić pliki i foldery w projekcie. Podczas kompilacji program MSBuild odczytuje ustawienia z pliku projektu, aby utworzyć plik wykonywalny.

## <a name="solutions"></a>Rozwiązania

A *rozwiązania* jest kontenerem tej grupy razem jeden lub więcej powiązanych projektów. Rozwiązania są opisane przez plik tekstowy (rozszerzenie `.sln`) swój własny unikatowy format; nie mają być edytowane ręcznie.

## <a name="managing-projects-in-the-solution-pad"></a>Zarządzanie projektami, w konsoli rozwiązania

Po utworzeniu projektu lub załadowany, służy Konsola rozwiązań do przeglądania i zarządzania, projekt lub rozwiązanie i pliki zawarte w. Poniższa ilustracja przedstawia Konsola rozwiązań za pomocą rozwiązania .NET Core, która zawiera dwa projekty:

![Przykładowe rozwiązanie z wieloma projektami](media/solution-example.png)

Można zarządzać właściwości projektów i rozwiązań, albo klikając dwukrotnie nazwę projektu lub rozwiązania, lub kliknij prawym przyciskiem myszy i wybierając polecenie **opcje**.

Więcej informacji o tych opcjach znajduje się w [właściwości projektu i rozwiązania zarządzania](managing-solutions-and-project-properties.md) artykułu.

## <a name="see-also"></a>Zobacz także

- [Rozwiązania i projekty w programie Visual Studio (Windows)](/visualstudio/ide/solutions-and-projects-in-visual-studio)
