---
title: Opcje ustawień projektu C++
description: Dowiedz się, jak używać strony ustawień projektu VC + + w sekcji projekty i rozwiązania, aby definiować ustawienia kompilacji i projektu C++ dotyczące rejestrowania, wydajności i typów plików pomocniczych.
ms.custom: SEO-VS-2020
ms.date: 08/02/2017
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
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 16226cd66c2cf46d1dc46f1cb3f90dc3bad9658c
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616281"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>Ustawienia projektu VC++, projekty i rozwiązania, opcje — Okno dialogowe

To okno dialogowe umożliwia zdefiniowanie ustawień kompilacji i projektu języka C++ związanych z rejestrowaniem, wydajnością i typami plików pomocniczych.

## <a name="to-access-this-dialog-box"></a>Aby uzyskać dostęp do tego okna dialogowego

1. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).

2. Wybierz **projekty i rozwiązania**, a następnie wybierz pozycję **Ustawienia projektu VC + +**.

## <a name="build-logging"></a>Rejestrowanie kompilacji

 **Tak**

  Włącza generowanie pliku dziennika kompilacji. Ta opcja generuje BuildLog.htm, które znajdują się w katalogu pośrednich plików projektu. Każda nowa kompilacja zastępuje poprzedni plik BuildLog.htm.

 **Nie**

  Wyłącza generowanie pliku dziennika kompilacji.

## <a name="show-environment-in-log"></a>Pokaż środowisko w dzienniku

 **Tak**

Wyświetla listę zmiennych środowiskowych w pliku dziennika kompilacji. Ta opcja określa, że wszystkie zmienne środowiskowe są wyświetlane podczas kompilacji projektów C++ w pliku dziennika kompilacji.

 **Nie**

Wyklucz zmienne środowiskowe z pliku dziennika kompilacji.

## <a name="build-timing"></a>Czas kompilacji

 **Tak**

  Włącza czas kompilacji. W przypadku wybrania tej operacji w oknie danych wyjściowych zostanie opublikowany czas potrzebny na zakończenie kompilacji. Aby uzyskać więcej informacji, zobacz [okno dane wyjściowe](../../ide/reference/output-window.md).

 **Nie**

Wyłącza czas kompilacji.

## <a name="maximum-concurrent-c-compilations"></a>Maksymalna liczba współbieżnych kompilacji języka C++

Określa maksymalną liczbę rdzeni procesora CPU, które mają być używane do równoległej kompilacji w języku C++.

## <a name="extensions-to-include"></a>Rozszerzenia do uwzględnienia

Określa rozszerzenia nazw plików, które można przenieść do projektu.

## <a name="extensions-to-hide"></a>Rozszerzenia do ukrycia

Określa rozszerzenia nazw plików, które nie będą wyświetlane w **Eksplorator rozwiązań** po włączeniu **wyświetlania wszystkich plików** .

## <a name="build-customization-search-path"></a>Ścieżka wyszukiwania dostosowywania kompilacji

Określa listę katalogów zawierających pliki reguł, które ułatwiają definiowanie reguł kompilacji dla projektów.

## <a name="solution-explorer-mode"></a>Tryb Eksplorator rozwiązań

**Pokaż tylko pliki w projekcie**

Konfiguruje **Eksplorator rozwiązań** tylko do wyświetlania plików w projekcie.

**Pokaż wszystkie pliki**

Konfiguruje **Eksplorator rozwiązań** do wyświetlania plików w projekcie i plikach na dysku w folderze projektu.

## <a name="enable-project-caching"></a>Włącz buforowanie projektu

**Tak**

Umożliwia programowi Visual Studio buforowanie danych projektu w taki sposób, aby po otwarciu projektu w następnym momencie można było załadować te dane w pamięci podręcznej, a nie ponownie obliczać je na podstawie plików projektu. Użycie danych w pamięci podręcznej może znacznie skrócić czas ładowania projektu.

**Nie**

Nie używaj danych projektu w pamięci podręcznej. Analizuj pliki projektu za każdym razem, gdy projekt jest ładowany.

## <a name="see-also"></a>Zobacz także

- [Kompilowanie programów C/C++](/cpp/build/projects-and-build-systems-cpp)
- [Odwołanie kompilacji C/C++](/cpp/build/reference/c-cpp-building-reference)