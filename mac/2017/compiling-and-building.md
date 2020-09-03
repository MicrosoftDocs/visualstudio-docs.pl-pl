---
title: Kompilowanie i tworzenie
description: W tym artykule opisano sposób kompilowania i kompilowania projektów oraz rozwiązań w Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.topic: overview
ms.openlocfilehash: 532a245b8e217ea278bf5a3424a194ce87ae43f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85950048"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Kompilowanie i kompilowanie w Visual Studio dla komputerów Mac

Visual Studio dla komputerów Mac może służyć do kompilowania aplikacji i tworzenia zestawów podczas opracowywania projektu. Ważne jest, aby kompilować i kompilować swój kod wczesnie i często, aby można było identyfikować niezgodności typów i inne błędy czasu kompilacji.

## <a name="building-from-the-ide"></a>Kompilacja z IDE

Za pomocą Visual Studio dla komputerów Mac można szybko tworzyć i uruchamiać kompilacje, jednocześnie zapewniając kontrolę nad funkcjami kompilacji. Visual Studio dla komputerów Mac używa programu MSBuild jako bazowego systemu kompilacji.

Wszystkie projekty i rozwiązania utworzone w środowisku IDE będą miały domyślną konfigurację kompilacji, która definiuje kontekst dla kompilacji. Te konfiguracje można edytować lub można utworzyć własne. Utworzenie lub zmodyfikowanie tych konfiguracji spowoduje automatyczne zaktualizowanie pliku projektu, który następnie jest używany przez program MSBuild do kompilowania projektu.

Aby uzyskać więcej informacji na temat sposobu kompilowania projektów i rozwiązań w środowisku IDE, zobacz Przewodnik [tworzenia i czyszczenia projektów i rozwiązań](building-and-cleaning-projects-and-solutions.md) .

Visual Studio dla komputerów Mac można również użyć do wykonania następujących czynności:

* Zmień ścieżkę wyjściową. Jest to edytowane w opcjach projektu:

    ![Zmień ścieżkę wyjściową](media/compiling-and-building-image4.png)

* Zmień poziom szczegółowości danych wyjściowych kompilacji:

    ![Zmień szczegółowość kompilacji](media/compiling-and-building-image5.png)

* Dodaj niestandardowe polecenia przed, w trakcie lub po skompilowaniu lub oczyszczeniu:

    ![Dodawanie poleceń niestandardowych](media/compiling-and-building-image6.png)

## <a name="building-from-command-line"></a>Kompilowanie z wiersza polecenia

Możesz użyć aparatu kompilacji MSBuild do kompilowania aplikacji za pomocą wiersza polecenia.

Aby uzyskać więcej informacji na temat korzystania z programu MSBuild, zobacz zawartość programu [MSBuild](/visualstudio/msbuild/msbuild) .

## <a name="building-from-azure-pipelines"></a>Kompilowanie z Azure Pipelines

* [Kompilowanie aplikacji platformy Xamarin](/vsts/pipelines/apps/mobile/xamarin?view=vsts&tabs=vsts)
* [Ciągła integracja z platformą Xamarin](https://developer.xamarin.com/guides/cross-platform/ci/)

## <a name="see-also"></a>Zobacz też

- [Kompiluj i Kompiluj (Visual Studio w systemie Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)