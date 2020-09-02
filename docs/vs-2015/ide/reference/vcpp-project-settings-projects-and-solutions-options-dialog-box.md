---
title: Ustawienia projektu VC + +, projekty i rozwiązania, okno dialogowe Opcje | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ef861d13387c013659e5e4c1714680b71896858c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657866"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>Ustawienia projektu VC++, projekty i rozwiązania, opcje — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

To okno dialogowe umożliwia definiowanie [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] ustawień projektu związanych z rejestrowaniem i typami plików pomocniczych.

### <a name="to-access-this-dialog-box"></a>Aby uzyskać dostęp do tego okna dialogowego

1. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).

2. Wybierz **projekty i rozwiązania**, a następnie wybierz pozycję **Ustawienia projektu VC + +**.

## <a name="build-customization-search-path"></a>Ścieżka wyszukiwania dostosowywania kompilacji
 Określa listę katalogów zawierających pliki reguł, które ułatwiają definiowanie reguł kompilacji dla projektów.

## <a name="build-logging"></a>Rejestrowanie kompilacji
 **Tak** Włącza generowanie pliku dziennika kompilacji. Ta opcja generuje BuildLog.htm, które znajdują się w katalogu pośrednich plików projektu. Każda nowa kompilacja zastępuje poprzedni plik BuildLog.htm.

 **Nie** Wyłącza generowanie pliku dziennika kompilacji.

## <a name="build-timing"></a>Czas kompilacji
 **Tak** Włącza czas kompilacji. W przypadku wybrania tej operacji w oknie danych wyjściowych zostanie opublikowany czas potrzebny na zakończenie kompilacji. Aby uzyskać więcej informacji, zobacz [okno dane wyjściowe](../../ide/reference/output-window.md).

 **Nie** Wyłącza czas kompilacji.

## <a name="extensions-to-hide"></a>Rozszerzenia do ukrycia
 Określa rozszerzenia nazw plików, które nie będą wyświetlane w **Eksplorator rozwiązań** po włączeniu **wyświetlania wszystkich plików** .

## <a name="extensions-to-include"></a>Rozszerzenia do uwzględnienia
 Określa rozszerzenia nazw plików, które można przenieść do projektu.

## <a name="maximum-concurrent-c-compilations"></a>Maksymalna liczba współbieżnych kompilacji języka C++
 Określa maksymalną liczbę rdzeni procesora CPU, które mają być używane do równoległej kompilacji w języku C++.

## <a name="show-environment-in-log"></a>Pokaż środowisko w dzienniku
 **Tak** Wyświetla listę zmiennych środowiskowych w pliku dziennika kompilacji. Ta opcja określa, że wszystkie zmienne środowiskowe podczas kompilacji [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projektów są wyświetlane w pliku dziennika kompilacji.

 **Nie** Wyklucz zmienne środowiskowe z pliku dziennika kompilacji.

## <a name="solution-explorer-mode"></a>Tryb Eksplorator rozwiązań
 **Pokaż tylko pliki w projekcie** Konfiguruje **Eksplorator rozwiązań** tylko do wyświetlania plików w projekcie.

 **Pokaż wszystkie pliki** Konfiguruje **Eksplorator rozwiązań** do wyświetlania plików w projekcie i plikach na dysku w folderze projektu.

## <a name="see-also"></a>Zobacz też
 [Kompilowanie programu c/c++](https://msdn.microsoft.com/library/fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008) — [Dokumentacja konstrukcyjna c/c++](https://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d)
