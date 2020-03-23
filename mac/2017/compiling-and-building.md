---
title: Kompilowanie i tworzenie
description: W tym artykule opisano sposób kompilowania i tworzenia projektów i rozwiązań w programie Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: 0165594b4c2d77005c2a9ef921cce457f6f2d0f6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983608"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Kompilowanie i tworzenie w programie Visual Studio dla komputerów Mac

Visual Studio dla komputerów Mac może służyć do tworzenia aplikacji i tworzenia zestawów podczas opracowywania projektu. Ważne jest, aby skompilować i skompilować kod wcześnie i często, dzięki czemu można zidentyfikować niezgodności typów i inne błędy w czasie kompilacji.

## <a name="building-from-the-ide"></a>Kompilacja z IDE

Za pomocą programu Visual Studio dla komputerów Mac pozwala tworzyć i uruchamiać kompilacje natychmiast, a jednocześnie daje kontrolę nad funkcjami kompilacji. Visual Studio dla komputerów Mac używa MSBuild jako podstawowy system kompilacji.

Wszystkie projekty i rozwiązania utworzone w IDE będzie miał domyślną konfigurację kompilacji, które definiują kontekst dla kompilacji. Te konfiguracje mogą być edytowane lub można utworzyć własne. Tworzenie lub modyfikowanie tych konfiguracji spowoduje automatyczną aktualizację pliku projektu, który jest następnie używany przez FIRMĘ MSBuild do tworzenia projektu.

Aby uzyskać więcej informacji na temat tworzenia projektów i rozwiązań w IDE, zobacz [budynku i czyszczenia projektów i rozwiązań](building-and-cleaning-projects-and-solutions.md) przewodnik.

Visual Studio dla komputerów Mac może również służyć do wykonywania następujących czynności:

* Zmień ścieżkę wyjściową. Jest to edytowane w opcjach programu Project:

    ![Zmienianie ścieżki wyjściowej](media/compiling-and-building-image4.png)

* Zmień szczegółowość danych wyjściowych kompilacji:

    ![Zmiana szczegółowości kompilacji](media/compiling-and-building-image5.png)

* Dodawanie poleceń niestandardowych przed, w trakcie lub po zakończeniu tworzenia lub czyszczenia:

    ![dodawanie poleceń niestandardowych](media/compiling-and-building-image6.png)

## <a name="building-from-command-line"></a>Tworzenie z wiersza polecenia

Aparat kompilacji MSBuild służy do tworzenia aplikacji za pośrednictwem wiersza polecenia.

Zobacz zawartość [MSBuild, aby](/visualstudio/msbuild/msbuild) uzyskać więcej informacji na temat korzystania z usługi MSBuild.

## <a name="building-from-azure-pipelines"></a>Tworzenie z potoków platformy Azure

* [Tworzenie aplikacji platformy Xamarin](/vsts/pipelines/apps/mobile/xamarin?view=vsts&tabs=vsts)
* [Ciągła integracja z xamarinem](https://developer.xamarin.com/guides/cross-platform/ci/)

## <a name="see-also"></a>Zobacz też

- [Kompilowanie i tworzenie (Visual Studio w systemie Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)