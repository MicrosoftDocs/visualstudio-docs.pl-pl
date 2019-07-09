---
title: Kompilowanie i tworzenie
description: W tym artykule opisano sposób skompilować i utworzyć projekty i rozwiązania w programie Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: 0165594b4c2d77005c2a9ef921cce457f6f2d0f6
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693119"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Kompilowanie i tworzenie w programie Visual Studio dla komputerów Mac

Program Visual Studio for Mac może służyć do tworzenia aplikacji i tworzyć zestawy podczas tworzenia projektu. Jest ważne skompilować i utworzyć kod wcześnie i często, dzięki czemu można zidentyfikować niezgodności typów i inne błędy kompilacji.

## <a name="building-from-the-ide"></a>Kompilacja z IDE

Za pomocą programu Visual Studio dla komputerów Mac umożliwia tworzenie i uruchamianie opiera się natychmiast, zapewniając nadal kontrolować funkcje kompilacji. Program Visual Studio for Mac używa programu MSBuild jako podstawowej systemu kompilacji.

Wszystkie projekty i rozwiązania utworzone w środowisku IDE ma domyślnej konfiguracji kompilacji, definiującą kontekst dla kompilacji. Te konfiguracje mogą być edytowane, lub możesz utworzyć swój własny. Tworzenie lub modyfikowanie tych konfiguracji automatycznie aktualizuje plik projektu, który jest następnie używany przez program MSBuild do kompilowania projektu.

Aby uzyskać więcej informacji na temat sposobu tworzenia projektów i rozwiązań w środowisku IDE, zobacz [kompilowanie oraz Oczyszczanie projektów i rozwiązań](building-and-cleaning-projects-and-solutions.md) przewodnik.

Program Visual Studio for Mac można również wykonać następujące czynności:

* Zmienianie ścieżki wyjściowej. To jest edytowany w opcjach projektu:

    ![Zmień ścieżkę wyjściową](media/compiling-and-building-image4.png)

* Zmień poziom szczegółowości danych wyjściowych kompilacji:

    ![Zmień poziom szczegółowości](media/compiling-and-building-image5.png)

* Dodaj niestandardowe polecenia przed, w trakcie lub po Tworzenie lub czyszczenie:

    ![Dodawanie poleceń niestandardowych](media/compiling-and-building-image6.png)

## <a name="building-from-command-line"></a>Tworzenie z wiersza polecenia

Można użyć aparatu kompilacji MSBuild do kompilowania aplikacji z poziomu wiersza polecenia.

Zobacz [MSBuild](/visualstudio/msbuild/msbuild) zawartości, aby uzyskać więcej informacji na temat korzystania z programu MSBuild.

## <a name="building-from-azure-pipelines"></a>Tworzenie z potoków platformy Azure

* [Tworzenie aplikacji platformy Xamarin](/vsts/pipelines/apps/mobile/xamarin?view=vsts&tabs=vsts)
* [Ciągła integracja za pomocą platformy Xamarin](https://developer.xamarin.com/guides/cross-platform/ci/)

## <a name="see-also"></a>Zobacz także

- [Skompilować i utworzyć (Visual Studio Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)