---
title: Ustawianie konfiguracji debugowania i wydania | Microsoft Docs
description: Ustawianie konfiguracji debugowania i wydania w programie Visual Studio. Można skompilować wersję do debugowania dla debugowania i wersję wydania dla ostatecznej dystrybucji wersji.
ms.custom: SEO-VS-2020
ms.date: 10/05/2018
ms.topic: how-to
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
ms.openlocfilehash: 51237a9b73825620c77c7f2a10ad1efe367cdd37
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149550"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Ustawianie konfiguracji debugowania i wersji w programie Visual Studio

Projekty programu Visual Studio mają osobne konfiguracje wersji i debugowania dla Twojego programu. Można skompilować wersję do debugowania dla debugowania i wersję wydania dla ostatecznej dystrybucji wersji.

W konfiguracji debugowania program kompiluje z pełnymi symbolicznymi informacjami o debugowaniu i bez optymalizacji. Optymalizacja komplikuje debugowanie, ponieważ relacja między kodem źródłowym i wygenerowanymi instrukcjami jest bardziej skomplikowana.

Konfiguracja wydania programu nie ma symbolicznych informacji o debugowaniu i jest w pełni zoptymalizowana. W przypadku kodu zarządzanego i kodu C++ informacje debugowania mogą być generowane w plikach. pdb, w zależności od używanych [opcji kompilatora](#BKMK_symbols_release) . Tworzenie plików. pdb może być przydatne, jeśli później będzie konieczne debugowanie wersji wydania.

Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [Omówienie konfiguracji kompilacji](../ide/understanding-build-configurations.md).

Konfigurację kompilacji można zmienić z menu **kompilacja** , na pasku narzędzi lub na stronach właściwości projektu. Strony właściwości projektu są specyficzne dla języka. W poniższej procedurze pokazano, jak zmienić konfigurację kompilacji z menu i paska narzędzi. Więcej informacji o sposobach zmiany konfiguracji kompilacji w projektach w różnych językach można znaleźć w sekcji [Zobacz też](#see-also) poniżej.

## <a name="change-the-build-configuration"></a>Zmień konfigurację kompilacji

Aby zmienić konfigurację kompilacji, należy wykonać jedną z:

* Z menu **kompilacja** wybierz pozycję **Configuration Manager**, a następnie wybierz pozycję **Debuguj** lub **Zwolnij**.

lub

* Na pasku narzędzi wybierz opcję **Debuguj** lub **Zwolnij** z listy **konfiguracje rozwiązań** .

  ![paski narzędzi — Konfiguracja kompilacji](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="generate-symbol-pdb-files-for-a-build-c-c-visual-basic-f"></a><a name="BKMK_symbols_release"></a>Generuj pliki symboli (. pdb) dla kompilacji (C#, C++, Visual Basic, F #)

Można wybrać opcję generowania plików symboli (. pdb) i informacji debugowania do uwzględnienia. W przypadku większości typów projektów kompilator generuje pliki symboli domyślnie dla kompilacji debugowania i wydania, podczas gdy inne ustawienia domyślne różnią się w zależności od typu projektu i wersji programu Visual Studio.

> [!IMPORTANT]
> Debuger będzie ładował tylko plik .pdb dla pliku wykonywalnego, który dokładnie pasuje do pliku .pdb, który z kolei został utworzony podczas kompilowania pliku wykonywalnego (czyli .pdb musi być plikiem oryginalnym lub kopią oryginalnego pliku .pdb). Aby uzyskać więcej informacji, zobacz [Dlaczego program Visual Studio wymaga, aby pliki symboli debugera były dokładnie zgodne z plikami binarnymi, z których zostały skompilowane?](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with).

Każdy typ projektu może mieć inny sposób ustawiania tych opcji.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Generuj pliki symboli dla projektu C#, ASP.NET lub Visual Basic

Aby uzyskać szczegółowe informacje na temat ustawień projektu dla konfiguracji debugowania w języku C# lub Visual Basic, zobacz [Ustawienia projektu dla konfiguracji debugowania w języku c#](../debugger/project-settings-for-csharp-debug-configurations.md) lub [Ustawienia projektu dla konfiguracji debugowania Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. W Eksplorator rozwiązań wybierz projekt.

2. Wybierz ikonę **Właściwości** (lub naciśnij klawisze **ALT + ENTER**).

3. W okienku po stronie wybierz opcję **Kompiluj** (lub **Kompiluj** w Visual Basic).

4. Na liście **Konfiguracja** wybierz **Debuguj** lub **Zwolnij**.

5. Wybierz przycisk **Zaawansowane** (lub przycisk **Zaawansowane opcje kompilowania** w Visual Basic).

6. Na liście **Informacje o debugowaniu** (lub **Generuj** listę informacji debugowania w Visual Basic) wybierz opcję **pełny**, plik **PDB-Only** lub **przenośny**.

   Formatem przenośnym jest najnowszy format Międzyplatformowy dla platformy .NET Core. Aby uzyskać więcej informacji na temat opcji, zobacz okno [dialogowe Zaawansowane ustawienia kompilacji (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

   ![Generowanie plików PDB dla kompilacji w języku C #](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. Skompilowanie projektu.

   Kompilator tworzy pliki symboli w tym samym folderze, w którym znajduje się plik wykonywalny lub główny pliku wyjściowego.

### <a name="generate-symbol-files-for-a-c-project"></a>Generuj pliki symboli dla projektu C++

1. W Eksplorator rozwiązań wybierz projekt.

2. Wybierz ikonę **Właściwości** (lub naciśnij klawisze **ALT + ENTER**).

3. Na liście **Konfiguracja** wybierz **Debuguj** lub **Zwolnij**.

4. W okienku po stronie wybierz pozycję **konsolidator > debugowanie**, a następnie wybierz pozycję Opcje **generowania informacji o debugowaniu**.

   Aby uzyskać szczegółowe informacje na temat ustawień projektu dla konfiguracji debugowania w języku C++, zobacz [Ustawienia projektu dla konfiguracji debugowania języka c++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

5. Skonfiguruj opcje **generowania plików bazy danych programu**.

   W większości projektów języka C++ wartość domyślna to `$(OutDir)$(TargetName).pdb` , która generuje pliki. pdb w folderze wyjściowym.

   ![Generowanie plików PDB dla kompilacji w języku C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. Skompilowanie projektu.

   Kompilator tworzy pliki symboli w tym samym folderze, w którym znajduje się plik wykonywalny lub główny pliku wyjściowego.

## <a name="see-also"></a><a name="see-also"></a>Zobacz także

- [Określanie plików symboli (. pdb) i plików źródłowych w debugerze programu Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)<br/>
- [Ustawienia projektu dla konfiguracji debugowania w języku C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
- [Ustawienia projektu dla konfiguracji debugowania języka C#](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
- [Ustawienia projektu dla konfiguracji debugowania w języku Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
- [Instrukcje: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md)