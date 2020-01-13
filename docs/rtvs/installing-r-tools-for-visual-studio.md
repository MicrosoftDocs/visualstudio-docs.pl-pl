---
title: Instalowanie narzędzi R Tools
description: Jak zainstalować narzędzia R Tools w programie Visual Studio 2017 i Visual Studio 2015, w tym w przypadku instalacji w trybie offline.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
monikerRange: vs-2017
ms.openlocfilehash: 5a09b3f78b929fd60764be36f56c0b580c7a42d7
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75843733"
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>Jak zainstalować R Tools for Visual Studio

W tym artykule:

- [Obsługiwane wersje programu Visual Studio](#supported-versions-of-visual-studio)
- [Zainstaluj RTVS w programie Visual Studio 2017](#install-rtvs-in-visual-studio-2017)
- [Zainstaluj RTVS w programie Visual Studio 2015](#install-rtvs-in-visual-studio-2015)
- [Instalacja w trybie offline](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> Po zainstalowaniu narzędzi języka R można skonfigurować program Visual Studio pod kątem zoptymalizowanego układu Analityka danych, zgodnie z opisem w artykule [Opcje](options-for-r-tools-in-visual-studio.md) .

## <a name="supported-versions-of-visual-studio"></a>Obsługiwane wersje programu Visual Studio

Program R Tools for Visual Studio (RTVS) jest obsługiwany w systemie Windows z wersjami społecznościowymi programu [Visual studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) i [Visual Studio 2015 Update 3 (lub nowszym](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) ).

RTVS nie jest obecnie obsługiwana w Visual Studio dla komputerów Mac.

RTVS nie jest instalowana, jeśli masz tylko powłokę programu Visual Studio, która jest dołączona do produktów, takich jak Visual Studio Test Professional i SQL Server Management Studio. Powłoka programu Visual Studio nie ma niezbędnych składników do RTVS.

## <a name="install-rtvs-in-visual-studio-2017"></a>Zainstaluj RTVS w programie Visual Studio 2017

1. Uruchom Instalatora programu Visual Studio i wybierz opcję **Modify** (Aby uzyskać szczegółowe informacje, zobacz [modyfikowanie programu Visual Studio](../install/modify-visual-studio.md)). Jeśli nie masz jeszcze zainstalowanego programu Visual Studio, zobacz [Instalowanie programu Visual Studio](../install/install-visual-studio.md). W systemie Windows 7 upewnij się, że Instalator został zaktualizowany, aby pokazać program Visual Studio 2017 w wersji *15,2 kompilacji 26430,12* lub nowszej.

1. Wybierz obciążenie **aplikacji** do analizy i przetwarzania danych:

    ![Obciążenie aplikacji do analizy i przetwarzania danych w program VS2017](media/installation-data-science-workload.png)

1. Ustaw opcje dodatkowe po prawej stronie pod tą samą nazwą obciążenia. Domyślnie to obciążenie obejmuje F# obsługę języka Python. W przypadku języka R wymagania minimalne są **obsługiwane w języku r**, **Obsługa środowiska uruchomieniowego w środowisku r**i **program Microsoft R Client**.

RTVS jest zainstalowany w: *% ProgramFiles (x86)% \ Microsoft Visual Studio\<wersja >\<edition > Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio, w* której *\<wersja >* jest zazwyczaj `2017` i\<*edition >* jest `Community`, `Professional`lub `Enterprise`.

## <a name="install-rtvs-in-visual-studio-2015"></a>Zainstaluj RTVS w programie Visual Studio 2015

W programie Visual Studio 2015 należy zainstalować interpreter języka R i osobno narzędzia języka R.

### <a name="install-an-r-interpreter"></a>Instalowanie interpretera języka R

RTVS wymaga instalacji 64-bitowej języka R w wersji 3.2.1 lub nowszej z co najmniej jednego z następujących źródeł:

- [Microsoft R Open](https://mran.microsoft.com/download/)
- [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [CRAN R](https://cran.r-project.org/bin/windows/base/)

Programy Microsoft R Open i CRAN R umożliwiają stosowanie wielu równoległych wersji. Program Microsoft R Client jednak obsługuje tylko jedną wersję i zawsze używa najnowszej zainstalowanej wersji.

### <a name="install-the-r-tools"></a>Instalowanie narzędzi R Tools

Pobierz bieżące RTVS dla programu Visual Studio 2015 z [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe). RTVS sprawdza dostępność odpowiedniej wersji programu Visual Studio i pomaga zainstalować interpreter języka R, jeśli jeszcze tego nie zrobiono.

> [!Note]
> Autonomiczny Instalator RTVS działa tylko z programem Visual Studio 2015; w programie Visual Studio 2017 zainstaluj obsługę języka R za pomocą [obciążenia aplikacji analizy i przetwarzania danych](#install-rtvs-in-visual-studio-2017) zgodnie z wcześniejszym opisem.

RTVS dla programu Visual Studio 2015 jest zainstalowany w programie: `%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Instalacja w trybie offline programów Visual Studio i RTVS

Instalacja w trybie offline jest odpowiednia dla komputerów, które nie są połączone z Internetem:

1. Przejdź do obszaru [Tworzenie instalacji w trybie offline programu Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md).

1. Jeśli używasz programu Visual Studio 2015, wybierz pozycję **2015** w selektorze powyżej spisu treści.

1. Postępuj zgodnie z instrukcjami dotyczącymi tworzenia instalacji w trybie offline na stronie sieci Web.

1. W przypadku programu Visual Studio 2015 Pobierz Instalatory RTVS w trybie offline z [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip) i [https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip).

1. Zainstaluj program Visual Studio i RTVS z instalatorów trybu offline.

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do języka R](getting-started-with-r.md)
- [Przykładowe projekty narzędzi R Tools](getting-started-samples.md)
- [Pomoc w narzędziach języka R](getting-started-help.md)
- [Opcje narzędzi języka R](options-for-r-tools-in-visual-studio.md)
- [Microsoft Machine Learning Server (dawniej R Server)](/machine-learning-server/)
