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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596258"
---
# <a name="options-text-editor-cc-formatting"></a>Opcje, edytor tekstu, C/C++, formatowanie

Użyj tych stron właściwości, aby zmienić domyślne zachowanie edytora kodu podczas programowania w języku C lub C++.

![Strony właściwości formatowanie języka C++](media/cpp-formatting.png)

Aby uzyskać dostęp do tej strony, w oknie dialogowym **Opcje** w lewym okienku rozwiń pozycję **Edytor tekstu**, rozwiń węzeł **C/C++,** a następnie kliknij pozycję **Formatowanie**.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie ide programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-page"></a>Strona ogólna

Na tej stronie dostępne są opcje formatowania instrukcji i bloków podczas ich wpisywanie.

::: moniker range="vs-2017"

**Visual Studio 2017 w wersji 15.7 i nowszej:**

::: moniker-end

Strona ma również opcje konfigurowania obsługi [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) w wersji 5.0. ClangFormat to narzędzie, które ułatwia stylowanie i formatowanie kodu na podstawie zestawu reguł, które można skonfigurować w formacie .clang lub pliku w formacie _clang.

### <a name="configuring-clangformat-options"></a>Konfigurowanie opcji ClangFormat

::: moniker range="vs-2017"

**Visual Studio 2017 w wersji 15.7 i nowszej:**

::: moniker-end

Obsługa ClangFormat jest domyślnie włączona. Możesz wybrać, która z tych popularnych konwencji formatowania ma być stosowana do wszystkich projektów: LLVM, Google, Chromium, Mozilla lub WebKit. Można również utworzyć niestandardową definicję formatu .clang-format lub plik w formacie _clang. Jeśli taki plik jest obecny w folderze projektu, program Visual Studio używa go do formatowania wszystkich plików kodu źródłowego w tym folderze i jego podfolderach.

Domyślnie program Visual Studio uruchamia program clangformat.exe w tle stosuje formatowanie podczas pisania. Można również określić, aby uruchomić go tylko dla ręcznie wywoływanych poleceń formatowania **Format dokumentu (Ctrl+K, Ctrl+D)** lub **Zaznaczenie formatu (Ctrl + K, Ctrl + F)**.

## <a name="indentation-new-lines-spacing-wrapping-pages"></a>Wcięcie, nowe wiersze, strony zawijania odstępów

Strony te umożliwiają różne dostosowania formatowania, ale są ignorowane, jeśli clangformat jest włączony.

## <a name="see-also"></a>Zobacz też

- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
- [Korzystanie z IntelliSense](../../ide/using-intellisense.md)
