---
title: Instalowanie narzędzi R
description: Jak zainstalować narzędzia języka R w programie Visual Studio 2017 i visual studio 2015, w tym instalacje w trybie offline.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
monikerRange: vs-2017
ms.openlocfilehash: 5a09b3f78b929fd60764be36f56c0b580c7a42d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75843733"
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>Jak zainstalować narzędzia języka R dla programu Visual Studio

W tym artykule:

- [Obsługiwane wersje programu Visual Studio](#supported-versions-of-visual-studio)
- [Instalowanie rtvs w programie Visual Studio 2017](#install-rtvs-in-visual-studio-2017)
- [Instalowanie rtvs w programie Visual Studio 2015](#install-rtvs-in-visual-studio-2015)
- [Instalacja w trybie offline](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> Po zainstalowaniu narzędzi R, można skonfigurować visual studio dla zoptymalizowanego układu data scientist, zgodnie z opisem w [artykule Opcje.](options-for-r-tools-in-visual-studio.md)

## <a name="supported-versions-of-visual-studio"></a>Obsługiwane wersje programu Visual Studio

Narzędzia R Tools for Visual Studio (RTVS) są obsługiwane w systemie Windows w wersjach Community (bezpłatne), Professional i Enterprise zarówno [w programach Visual Studio 2017,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) jak i [w programie Visual Studio 2015 Update 3 (lub nowszym)](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) (pobieranie bezpośrednie).

RTVS nie jest obecnie obsługiwany w programie Visual Studio dla komputerów Mac.

RTVS nie jest instalowany, jeśli masz tylko powłoki programu Visual Studio, który jest dołączony do produktów, takich jak Visual Studio Test Professional i SQL Server Management Studio. Powłoka programu Visual Studio nie ma niezbędnych składników dla RTVS.

## <a name="install-rtvs-in-visual-studio-2017"></a>Instalowanie rtvs w programie Visual Studio 2017

1. Uruchom instalator programu Visual Studio i wybierz opcję **Modyfikuj** (aby uzyskać szczegółowe informacje, zobacz [Modyfikowanie programu Visual Studio](../install/modify-visual-studio.md)). Jeśli nie masz jeszcze zainstalowanego programu Visual Studio, zobacz [Instalowanie programu Visual Studio](../install/install-visual-studio.md). W systemie Windows 7 upewnij się, że instalator jest aktualizowany w celu wyświetlenia kompilacji programu Visual Studio 2017 w wersji *15.2 26430.12* lub nowszej.

1. Wybierz obciążenie **do nauki o danych i aplikacji analitycznych:**

    ![Obciążenie aplikacji do nauki o danych i aplikacji analitycznych w programie VS2017](media/installation-data-science-workload.png)

1. Ustaw dodatkowe opcje po prawej stronie pod tą samą nazwą obciążenia. Domyślnie to obciążenie obejmuje obsługę języka F# i Python. W przypadku języka R minimalne wymagania to **obsługa języka języka R,** **obsługa środowiska wykonawczego dla programowania języka R**i klient **Microsoft R**.

RTVS jest zainstalowany w: *%ProgramFiles(x86)%\Microsoft Visual\< \<Studio version>edition>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio* gdzie `Community` `Professional` `Enterprise` `2017` * \<zazwyczaj* jest>wersji i * \<>w wersji* jest , lub .

## <a name="install-rtvs-in-visual-studio-2015"></a>Instalowanie rtvs w programie Visual Studio 2015

W programie Visual Studio 2015 należy osobno zainstalować interpreter języka R i narzędzia języka R.

### <a name="install-an-r-interpreter"></a>Instalowanie interpretera R

RTVS wymaga 64-bitowej instalacji r w wersji 3.2.1 lub nowszej z jednego lub więcej z następujących źródeł:

- [Microsoft R Open](https://mran.microsoft.com/download/)
- [Klient microsoft r](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [CRAN R](https://cran.r-project.org/bin/windows/base/)

Zarówno Microsoft R Open, jak i CRAN R umożliwiają korzystanie z wielu wersji side-by-side. Microsoft R Client obsługuje jednak tylko jedną wersję i zawsze używa najnowszej zainstalowanej.

### <a name="install-the-r-tools"></a>Instalowanie narzędzi R

Pobierz bieżący RTVS dla programu Visual [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe)Studio 2015 z . RTVS sprawdza odpowiednią wersję programu Visual Studio i pomaga zainstalować interpreter języka R, jeśli jeszcze tego nie zrobiłeś.

> [!Note]
> Autonomiczny instalator RTVS działa tylko z programem Visual Studio 2015; z programem Visual Studio 2017 zainstaluj obsługę języka R za pomocą [obciążenia data science and analytical applications,](#install-rtvs-in-visual-studio-2017) jak opisano wcześniej.

RTVS dla programu Visual Studio 2015 jest zainstalowany w:`%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Instalacja w trybie offline programów Visual Studio i RTVS

Instalacja w trybie offline jest odpowiednia dla komputerów, które nie są połączone z Internetem:

1. Przejdź do [tworzenia instalacji w trybie offline programu Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md).

1. Jeśli używasz programu Visual Studio 2015, wybierz **2015** w selektorze powyżej spisu treści.

1. Postępuj zgodnie z instrukcjami dotyczącymi tworzenia instalacji w trybie offline na stronie internetowej.

1. W programie Visual Studio 2015 pobierz instalatory RTVS w trybie offline z [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip) programu I . [https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip)

1. Zainstaluj program Visual Studio i RTVS z instalatorów w trybie offline.

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do R](getting-started-with-r.md)
- [R Narzędzia przykładowe projekty](getting-started-samples.md)
- [Pomoc w narzędziach R](getting-started-help.md)
- [Opcje narzędzi R](options-for-r-tools-in-visual-studio.md)
- [Microsoft Machine Learning Server (dawniej R Server)](/machine-learning-server/)
