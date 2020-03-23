---
title: Opcje ustawień projektu języka C++
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "68918882"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>Ustawienia projektu VC++, projekty i rozwiązania, opcje — Okno dialogowe

To okno dialogowe umożliwia definiowanie ustawień kompilacji i projektu języka C++ związanych z rejestrowaniem, wydajnością i obsługiwanymi typami plików.

## <a name="to-access-this-dialog-box"></a>Aby uzyskać dostęp do tego okna dialogowego

1. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).

2. Wybierz **pozycję Projekty i rozwiązania**, a następnie wybierz pozycję Ustawienia projektu **VC++**.

## <a name="build-logging"></a>Tworzenie rejestrowania

 **Tak**

  Włącza generowanie pliku dziennika kompilacji. Ta opcja generuje BuildLog.htm, który można znaleźć w katalogu plików pośrednich projektu. Każda świeża kompilacja zastępuje poprzedni plik BuildLog.htm.

 **Nie**

  Wyłącza generowanie pliku dziennika kompilacji.

## <a name="show-environment-in-log"></a>Pokaż środowisko w dzienniku

 **Tak**

Wyświetla listę zmiennych środowiskowych w pliku dziennika kompilacji. Ta opcja określa echo wszystkich zmiennych środowiskowych, podczas kompilacji projektów C++ do pliku dziennika kompilacji.

 **Nie**

Wyklucz zmienne środowiskowe z pliku dziennika kompilacji.

## <a name="build-timing"></a>Czas kompilacji

 **Tak**

  Włącza czas kompilacji. Jeśli ta opcja jest zaznaczona, czas potrzebny na ukończenie kompilacji jest księgowane w oknie Dane wyjściowe. Aby uzyskać więcej informacji, zobacz [Okno wyjściowe](../../ide/reference/output-window.md).

 **Nie**

Wyłącza czas kompilacji.

## <a name="maximum-concurrent-c-compilations"></a>Maksymalna jednoczesna kompilacja języka C++

Określa maksymalną liczbę rdzeni procesora CPU do użycia dla równoległej kompilacji C++.

## <a name="extensions-to-include"></a>Rozszerzenia do uwzględnienia

Określa rozszerzenia nazw plików, które mogą być przenoszone do projektu.

## <a name="extensions-to-hide"></a>Rozszerzenia do ukrycia

Określa rozszerzenia nazw plików, które nie będą wyświetlane w **Eksploratorze rozwiązań** po włączeniu **funkcji Pokaż wszystkie pliki.**

## <a name="build-customization-search-path"></a>Ścieżka wyszukiwania dostosowywania kompilacji

Określa listę katalogów zawierających pliki .rules, które ułatwiają definiowanie reguł kompilacji dla projektów.

## <a name="solution-explorer-mode"></a>Tryb Eksploratora rozwiązań

**Pokaż tylko pliki w projekcie**

Konfiguruje **Eksploratora rozwiązań,** aby wyświetlał tylko pliki w projekcie.

**Pokaż wszystkie pliki**

Konfiguruje **Eksploratora rozwiązań,** aby wyświetlał pliki w projekcie i pliki na dysku w folderze projektu.

## <a name="enable-project-caching"></a>Włącz buforowanie projektu

**Tak**

Umożliwia programowi Visual Studio buforowanie danych projektu, dzięki czemu podczas następnego otwarcia projektu można załadować te dane w pamięci podręcznej, a nie ponownie obliczyć je z plików projektu. Korzystanie z danych w pamięci podręcznej może znacznie przyspieszyć czas ładowania projektu.

**Nie**

Nie należy używać buforowanych danych projektu. Analizuj pliki projektu za każdym razem, gdy projekt się ładuje.

## <a name="see-also"></a>Zobacz też

- [Kompilowanie programów C/C++](/cpp/build/projects-and-build-systems-cpp)
- [Odwołanie kompilacji C/C++](/cpp/build/reference/c-cpp-building-reference)