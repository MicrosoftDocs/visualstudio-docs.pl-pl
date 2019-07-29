---
title: Opcje, edytor tekstu, JavaScript, formatowanie
ms.date: 10/29/2018
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.New_Lines
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.New_Lines
ms.assetid: 28a0aef1-9353-4d94-95a5-54b42e15c0dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 957dbd557a15c4c1df6028672f204a06936767c1
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605988"
---
# <a name="options-dialog-box-text-editor--javascript--formatting"></a>Opcje — okno dialogowe: Formatowanie JavaScript \> \> edytora tekstu

Na stronie **Formatowanie** okna dialogowego **Opcje** można ustawić opcje formatowania kodu w edytorze kodu. Aby uzyskać dostęp do tej strony, na pasku menu wybierz**Opcje** **Narzędzia** > , a następnie rozwiń pozycję **Edytor** > tekstu**JavaScript/TypeScript** > **Formatowanie**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="automatic-formatting"></a>Automatyczne formatowanie

Te opcje określają, kiedy formatowanie jest wykonywane w widoku **źródła** .

### <a name="uielement-list"></a>Lista elementów UI

|Opcja|Opis|
|------------|-----------------|
|**Formatuj wiersz ukończony po wprowadzeniu**|Gdy ta opcja jest zaznaczona, Edytor kodu automatycznie sformatuje wiersz po wybraniu klawisza ENTER.|
|**Formatowanie ukończonej instrukcji w;**|Gdy ta opcja jest zaznaczona, Edytor kodu automatycznie sformatuje wiersz w przypadku wybrania klucza średnika.|
|**Format otwarty blok na {**|Gdy ta opcja jest zaznaczona, Edytor kodu automatycznie sformatuje wiersz po wybraniu klawisza otwierającego nawiasu klamrowego.|
|**Formatowanie ukończonego bloku na}**|Gdy ta opcja jest zaznaczona, Edytor kodu automatycznie sformatuje wiersz po wybraniu klawisza zamykającego nawiasu klamrowego.|
|**Formatuj przy wklejaniu**|Gdy ta opcja jest zaznaczona, Edytor kodu ponownie sformatuje kod po wklejeniu go do edytora. Edytor używa aktualnie zdefiniowanych reguł formatowania. Jeśli ta opcja nie jest zaznaczona, Edytor używa oryginalnego formatowania wklejonego kodu.|

## <a name="new-lines"></a>Nowe wiersze

Te opcje określają, czy Edytor kodu umieszcza otwierający nawias klamrowy dla funkcji i bloków sterujących w nowym wierszu.

### <a name="uielement-list"></a>Lista elementów UIElement

|Opcja|Opis|
|------------|-----------------|
|**Umieść otwierający nawias klamrowy w nowym wierszu dla funkcji**|Po wybraniu tej opcji Edytor kodu przenosi otwierający nawias klamrowy skojarzony z funkcją do nowego wiersza.|
|**Umieść otwierający nawias klamrowy w nowym wierszu dla bloków sterowania**|Gdy ta opcja jest zaznaczona, Edytor kodu przenosi nawias otwierający, który jest skojarzony z blokiem sterowania (na przykład `if` `while` bloki sterujące) do nowego wiersza.|

## <a name="spacing"></a>Odstępy

Te opcje określają, jak spacje są wstawiane w widoku **źródła** .

### <a name="uielement-list"></a>Lista elementów UIElement

|Opcja|Opis|
|------------|-----------------|
|**Wstaw spację po ograniczniku przecinka**|Gdy ta opcja jest zaznaczona, Edytor kodu dodaje spację po przecinku.|
|**Wstaw spację po średniku w instrukcjach "for"**|Gdy ta opcja jest zaznaczona, Edytor kodu dodaje odstęp po każdym średniku w pierwszym wierszu `for` pętli.|
|**Wstaw spację przed operatorami binarnymi i po nich**|Gdy ta opcja jest zaznaczona, Edytor kodu dodaje spację przed operatorami binarnymi i po nich (na przykład +,-, & & &#124; &#124;,).|
|**Wstaw spację po słowach kluczowych w instrukcjach przepływu sterowania**|Gdy ta opcja jest zaznaczona, Edytor kodu dodaje odstęp po słowach kluczowych języka JavaScript w instrukcjach przepływu sterowania.|
|**Wstaw spację po słowie kluczowym function dla funkcji anonimowych**|Gdy ta opcja jest zaznaczona, Edytor kodu dodaje spację po `function` słowie kluczowym dla funkcji anonimowych.|
|**Wstaw spację po otwarciu i przed zamknięciem niepustego nawiasu**|Gdy ta opcja jest zaznaczona, Edytor kodu dodaje odstęp po nawiasie otwierającym i przed nawiasem zamykającym, jeśli znaki niepuste są obecne w nawiasach.|

## <a name="see-also"></a>Zobacz także

- [Ogólne, Środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)