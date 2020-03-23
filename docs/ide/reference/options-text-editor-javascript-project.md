---
title: Opcje, Edytor tekstu, JavaScript, Projekt
ms.date: 1/15/2019
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 190cbdb2a8096415985d83fc525b997572d252c2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "68605929"
---
# <a name="options-text-editor-javascript-project"></a>Opcje, Edytor tekstu, JavaScript, Projekt

Strona **Projekt** okna dialogowego **Opcje** służy do określania opcji projektu JavaScript i TypeScript w Edytorze kodu. Aby uzyskać dostęp do tej strony, na pasku menu wybierz pozycję**Opcje** **narzędzi** > , a następnie rozwiń pozycję **Edytor** > tekstu**JavaScript/TypeScript** > **Project**.

## <a name="project-analysis-options"></a>Opcje analizy projektu

Te opcje określają sposób, w jaki edytor analizuje projekty, raportuje diagnostykę i sugeruje ulepszenia. Wybierz lub wyczyść opcje, aby określić, jak edytor obsługuje te sytuacje.

### <a name="uielement-list"></a>Lista UIElement

- **Analizuj tylko projekty zawierające pliki otwarte w edytorze**
- **Raportowanie tylko dla plików otwartych w edytorze**
- **Zasugeruj możliwe ulepszenia, które nie są poprawkami**

## <a name="virtual-projects-in-solution-explorer"></a>Projekty wirtualne w Eksploratorze rozwiązań

Te opcje umożliwiają wybranie, czy projekty wirtualne mają być wyświetlane po załadowaniu rozwiązania, czy nie.

## <a name="compile-on-save"></a>Kompilowanie przy zapisywaniu

Te opcje określają, czy pliki TypeScript, które nie są częścią projektu, są kompilowane automatycznie. Zaznacz to pole wyboru, a następnie wybierz typ generowania kodu do użycia.

### <a name="uielement-list"></a>Lista UIElement

- **Użyj generowania kodu AMD dla modułów, które nie są częścią projektu**
- **Użyj generowania kodu CommonJS dla modułów, które nie są częścią projektu**
- **Użyj generowania kodu UMD dla modułów, które nie są częścią projektu**
- **Użyj generowania kodu systemu dla modułów, które nie są częścią projektu**
- **Użyj generowania kodu ES2015 dla modułów, które nie są częścią projektu**

## <a name="ecmascript-version-for-files-that-are-not-part-of-a-project"></a>Wersja ECMAScript dla plików, które nie są częścią projektu

Te opcje umożliwiają wybranie wersji ECMAScript dla plików, które nie są częścią projektu. Można wybrać między **ECMAScript 3**, **ECMAScript 5**lub **ECMAScript 6**.

## <a name="jsx-emit-for-tsx-files-that-are-not-part-of-a-project"></a>JSX Emit dla plików TSX, które nie są częścią projektu

Te opcje określają sposób, w jaki edytor traktuje pliki TypeScript, które nie są częścią projektu.

### <a name="uielement-list"></a>Lista UIElement

|Opcja|Opis|
|------------|-----------------|
|**Ramy reagowania**|Po wybraniu tej opcji Edytor kodu emituje rozszerzenie pliku *.js.*|
|**Zachować**|Gdy ta opcja jest zaznaczona, Edytor kodu zachowuje JSX jako część danych wyjściowych i emituje rozszerzenie pliku *.jsx.*|

## <a name="see-also"></a>Zobacz też

- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)