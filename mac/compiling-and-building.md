---
title: Kompilowanie i tworzenie
description: W tym artykule opisano sposób kompilowania i kompilowania projektów i rozwiązań w Visual Studio dla komputerów Mac
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/03/2021
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: a24c57907afedb4f02068a071d2c9f81eb8962bb
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2021
ms.locfileid: "108640977"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Kompilowanie i kompilowanie w Visual Studio dla komputerów Mac

Visual Studio dla komputerów Mac można używać do kompilowania aplikacji i tworzenia zestawów podczas opracowywania projektu. Ważne jest, aby często tworzyć kod, aby umożliwić szybkie identyfikowanie niezgodności typów, błędnej składni, błędnie napisanych słów kluczowych i innych błędów czasu kompilacji. Podczas budowania i debugowania można również znaleźć i naprawić błędy czasu działania, takie jak błędy logiki, we/wy i błędy dzielenia przez zero.

Pomyślna kompilacja oznacza, że kod źródłowy zawiera poprawną składnię i wszystkie statyczne odwołania do bibliotek, zestawów i innych składników mogą zostać rozwiązane. Proces kompilacji tworzy plik wykonywalny aplikacji. Ten plik wykonywalny można następnie przetestować za pomocą debugowania i różnych rodzajów testów ręcznych i automatycznych w celu zweryfikowania jakości kodu. Po pełnym przetestowaniu aplikacji możesz skompilować wersję wydania, aby wdrożyć ją u klientów.

Na komputerze Mac można użyć dowolnej z następujących metod kompilowania aplikacji: Visual Studio dla komputerów Mac, narzędzia wiersza polecenia programu MSBuild lub Azure Pipelines.

| Metoda kompilacji | Korzyści |
| --- |--- | --- |
| Visual Studio dla komputerów Mac |- Tworzenie kompilacji natychmiast i testowanie ich w debugerze.<br />— Uruchamianie kompilacji wieloprocesorowych dla projektów w języku C#.<br />- Dostosowywanie różnych aspektów systemu kompilacji. |
| Wiersz polecenia programu MSBuild| - Kompilowanie projektów bez instalowania Visual Studio dla komputerów Mac.<br />- Uruchamianie kompilacji wieloprocesorowych dla wszystkich typów projektów.<br />— Dostosowywanie większości obszarów systemu kompilacji.|
| Azure Pipelines | — Zautomatyzuj proces kompilacji w ramach potoku ciągłej integracji/ciągłego dostarczania.<br />— Stosowanie testów automatycznych przy każdej kompilacji.<br />— W procesach kompilacji można korzystać z praktycznie nieograniczonych zasobów opartych na chmurze.<br />— Modyfikowanie przepływu pracy kompilacji i tworzenie działań kompilacji w celu wykonywania głęboko dostosowanych zadań.|

Dokumentacja w tej sekcji zawiera dalsze szczegóły procesu kompilacji opartego na środowiskach IDE. Aby kompilować aplikacje z wiersza polecenia bez instalowania Visual Studio dla komputerów Mac, możesz zainstalować najnowszą wersję [zestaw .NET Core SDK](https://dotnet.microsoft.com/download). Aby uzyskać więcej informacji na temat tworzenia aplikacji za pomocą wiersza polecenia, zobacz [MSBuild](/visualstudio/msbuild/msbuild). Aby uzyskać szczegółowe informacje na temat tworzenia aplikacji za pomocą Azure Pipelines, zobacz [Azure Pipelines](/azure/devops/pipelines).


> [!NOTE]
> Ten temat dotyczy Visual Studio dla komputerów Mac. Aby uzyskać Visual Studio w systemie Windows, zobacz [Compile and build in Visual Studio (Kompilowanie i kompilowanie w systemie Visual Studio).](/visualstudio/ide/compiling-and-building-in-visual-studio)


## <a name="building-from-the-ide"></a>Kompilacja z IDE

Visual Studio dla komputerów Mac umożliwia natychmiastowe tworzenie i uruchamianie kompilacji, jednocześnie zapewniając kontrolę nad funkcjami kompilacji. Podczas tworzenia projektu program Visual Studio dla komputerów Mac domyślną konfigurację kompilacji, która określa kontekst kompilacji. Możesz edytować domyślne konfiguracje kompilacji, a także tworzyć własne. Utworzenie lub zmodyfikowanie tych konfiguracji spowoduje automatyczne zaktualizowanie pliku projektu, który jest następnie używany przez program MSBuild do kompilowania projektu.

Aby uzyskać więcej informacji na temat sposobu tworzenia projektów i rozwiązań w idee, zobacz [Przewodnik Building and cleaning Projects and Solutions](building-and-cleaning-projects-and-solutions.md) (Kompilowanie i czyszczenie projektów i rozwiązań).

Visual Studio dla komputerów Mac można również użyć do następujących czynności:

* Zmień ścieżkę wyjściową. Ta opcja jest edytowana w opcjach projektu:

    ![Zmienianie ścieżki wyjściowej](media/compiling-and-building-image4.png)

* Zmień poziom szczegółowości danych wyjściowych kompilacji:

    ![Zmienianie szczegółowości kompilacji](media/compiling-and-building-image5.png)

* Dodaj Polecenia niestandardowe przed, w trakcie lub po zakończeniu budowania lub czyszczenia:

    ![dodawanie poleceń niestandardowych](media/compiling-and-building-image6.png)


## <a name="see-also"></a>Zobacz też

- [Kompilowanie i kompilowanie (Visual Studio w systemie Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)
