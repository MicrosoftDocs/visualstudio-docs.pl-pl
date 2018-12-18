---
title: Instalowanie narzędzi języka R
description: Jak zainstalować narzędzia języka R w programie Visual Studio 2017 i Visual Studio 2015, łącznie z instalacji w trybie offline.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 4fdf7cb791339350ff9644d0f727e3adc299add6
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220908"
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>Jak zainstalować narzędzia języka R dla programu Visual Studio

W tym artykule:

- [Obsługiwane wersje programu Visual Studio](#supported-versions-of-visual-studio)
- [Zainstaluj RTVS w programie Visual Studio 2017](#installing-rtvs-in-visual-studio-2017)
- [Zainstaluj RTVS w programie Visual Studio 2015](#installing-rtvs-in-visual-studio-2015)
- [Instalacja w trybie offline](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> Po zainstalowaniu narzędzia języka R może chcesz skonfigurować Visual Studio układu naukowego przetwarzania danych zoptymalizowanych zgodnie z opisem na [opcje](options-for-r-tools-in-visual-studio.md) artykułu.

## <a name="supported-versions-of-visual-studio"></a>Obsługiwane wersje programu Visual Studio

Narzędzia R Tools for Visual Studio (RTVS) jest obsługiwana na Windows ze społecznością (wersja bezpłatna), Professional i w wersji Enterprise zarówno [programu Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) i [Visual Studio 2015 Update 3 (lub nowszej)](http://go.microsoft.com/fwlink/?LinkId=691129) (bezpośredni Pobierz).

RTVS nie jest obecnie obsługiwany w programie Visual Studio dla komputerów Mac.

Nie można zainstalować RTVS, jeśli masz tylko program Visual Studio Shell znajdującej się produkty takie jak Visual Studio Test Professional oraz programu SQL Server Management Studio. Visual Studio Shell nie posiada niezbędnych składników dla RTVS.

## <a name="install-rtvs-in-visual-studio-2017"></a>Zainstaluj RTVS w programie Visual Studio 2017

1. Uruchom Instalatora programu Visual Studio, a następnie wybierz **Modyfikuj** opcji (Aby uzyskać więcej informacji, zobacz [modyfikowanie programu Visual Studio](../install/modify-visual-studio.md)). Jeśli nie masz jeszcze zainstalowanego programu Visual Studio, zobacz [Zainstaluj program Visual Studio](../install/install-visual-studio.md). Windows 7, upewnij się, że Instalatora jest aktualizowana w celu wyświetlenia wersji programu Visual Studio 2017 *15.2 kompilacji 26430.12* lub nowszej.

1. Wybierz **aplikacji analitycznych i naukowych opracowań danych** obciążenia:

    ![Obciążenie dla aplikacji analitycznych w programie VS2017 i nauki o danych](media/installation-data-science-workload.png)

1. Ustaw dodatkowe opcje po prawej stronie w obszarze tej samej nazwie obciążenia. Domyślnie ten pakiet roboczy zawiera F# i obsługi języka Python. W przypadku języka R są minimalne wymagania **obsługę języka R**, **obsługę środowiska uruchomieniowego dla Programowanie w języku R**, i **Microsoft R client**.

RTVS jest zainstalowany w: *% ProgramFiles (x86) %\Microsoft Visual Studio\<wersji >\<edition > Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio* gdzie  *\<wersji >* jest zazwyczaj `2017` i  *\<edition >* jest `Community`, `Professional`, lub `Enterprise`.

## <a name="install-rtvs-in-visual-studio-2015"></a>Zainstaluj RTVS w programie Visual Studio 2015

Za pomocą programu Visual Studio 2015 należy oddzielnie zainstalować interpreter języka R i narzędzia języka R.

### <a name="install-an-r-interpreter"></a>Instalowanie interpretera języka R

RTVS wymaga 64-bitowej instalacji języka r, wersja 3.2.1 lub nowszy z co najmniej jeden z następujących źródeł:

- [Microsoft R Open](https://mran.microsoft.com/download/)
- [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [CRAN JĘZYKA R](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open i CRAN r. zarówno umożliwiają wielu wersji obok siebie. Microsoft R Client, jednak obsługuje tylko jedną wersję i zawsze używa najnowszego, który został zainstalowany.

### <a name="install-the-r-tools"></a>Zainstaluj narzędzia języka R

Pobieranie bieżącego RTVS dla programu Visual Studio 2015 z [ https://aka.ms/rtvs-current ](https://aka.ms/rtvs-current). RTVS sprawdza, czy odpowiednia wersja programu Visual Studio i pomaga zainstalować interpreter języka R, jeśli jeszcze go.

> [!Note]
> Autonomiczny Instalator RTVS działa tylko w przypadku programu Visual Studio 2015; za pomocą programu Visual Studio 2017, należy zainstalować obsługę języka R za pośrednictwem [obciążenie aplikacji analitycznych i naukowych opracowań danych](#installing-rtvs-in-visual-studio-2017) zgodnie z wcześniejszym opisem.

Rozszerzenie RTVS dla programu Visual Studio 2015 jest instalowany w: `%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Instalacja w trybie offline programu Visual Studio i RTVS

Instalacja w trybie offline jest odpowiednia dla komputerów, które nie są połączone z Internetem:

1. Przejdź do [Tworzenie instalacji offline programu Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md).

1. Jeśli używasz programu Visual Studio 2015, wybierz **2015** w selektorze powyżej spisu treści.

1. Postępuj zgodnie z instrukcjami dotyczącymi tworzenia instalacji w trybie offline na stronie sieci web.

1. Dla programu Visual Studio 2015, Pobierz instalatory RTVS w trybie offline z [ https://aka.ms/rtvs-current-zip ](https://aka.ms/rtvs-current-zip) i [ https://aka.ms/rtvs-remote-zip ](https://aka.ms/rtvs-remote-zip).

1. Zainstaluj program Visual Studio i RTVS z instalatory w trybie offline.

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do języka R](getting-started-with-r.md)
- [Narzędzia języka R przykładowych projektów](getting-started-samples.md)
- [Pomoc przy określaniu narzędzia języka R](getting-started-help.md)
- [Opcje narzędzia języka R](options-for-r-tools-in-visual-studio.md)
- [Serwer Microsoft Machine Learning (dawniej program R Server)](/machine-learning-server/)