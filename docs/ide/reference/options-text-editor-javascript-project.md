---
title: Options, Text Editor, JavaScript, Project
ms.date: 1/15/2019
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7be14c9953fed34e7bdd9507b6224875b1008a22
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54350184"
---
# <a name="options-text-editor-javascript-project"></a>Options, Text Editor, JavaScript, Project

Użyj **projektu** strony **opcje** okno dialogowe, aby określić opcje projektu JavaScript w edytorze kodu. Dostępu do tej strony, na pasku menu wybierz **narzędzia** > **opcje**, a następnie rozwiń węzeł **edytora tekstów** > **językaJavaScript**  >  **Projektu**.

## <a name="project-analysis-options"></a>Opcje analizy projektów

Te opcje określają, jak edytor analizuje projektów, raporty diagnostyczne i sugeruje ulepszenia. Zaznacz lub wyczyść opcje, aby określić sposób obsługi tych sytuacji w edytorze.

### <a name="uielement-list"></a>Lista elementów interfejsu użytkownika

- **Analizuj tylko projekty zawierające pliki otwarte w edytorze**
- **Zgłaszaj tylko diagnostykę dla plików otwartych w edytorze**
- **Zaproponuj możliwych ulepszeń, które nie są poprawki**

## <a name="virtual-projects-in-solution-explorer"></a>Projekty wirtualne w Eksploratorze rozwiązań

Te opcje pozwalają wybrać, czy do wyświetlenia projekty wirtualne, gdy rozwiązanie jest załadowany lub nie załadowano. 

## <a name="compile-on-save"></a>Kompiluj przy zapisywaniu

Te opcje określają, czy pliki TypeScript, które nie są częścią projektu automatycznie są kompilowane. Zaznacz pole wyboru, a następnie wybierz typ generacji kodu do użycia.

### <a name="uielement-list"></a>Lista elementów interfejsu użytkownika

- **Użyj generowania kodu AMD dla modułów, które nie są częścią projektu**
- **Użyj CommonJS generowanie kodu dla modułów, które nie są częścią projektu**
- **Użyj generowania kodu wyjścia dla modułów, które nie są częścią projektu**
- **Użyj generowania kodu systemu dla modułów, które nie są częścią projektu**
- **Użyj generowania kodu ES2015 dla modułów, które nie są częścią projektu**

## <a name="ecmascript-version-for-files-that-are-not-part-of-a-project"></a>W wersji ECMAScript dla plików, które nie są częścią projektu

Te opcje można wybrać wersję ECMAScript dla plików, które nie są częścią projektu. Możesz wybrać między **ECMAScript 3**, **ECMAScript 5**, lub **ECMAScript 6**.

## <a name="jsx-emit-for-tsx-files-that-are-not-part-of-a-project"></a>Użyciu emisji JSX dla plików TSX, które nie są częścią projektu

Te opcje określają, w jaki sposób traktuje pliki TypeScript, które nie są częścią projektu w edytorze.

### <a name="uielement-list"></a>Lista elementów interfejsu użytkownika

|Opcja|Opis|
|------------|-----------------|
|**Platforma react**|Gdy ta opcja jest zaznaczona, Edytor kodu emituje *js* rozszerzenie pliku.|
|**Preserve**|Gdy ta opcja jest zaznaczona, Edytor kodu, elementy JSX jako część danych wyjściowych i emituje *jsx* rozszerzenie pliku.|

## <a name="see-also"></a>Zobacz także

- [Ogólne, Środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)