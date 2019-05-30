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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 186db68e9b69b98a9fe9d9a2a8c8941302304cb2
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263090"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>Ustawienia projektu VC++, projekty i rozwiązania, opcje — Okno dialogowe
To okno dialogowe pozwala zdefiniować [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] kompilacji i ustawienia związane z rejestrowania, wydajności i obsługi typów plików projektu.

### <a name="to-access-this-dialog-box"></a>Dostęp do tego okna dialogowego

1. Na **narzędzia** menu, kliknij przycisk **opcje**.

2. Wybierz **projekty i rozwiązania**, a następnie wybierz pozycję **ustawienia projektu VC ++**.

## <a name="build-logging"></a>Rejestrowanie kompilacji
 **Tak**

  Włącza generowanie pliku dziennika kompilacji. Ta opcja powoduje wygenerowanie nazwę BuildLog.htm, które znajdują się w katalogu pośrednie pliki projektu. Każdej nowej kompilacji zastępuje poprzedni plik nazwę BuildLog.htm.

 **Brak**

  Wyłącza generowanie pliku dziennika kompilacji.

## <a name="show-environment-in-log"></a>Pokaż środowisko w rejestrze
 **Tak**

 Wyświetla listę zmiennych środowiskowych w pliku dziennika kompilacji. Ta opcja określa, aby wyświetlić wszystkich systemowych zmiennych środowiskowych, podczas kompilacji z [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektów do kompilacji pliku dziennika.

 **Brak**

 Wyklucz zmienne środowiskowe z pliku dziennika kompilacji.

## <a name="build-timing"></a>Czas kompilacji
 **Tak**

  Włącza międzyczasy kompilacji. Jeśli zaznaczone, czas potrzebny na zakończenie kompilacji jest publikowany w oknie danych wyjściowych. Aby uzyskać więcej informacji, zobacz [okno danych wyjściowych](../../ide/reference/output-window.md).

 **Brak**

 Wyłącza międzyczasy kompilacji.

## <a name="maximum-concurrent-c-compilations"></a>Maksymalna współbieżnych kompilacji języka C++
  Określa maksymalną liczbę rdzeni Procesora używanych w równoległej kompilacji języka C++.

## <a name="extensions-to-include"></a>Rozszerzenia do uwzględnienia
  Określa rozszerzenia nazw plików, które mogą być przenoszone do projektu.

## <a name="extensions-to-hide"></a>Ukryte rozszerzenia
  Określa rozszerzenia nazw plików, które nie będą wyświetlane w **Eksploratora rozwiązań** podczas **Pokaż wszystkie pliki** jest włączona.

## <a name="build-customization-search-path"></a>Ścieżka wyszukiwania dostosowania kompilacji
  Określa listę katalogów, które zawierają pliki Rules, które ułatwiają definiowanie reguł kompilacji dla Twoich projektów.

## <a name="solution-explorer-mode"></a>Tryb Eksploratora rozwiązań
 **Pokaż tylko pliki w projekcie**

  Konfiguruje **Eksploratora rozwiązań** Aby wyświetlić tylko pliki w projekcie.

 **Pokaż wszystkie pliki**

  Konfiguruje **Eksploratora rozwiązań** Aby wyświetlić pliki w projekcie i pliki na dysku w folderze projektu.

## <a name="enable-project-caching"></a>Włącz buforowanie projektu
**Tak**

Umożliwia środowisku Visual Studio do buforowania danych projektu tak, aby przy następnym otwarciu projektu go załadować tych buforowanych danych, zamiast ponownego przetwarzania danych z plików projektu. Przy użyciu danych z pamięci podręcznej można przyspieszyć czas ładowania projektu znacznie.

**Brak**

Nie należy używać danych z pamięci podręcznej programu project. Analizowanie plików projektu, projekt ładuje się każdorazowo.

## <a name="see-also"></a>Zobacz także

- [Kompilowanie programów C/C++](/cpp/build/projects-and-build-systems-cpp)
- [Dokumentacja kompilacji w języku C/C++](/cpp/build/reference/c-cpp-building-reference)
