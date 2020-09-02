---
title: Kompilowanie i tworzenie
description: W tym artykule opisano sposób kompilowania i kompilowania projektów oraz rozwiązań w Visual Studio dla komputerów Mac
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 08/29/2019
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: b4f1cfc3dfdffcc3dd4cb90cd7d29d4333578b9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "71128419"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Kompilowanie i kompilowanie w Visual Studio dla komputerów Mac

Visual Studio dla komputerów Mac może służyć do kompilowania aplikacji i tworzenia zestawów podczas opracowywania projektu. Ważne jest, aby kompilować swój kod często, aby umożliwić szybkie identyfikowanie niezgodności typów, błędnej składni, błędnie napisanego słowa kluczowego i innych błędów w czasie kompilacji. Dzięki skompilowaniu debugowania można także znajdować i naprawiać błędy czasu wykonywania, takie jak logika, we/wy i błędy dzielenia przez zero.

Pomyślne kompilacje oznacza, że kod źródłowy zawiera poprawną składnię i wszystkie statyczne odwołania do bibliotek, zestawów i innych składników mogą zostać rozpoznane. Proces kompilacji tworzy plik wykonywalny aplikacji. Ten plik wykonywalny może zostać następnie przetestowany przez debugowanie i różne rodzaje testów ręcznych i zautomatyzowanych w celu sprawdzenia jakości kodu. Po pełnym przetestowaniu aplikacji możesz skompilować wersję wydania, aby wdrożyć ją dla klientów.

Na komputerze Mac możesz użyć dowolnej z następujących metod, aby skompilować aplikację: Visual Studio dla komputerów Mac, narzędzia wiersza polecenia programu MSBuild lub Azure Pipelines.

| Metoda kompilacji | Korzyści |
| --- |--- | --- |
| Visual Studio for Mac |— Natychmiast Twórz kompilacje i Testuj je w debugerze.<br />— Uruchom kompilacje wieloprocesorowe dla projektów w języku C#.<br />-Dostosowywanie różnych aspektów systemu kompilacji. |
| Wiersz polecenia MSBuild| -Kompiluj projekty bez instalowania Visual Studio dla komputerów Mac.<br />— Uruchom kompilacje wieloprocesorowe dla wszystkich typów projektów.<br />-Dostosowywanie większości obszarów systemu kompilacji.|
| Azure Pipelines | — Automatyzuj proces kompilacji w ramach potoku ciągłej integracji/ciągłego dostarczania.<br />-Zastosuj testy automatyczne przy każdej kompilacji.<br />— Wykorzystuj praktycznie nieograniczone zasoby oparte na chmurze dla procesów kompilacji.<br />— Modyfikuj przepływ pracy kompilacji i twórz działania kompilacji, aby wykonywać głęboko dostosowane zadania.|

Dokumentacja w tej sekcji zawiera dalsze szczegóły procesu kompilacji opartego na środowisku IDE. Aby uzyskać więcej informacji na temat tworzenia aplikacji za pomocą wiersza polecenia, zobacz [MSBuild](/visualstudio/msbuild/msbuild). Aby uzyskać szczegółowe informacje na temat tworzenia aplikacji z Azure Pipelines, zobacz [Azure Pipelines](/azure/devops/pipelines).


> [!NOTE]
> Ten temat ma zastosowanie do Visual Studio dla komputerów Mac. W przypadku programu Visual Studio w systemie Windows, zobacz [Kompilowanie i kompilowanie w programie Visual Studio](/visualstudio/ide/compiling-and-building-in-visual-studio).


## <a name="building-from-the-ide"></a>Kompilacja z IDE

Visual Studio dla komputerów Mac umożliwia natychmiastowe tworzenie i uruchamianie kompilacji, a jednocześnie zapewnia kontrolę nad funkcjami kompilacji. Podczas tworzenia projektu, Visual Studio dla komputerów Mac definiuje domyślną konfigurację kompilacji, która ustawia kontekst dla kompilacji. Można edytować domyślne konfiguracje kompilacji, a także utworzyć własne. Utworzenie lub zmodyfikowanie tych konfiguracji spowoduje automatyczne zaktualizowanie pliku projektu, który następnie jest używany przez program MSBuild do kompilowania projektu.

Aby uzyskać więcej informacji na temat sposobu kompilowania projektów i rozwiązań w środowisku IDE, zobacz Przewodnik [tworzenia i czyszczenia projektów i rozwiązań](building-and-cleaning-projects-and-solutions.md) .

Visual Studio dla komputerów Mac można również użyć do wykonania następujących czynności:

* Zmień ścieżkę wyjściową. Jest to edytowane w opcjach projektu:

    ![Zmień ścieżkę wyjściową](media/compiling-and-building-image4.png)

* Zmień poziom szczegółowości danych wyjściowych kompilacji:

    ![Zmień szczegółowość kompilacji](media/compiling-and-building-image5.png)

* Dodaj niestandardowe polecenia przed, w trakcie lub po skompilowaniu lub oczyszczeniu:

    ![Dodawanie poleceń niestandardowych](media/compiling-and-building-image6.png)


## <a name="see-also"></a>Zobacz też

- [Kompiluj i Kompiluj (Visual Studio w systemie Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)
