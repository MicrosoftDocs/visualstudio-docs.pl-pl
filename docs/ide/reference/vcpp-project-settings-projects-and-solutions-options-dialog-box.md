---
title: C++Opcje ustawień projektu
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
ms.openlocfilehash: c7acd0d8f9c6d15f9f20c42f59c3bd5562884ac3
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918882"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>Ustawienia projektu VC++, projekty i rozwiązania, opcje — Okno dialogowe

To okno dialogowe umożliwia definiowanie C++ ustawień kompilacji i projektu związanych z rejestrowaniem, wydajnością i typami plików pomocniczych.

## <a name="to-access-this-dialog-box"></a>Aby uzyskać dostęp do tego okna dialogowego

1. Na **narzędzia** menu, kliknij przycisk **opcje**.

2. Wybierz **projekty i rozwiązania**, a następnie wybierz pozycję **Ustawienia projektu VC + +** .

## <a name="build-logging"></a>Rejestrowanie kompilacji

 **Tak**

  Włącza generowanie pliku dziennika kompilacji. Ta opcja generuje BuildLog. htm, który można znaleźć w katalogu plików pośrednich projektu. Każda nowa kompilacja zastępuje poprzedni plik BuildLog. htm.

 **Znaleziono**

  Wyłącza generowanie pliku dziennika kompilacji.

## <a name="show-environment-in-log"></a>Pokaż środowisko w dzienniku

 **Tak**

Wyświetla listę zmiennych środowiskowych w pliku dziennika kompilacji. Ta opcja określa, że wszystkie zmienne środowiskowe podczas kompilacji C++ projektów są wyświetlane w pliku dziennika kompilacji.

 **Znaleziono**

Wyklucz zmienne środowiskowe z pliku dziennika kompilacji.

## <a name="build-timing"></a>Czas kompilacji

 **Tak**

  Włącza czas kompilacji. W przypadku wybrania tej operacji w oknie danych wyjściowych zostanie opublikowany czas potrzebny na zakończenie kompilacji. Aby uzyskać więcej informacji, zobacz [okno dane wyjściowe](../../ide/reference/output-window.md).

 **Znaleziono**

Wyłącza czas kompilacji.

## <a name="maximum-concurrent-c-compilations"></a>Maksymalna liczba C++ współbieżnych kompilacji

Określa maksymalną liczbę rdzeni procesora CPU do użycia na potrzeby kompilacji C++ równoległej.

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

**Znaleziono**

Nie używaj danych projektu w pamięci podręcznej. Analizuj pliki projektu za każdym razem, gdy projekt jest ładowany.

## <a name="see-also"></a>Zobacz także

- [Kompilowanie programów C/C++](/cpp/build/projects-and-build-systems-cpp)
- [Dokumentacja kompilacji w języku C/C++](/cpp/build/reference/c-cpp-building-reference)