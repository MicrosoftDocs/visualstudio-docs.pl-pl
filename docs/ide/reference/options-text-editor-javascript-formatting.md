---
title: Opcje, edytor tekstu, JavaScript, formatowanie
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.New_Lines
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.New_Lines
ms.assetid: 28a0aef1-9353-4d94-95a5-54b42e15c0dc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa846a25e1383c0c164dfb4747899f5e86237d32
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671056"
---
# <a name="options-text-editor-javascript-formatting"></a>Opcje, edytor tekstu, JavaScript, formatowanie
Użyj **formatowanie** strony **opcje** okno dialogowe, aby ustawić opcje formatowania kodu w edytorze kodu. Dostępu do tej strony, na pasku menu wybierz **narzędzia**, **opcje**, a następnie rozwiń węzeł **edytora tekstów**, **JavaScript**i **Formatowanie**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="automatic-formatting"></a>Automatyczne formatowanie
 Te opcje określają, kiedy formatowanie występuje w **źródła** widoku.

### <a name="uielement-list"></a>Lista elementów UI

|Opcja|Opis|
|------------|-----------------|
|**Formatuj ukończony wiersz na wprowadź**|Gdy ta opcja jest zaznaczona, Edytor kodu automatycznie formatuje wiersz po naciśnij klawisz Enter.|
|**Formatuj ukończony instrukcji.**|Gdy ta opcja jest zaznaczona, Edytor kodu automatycznie formatuje wiersz, po wybraniu klawisza średnikami.|
|**Blok otwarty format na {**|Gdy ta opcja jest zaznaczona, Edytor kodu automatycznie formatuje wiersz, w przypadku otwarcia klucza nawiasu klamrowego.|
|**Formatuj ukończony blok po naciśnięciu}**|Gdy ta opcja jest zaznaczona, Edytor kodu automatycznie formatuje wiersz, w przypadku wybrania zamykający nawias klamrowy klucza.|
|**Formatuj przy wklejeniu**|Gdy ta opcja jest zaznaczona, Edytor kodu formatuje kod, wkleić go do edytora. Edytor przy użyciu aktualnie zdefiniowanych reguł formatowania. Jeśli ta opcja nie jest zaznaczone, Edytor używa oryginalne formatowanie kodu w wklejone.|

## <a name="new-lines"></a>Nowe wiersze
 Te opcje określają, czy edytor kodu umieszcza otwierający nawias klamrowy, funkcje i bloki sterujące w nowym wierszu.

### <a name="uielement-list"></a>Lista elementów UI

|Opcja|Opis|
|------------|-----------------|
|**Umieść otwierający nawias klamrowy w nowym wierszu dla funkcji**|Edytor kodu, gdy ta opcja jest zaznaczona, przenosi otwierający nawias klamrowy, skojarzone z funkcją do nowego wiersza.|
|**Umieść otwierający nawias klamrowy w nowym wierszu dla bloków sterowania**|Gdy ta opcja jest zaznaczona, Edytor kodu przenosi otwierający nawias klamrowy, skojarzone z bloku sterowania (na przykład `if` i `while` bloki sterujące) do nowego wiersza.|

## <a name="spacing"></a>Odstępy
 Te opcje określają, jak spacje są dodawane w **źródła** widoku.

### <a name="uielement-list"></a>Lista elementów UI

|Opcja|Opis|
|------------|-----------------|
|**Wstaw spację po przecinek oddzielający**|Gdy ta opcja jest zaznaczona, Edytor kodu dodaje odstęp po ograniczniki przecinkami.|
|**Wstaw spację po średniku w instrukcji "for"**|Gdy ta opcja jest zaznaczona, Edytor kodu dodaje odstęp po każdym średniku w pierwszym wierszu `for` pętli.|
|**Wstaw spację przed operatorami binarnymi i po**|Gdy ta opcja jest zaznaczona, Edytor kodu spację przed operatorami binarnymi i po (na przykład, +, -, & &, &#124; &#124;).|
|**Wstaw spację po słowach kluczowych w instrukcjach przepływu sterowania**|Gdy ta opcja jest zaznaczona, Edytor kodu dodaje odstęp po słowach kluczowych języka JavaScript, w instrukcjach przepływu sterowania.|
|**Wstaw spację po funkcji — słowo kluczowe dla funkcji anonimowych**|Gdy ta opcja jest zaznaczona, Edytor kodu dodaje odstęp po `function` kluczowym dla funkcji anonimowych.|
|**Wstaw spację po otwarciu i przed zamknięciem nawiasu niepustego**|Gdy ta opcja jest zaznaczona, Edytor kodu dodaje odstęp po nawiasie otwierającym, a także przed nawiasem zamykającym Jeśli znaków niepuste znajdują się w nawiasach.|

## <a name="see-also"></a>Zobacz też

- [Ogólne, Środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)