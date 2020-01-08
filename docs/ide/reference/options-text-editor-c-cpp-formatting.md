---
title: Opcje, edytor tekstu, C/C++, formatowanie
ms.date: 04/30/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- CPP
helpviewer_keywords:
- Text Editor Options dialog box, formatting
- ClangFormat
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
author: TerryGLee
ms.author: tglee
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: d7a6029058ab0bc02a623df0e1733eb8548102d5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596258"
---
# <a name="options-text-editor-cc-formatting"></a>Opcje, edytor tekstu, C/C++, formatowanie

Za pomocą tych stron właściwości można zmienić domyślne zachowanie edytora kodu podczas programowania w języku C lub C++.

![C++Formatowanie stron właściwości](media/cpp-formatting.png)

Aby uzyskać dostęp do tej strony, w oknie dialogowym **Opcje** w okienku po lewej stronie rozwiń pozycję **Edytor tekstu**, rozwiń pozycję **C++C/** , a następnie kliknij pozycję **Formatowanie**.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-page"></a>Strona ogólna

Ta strona zawiera opcje formatowania instrukcji i bloków podczas wpisywania.

::: moniker range="vs-2017"

**Program Visual Studio 2017 w wersji 15,7 lub nowszej**:

::: moniker-end

Na stronie znajdują się również opcje konfigurowania obsługi [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) w wersji 5,0. ClangFormat to narzędzie ułatwiające Stylowanie i formatowanie kodu na podstawie zestawu reguł, które można skonfigurować w formacie. Clang lub _clang pliku.

### <a name="configuring-clangformat-options"></a>Konfigurowanie opcji ClangFormat

::: moniker range="vs-2017"

**Program Visual Studio 2017 w wersji 15,7 lub nowszej**:

::: moniker-end

Obsługa ClangFormat jest domyślnie włączona. Możesz wybrać, które z tych typowych Konwencji formatowania mają być stosowane do wszystkich projektów: LLVM, Google, chrom, Mozilla lub WebKit. Można również utworzyć niestandardową definicję formatu. Clang-format pliku lub plik _clang. Jeśli taki plik znajduje się w folderze projektu, program Visual Studio używa go do formatowania wszystkich plików kodu źródłowego w tym folderze i jego podfolderach.

Domyślnie program Visual Studio uruchamia clangformat. exe w tle stosuje formatowanie podczas pisania. Można również określić, aby uruchomić ją tylko dla ręcznie wywoływanych poleceń formatowania **dokumentu (Ctrl + k, CTRL + D)** lub **formatowania (Ctrl + k, Ctrl + F)** .

## <a name="indentation-new-lines-spacing-wrapping-pages"></a>Wcięcia, nowe linie, odstępy zawijania stron

Te strony umożliwiają różne dostosowania formatowania, ale są ignorowane, jeśli ClangFormat jest włączona.

## <a name="see-also"></a>Zobacz także

- [Ogólne, Środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
- [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)
