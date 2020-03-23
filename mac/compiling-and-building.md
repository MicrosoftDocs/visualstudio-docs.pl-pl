---
title: Kompilowanie i tworzenie
description: W tym artykule opisano sposób kompilowania i tworzenia projektów i rozwiązań w programie Visual Studio dla komputerów Mac
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 08/29/2019
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: b4f1cfc3dfdffcc3dd4cb90cd7d29d4333578b9a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128419"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Kompilowanie i tworzenie w programie Visual Studio dla komputerów Mac

Visual Studio dla komputerów Mac może służyć do tworzenia aplikacji i tworzenia zestawów podczas opracowywania projektu. Ważne jest, aby często tworzyć kod, aby umożliwić szybkie identyfikowanie niezgodności typów, błędną składnię, błędnie napisane słowa kluczowe i inne błędy w czasie kompilacji. Tworząc następnie debugowanie, można również znaleźć i naprawić błędy w czasie wykonywania, takie jak logika, we/wy i błędy dzielenia przez zero.

Pomyślna kompilacja oznacza, że kod źródłowy zawiera poprawną składnię i wszystkie statyczne odwołania do bibliotek, zestawów i innych składników można rozwiązać. Proces kompilacji tworzy plik wykonywalny aplikacji. Ten plik wykonywalny może być następnie testowany za pomocą debugowania i różnych rodzajów testów ręcznych i automatycznych w celu sprawdzenia jakości kodu. Po w pełni przetestowane aplikacji, można skompilować wersję wersji do wdrożenia dla klientów.

Na komputerze Mac można użyć dowolnej z następujących metod do tworzenia aplikacji: Visual Studio dla komputerów Mac, narzędzia wiersza polecenia MSBuild lub potoki platformy Azure.

| Metoda kompilacji | Korzyści |
| --- |--- | --- |
| Visual Studio dla komputerów Mac |- Tworzenie kompilacji natychmiast i przetestować je w debugera.<br />- Uruchamianie kompilacji wieloprocesorowych dla projektów języka C#.<br />- Dostosuj różne aspekty systemu kompilacji. |
| Wiersz polecenia MSBuild| - Tworzenie projektów bez instalowania programu Visual Studio dla komputerów Mac.<br />- Uruchamianie kompilacji wieloprocesorowych dla wszystkich typów projektów.<br />- Dostosuj większość obszarów systemu kompilacji.|
| Azure Pipelines | - Automatyzacja procesu kompilacji w ramach ciągłej integracji / ciągłego dostarczania rurociągu.<br />- Zastosuj zautomatyzowane testy z każdym kompilacji.<br />- Zatrudniaj praktycznie nieograniczone zasoby oparte na chmurze do tworzenia procesów.<br />- Zmodyfikuj przepływ pracy kompilacji i tworzenie działań kompilacji do wykonywania zadań głęboko dostosowane.|

Dokumentacja w tej sekcji przechodzi do dalszych szczegółów procesu kompilacji opartej na IDE. Aby uzyskać więcej informacji na temat tworzenia aplikacji za pośrednictwem wiersza polecenia, zobacz [MSBuild](/visualstudio/msbuild/msbuild). Aby uzyskać szczegółowe informacje na temat tworzenia aplikacji za pomocą usługi Azure Pipelines, zobacz [Potoki platformy Azure.](/azure/devops/pipelines)


> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio dla komputerów Mac. Aby zapoznać się z programem Visual Studio w systemie Windows, zobacz [Kompilowanie i tworzenie w programie Visual Studio](/visualstudio/ide/compiling-and-building-in-visual-studio).


## <a name="building-from-the-ide"></a>Kompilacja z IDE

Visual Studio dla komputerów Mac umożliwia natychmiastowe tworzenie i uruchamianie kompilacji, zapewniając jednocześnie kontrolę nad funkcjami kompilacji. Podczas tworzenia projektu program Visual Studio dla komputerów Mac definiuje domyślną konfigurację kompilacji, która ustawia kontekst dla kompilacji. Można edytować domyślne konfiguracje kompilacji, a także tworzyć własne. Tworzenie lub modyfikowanie tych konfiguracji spowoduje automatyczną aktualizację pliku projektu, który jest następnie używany przez FIRMĘ MSBuild do tworzenia projektu.

Aby uzyskać więcej informacji na temat tworzenia projektów i rozwiązań w IDE, zobacz [budynku i czyszczenia projektów i rozwiązań](building-and-cleaning-projects-and-solutions.md) przewodnik.

Visual Studio dla komputerów Mac może również służyć do wykonywania następujących czynności:

* Zmień ścieżkę wyjściową. Jest to edytowane w opcjach programu Project:

    ![Zmienianie ścieżki wyjściowej](media/compiling-and-building-image4.png)

* Zmień szczegółowość danych wyjściowych kompilacji:

    ![Zmiana szczegółowości kompilacji](media/compiling-and-building-image5.png)

* Dodawanie poleceń niestandardowych przed, w trakcie lub po zakończeniu tworzenia lub czyszczenia:

    ![dodawanie poleceń niestandardowych](media/compiling-and-building-image6.png)


## <a name="see-also"></a>Zobacz też

- [Kompilowanie i tworzenie (Visual Studio w systemie Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)
