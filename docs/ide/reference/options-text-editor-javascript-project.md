---
title: Opcje, Edytor tekstu, JavaScript, projekt
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
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605929"
---
# <a name="options-text-editor-javascript-project"></a>Opcje, Edytor tekstu, JavaScript, projekt

Na stronie **projekt** okna dialogowego **Opcje** można określić opcje JavaScript i projektu TypeScript w edytorze kodu. Aby uzyskać dostęp do tej strony, na pasku menu wybierz**Opcje** **Narzędzia** > , a następnie rozwiń węzeł **Edytor** > tekstu**JavaScript/TypeScript** >  **.**

## <a name="project-analysis-options"></a>Opcje analizy projektu

Te opcje określają, jak edytor analizuje projekty, raporty diagnostyczne i sugeruje ulepszenia. Zaznacz lub usuń zaznaczenie opcji, aby określić, jak edytor obsługuje te sytuacje.

### <a name="uielement-list"></a>Lista elementów UIElement

- **Analizuj tylko projekty zawierające pliki otwarte w edytorze**
- **Tylko Diagnostyka raportów dla plików otwartych w edytorze**
- **Sugeruj możliwe udoskonalenia, które nie są poprawkami**

## <a name="virtual-projects-in-solution-explorer"></a>Projekty wirtualne w Eksplorator rozwiązań

Te opcje pozwalają zdecydować, czy mają być wyświetlane projekty wirtualne w przypadku załadowania lub załadowania rozwiązania.

## <a name="compile-on-save"></a>Kompiluj przy zapisywaniu

Te opcje określają, czy pliki TypeScript, które nie są częścią projektu, są kompilowane automatycznie. Zaznacz pole wyboru, a następnie wybierz typ generowania kodu, który ma być używany.

### <a name="uielement-list"></a>Lista elementów UIElement

- **Użyj generowania kodu AMD dla modułów, które nie są częścią projektu**
- **Użyj generowania kodu CommonJS dla modułów, które nie są częścią projektu**
- **Użyj generowania kodu UMD dla modułów, które nie są częścią projektu**
- **Użyj generowania kodu systemowego dla modułów, które nie są częścią projektu**
- **Użyj generowania kodu ES2015 dla modułów, które nie są częścią projektu**

## <a name="ecmascript-version-for-files-that-are-not-part-of-a-project"></a>Wersja języka ECMAScript dla plików, które nie są częścią projektu

Te opcje umożliwiają wybranie wersji języka ECMAScript dla plików, które nie są częścią projektu. Można wybrać między **ECMAScript 3**, **ECMAScript 5**lub **ECMAScript 6**.

## <a name="jsx-emit-for-tsx-files-that-are-not-part-of-a-project"></a>JSX Emituj dla plików TSX, które nie są częścią projektu

Te opcje określają, jak edytor traktuje pliki TypeScript, które nie są częścią projektu.

### <a name="uielement-list"></a>Lista elementów UIElement

|Opcja|Opis|
|------------|-----------------|
|**Platforma reagowania**|Gdy ta opcja jest zaznaczona, Edytor kodu emituje rozszerzenie pliku *. js* .|
|**Preserve**|Gdy ta opcja jest zaznaczona, Edytor kodu utrzymuje JSX jako część danych wyjściowych i emituje rozszerzenie pliku *. JSX* .|

## <a name="see-also"></a>Zobacz także

- [Ogólne, Środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)