---
title: Zestaw debugowania i zwalniania konfiguracji | Dokumentacja firmy Microsoft
ms.date: 10/05/2018
ms.topic: reference
f1_keywords:
- vs.debug.builds
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0bf0da5f15bbb59c2898af0dc0bfec1105cbab0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62847657"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Zestaw debugowania i zwalniania konfiguracji w programie Visual Studio

Projektów programu Visual Studio mają oddzielnych wersji i konfiguracji programu do debugowania. Kompilujesz wersję debugera do debugowania i wersję zwolnienia do ostatecznej dystrybucji zwolnienia.

W konfiguracji debugowania programach kompiluje z informacji pełnego symbolicznego debugowania i bez optymalizacji. Optymalizacja komplikuje debugowanie, ponieważ relacja między kodem źródłowym i wygenerowanymi instrukcjami jest bardziej złożona.

Konfiguracja wydania programu ma nie symbolicznej informacji debugowania i jest w pełni zoptymalizowana. Dla kodu zarządzanego i kodu w języku C++, informacje debugowania mogą być generowane w plikach .pdb [w zależności od opcji kompilatora](#BKMK_symbols_release) które są używane. Tworzenie plików .pdb może być przydatne, jeśli później trzeba debugować swoje wersje.

Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [konfiguracje kompilacji omówienie](../ide/understanding-build-configurations.md).

Możesz zmienić konfigurację kompilacji z **kompilacji** menu na pasku narzędzi lub na stronach właściwości projektu. Strony właściwości projektu są specyficzne dla języka. Poniższa procedura pokazuje, jak zmienić konfigurację kompilacji w menu i paska narzędzi. Aby uzyskać więcej informacji o tym, jak zmienić konfigurację kompilacji w projektach w różnych językach, zobacz [Zobacz też](#see-also) poniższej sekcji.

## <a name="change-the-build-configuration"></a>Zmień konfigurację kompilacji

Aby zmienić konfigurację kompilacji, albo:

* Z **kompilacji** menu, wybierz opcję **programu Configuration Manager**, a następnie wybierz **debugowania** lub **wersji**.

lub

* Na pasku narzędzi wybierz **debugowania** lub **wersji** z **konfiguracje rozwiązania** listy.

  ![Konfiguracja kompilacji pasków narzędzi](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="BKMK_symbols_release"></a>Generowanie plików symboli (.pdb) dla kompilacji (C#, C++, Visual Basic F#)

Istnieje możliwość generowania plików symboli (.pdb) i jakie informacje debugowania. Dla większości typów projektów kompilator generuje pliki symboli domyślnie do debugowania i wersji kompilacji, podczas gdy inne ustawienia domyślne różnią się typów projektów i wersji programu Visual Studio.

> [!IMPORTANT]
> Debuger będzie ładował tylko plik .pdb dla pliku wykonywalnego, który dokładnie pasuje do pliku .pdb, który z kolei został utworzony podczas kompilowania pliku wykonywalnego (czyli .pdb musi być plikiem oryginalnym lub kopią oryginalnego pliku .pdb). Aby uzyskać więcej informacji, zobacz [Dlaczego Visual Studio wymaga, aby debuger symbol dokładnej zgodności plików plików binarnych, które zostały skompilowane?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

Każdy typ projektu może mieć inny sposób ustawienia tych opcji.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Generuj pliki symboli dla projektów C#, ASP.NET lub Visual Basic

Aby uzyskać szczegółowe informacje na temat ustawień projektu dla konfiguracji debugowania w języku C# lub Visual Basic, zobacz [ustawienia projektu dla języka C# konfiguracji debugowania](../debugger/project-settings-for-csharp-debug-configurations.md) lub [ustawienia projektu dla języka Visual Basic konfiguracjidebugowania](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. W Eksploratorze rozwiązań wybierz projekt.

2. Wybierz **właściwości** ikonę (lub naciśnij **klawisze Alt + Enter**).

3. W okienku bocznym wybierz **kompilacji** (lub **skompilować** w języku Visual Basic).

4. W **konfiguracji** wybierz **debugowania** lub **wersji**.

5. Wybierz **zaawansowane** przycisk (lub **zaawansowane opcje kompilacji** przycisku w języku Visual Basic).

6. W **informacje o debugowaniu** listy (lub **Generuj informacje debugowania** listy w języku Visual Basic), wybierz **pełne**, **tylko do Pdb**, lub **Przenośne**.

   Przenośne format jest najbardziej aktualną format dla wielu platform .NET Core. Aby uzyskać więcej informacji na temat opcji, zobacz [okno dialogowe Zaawansowane ustawienia kompilacji (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

   ![Generowanie plików PDB dla kompilacji w języku C#](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. Skompilowanie projektu.

   Kompilator tworzy pliki symboli w tym samym folderze co plik wykonywalny lub plik wyjściowy głównego.

### <a name="generate-symbol-files-for-a-c-project"></a>Generuj pliki symboli dla projektu w języku C++

1. W Eksploratorze rozwiązań wybierz projekt.

2. Wybierz **właściwości** ikonę (lub naciśnij **klawisze Alt + Enter**).

3. W **konfiguracji** wybierz **debugowania** lub **wersji**.

4. W okienku bocznym wybierz **konsolidatora > debugowanie**, następnie wybierz opcje **Generuj informacje o debugowaniu**.

   Aby uzyskać szczegółowe informacje na temat ustawień projektu dla konfiguracji debugowania w języku C++, zobacz [ustawienia projektu dla języka C++ konfiguracji debugowania](../debugger/project-settings-for-a-cpp-debug-configuration.md).

5. Skonfiguruj opcje **Generowanie plików bazy danych programu**.

   W większości projektów C++, wartość domyślna to `$(OutDir)$(TargetName).pdb`, które generuje pliki .pdb w folderze wyjściowym.

   ![Generowanie plików PDB dla kompilacji w języku C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. Skompilowanie projektu.

   Kompilator tworzy pliki symboli w tym samym folderze co plik wykonywalny lub plik wyjściowy głównego.

## <a name="see-also"></a>Zobacz też

- [Określanie plików symboli (.pdb) i plików źródłowych w debugerze programu Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)<br/>
- [Ustawienia projektu dla konfiguracji debugowania w języku C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
- [Ustawienia projektu dla konfiguracji debugowania języka C#](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
- [Ustawienia projektu dla konfiguracji debugowania w języku Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
- [Instrukcje: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md)
