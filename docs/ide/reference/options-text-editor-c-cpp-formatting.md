---
title: Opcje, edytor tekstu, C/C++, formatowanie
ms.date: 04/30/2018
ms.prod: visual-studio-dev15
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
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 6aa4c543d19c43bd397d7d18a185a73a4bf161a6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53960751"
---
# <a name="options-text-editor-cc-formatting"></a>Opcje, edytor tekstu, C/C++, formatowanie

Użyj tych stron właściwości, aby zmienić domyślne zachowanie edytora kodu, podczas programowania w języku C lub C++.

[Strony właściwości języka C++, formatowanie](media/cpp-formatting.png)

 Dostępu do tej strony, w **opcje** rozwiń w lewym okienku w oknie dialogowym **edytora tekstów**, rozwiń węzeł **C/C++**, a następnie kliknij przycisk **formatowanie** .

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-page"></a>Strona ogólna

Ta strona zawiera opcje formatowania instrukcji i bloków, podczas ich wpisywania.

**Visual Studio 2017 w wersji 15.7 lub nowszej**: Strona zawiera również opcje dotyczące konfigurowania obsługi adaptera [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) wersji 5.0. Narzędzie ClangFormat to narzędzie, które można łatwo styl i formatowanie kodu na podstawie zestawu reguł, które można skonfigurować w pliku clang format lub _clang-format.

### <a name="configuring-clangformat-options"></a>Konfigurowanie opcji narzędzia ClangFormat

W programie Visual Studio 2017 wersji 15.7 lub nowszej Obsługa narzędzia ClangFormat jest włączona domyślnie. Możesz wybrać, które z tych typowych Konwencji formatowanie, aby zastosować do wszystkich projektów: Maszyny wirtualnej niskiego poziomu, Google, chrom, Mozilla lub aparatu WebKit. Można również utworzyć definicję formatu niestandardowego pliku clang format lub _clang-format. Jeśli taki plik znajduje się w folderze projektu, Visual Studio używa jej do formatowania wszystkich plikach kodu źródłowego, w tym folderze i jego podfolderach. 

Domyślnie program Visual Studio clangformat.exe działa w tle, który ma zastosowanie formatowania podczas wpisywania. Można również określić ręcznie uruchomić je tylko w przypadku wywołana poleceń formatowania **Formatuj dokument (Ctrl + K, Ctrl + D)** lub **Formatuj zaznaczenie (Ctrl + K, Ctrl + F)**.


## <a name="indentation-new-lines-spacing-wrapping-pages"></a>Strony zawijania odstępy wcięcia, nowych wierszy

Te strony włączyć różne dostosowań formatowania, ale są ignorowane, jeśli narzędzie ClangFormat jest włączona.

## <a name="see-also"></a>Zobacz też

- [Ogólne, Środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
- [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)