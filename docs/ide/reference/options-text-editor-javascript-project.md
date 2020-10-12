---
title: Opcje, Edytor tekstu, JavaScript, projekt
description: Dowiedz się, jak za pomocą strony projektu okna dialogowego Opcje określić opcje JavaScript i projektu TypeScript w edytorze kodu.
ms.custom: SEO-VS-2020
ms.date: 06/19/2020
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
ms.openlocfilehash: 86ee8f59a91cc772d6a86a9e29268b4465b2c639
ms.sourcegitcommit: a7944c325bedd8efbb244452741864089a02f5db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2020
ms.locfileid: "91947703"
---
# <a name="options-text-editor-javascript-project"></a>Opcje, Edytor tekstu, JavaScript, projekt

Na stronie **projekt** okna dialogowego **Opcje** można określić opcje JavaScript i projektu TypeScript w edytorze kodu. Aby uzyskać dostęp do tej strony, na pasku menu wybierz **Tools**  >  **Opcje**narzędzia, a następnie rozwiń węzeł **Edytor tekstu**  >  **JavaScript/TypeScript**  >  **Project**.

## <a name="project-analysis-options"></a>Opcje analizy projektu

Te opcje określają, jak edytor analizuje projekty, raporty diagnostyczne i sugeruje ulepszenia. Zaznacz lub usuń zaznaczenie opcji, aby określić, jak edytor obsługuje te sytuacje.

### <a name="uielement-list"></a>Lista elementów UIElement

- **Analizuj tylko projekty zawierające pliki otwarte w edytorze**
- **Tylko Diagnostyka raportów dla plików otwartych w edytorze**
- **Sugeruj możliwe udoskonalenia, które nie są poprawkami**

## <a name="virtual-projects-in-solution-explorer"></a>Projekty wirtualne w Eksplorator rozwiązań

Te opcje pozwalają zdecydować, czy mają być wyświetlane projekty wirtualne w przypadku załadowania lub załadowania rozwiązania.

## <a name="compile-on-save"></a>Kompiluj przy zapisywaniu

Te opcje określają, czy pliki TypeScript, które nie są częścią projektu, są kompilowane automatycznie. Program Visual Studio kompiluje się przy użyciu najnowszej wersji programu TypeScript zainstalowanej w *folderze C:\Program Files (x86) \Microsoft SDKs\TypeScript*.

Zaznacz pole wyboru, a następnie wybierz typ generowania kodu, który ma być używany.

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
|**Zachowywał**|Gdy ta opcja jest zaznaczona, Edytor kodu utrzymuje JSX jako część danych wyjściowych i emituje rozszerzenie pliku *. JSX* .|

## <a name="see-also"></a>Zobacz też

- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)