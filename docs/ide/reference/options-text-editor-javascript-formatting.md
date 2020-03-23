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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "68605988"
---
# <a name="options-dialog-box-text-editor--javascript--formatting"></a>Okno dialogowe Opcje: \> Formatowanie w języku JavaScript edytora \> tekstu

Strona **Formatowanie** okna dialogowego **Opcje** służy do ustawiania opcji formatowania kodu w Edytorze kodów. Aby uzyskać dostęp do tej strony, na pasku menu wybierz pozycję**Opcje** **narzędzi** > , a następnie rozwiń pozycję Formatowanie**JavaScript/TypeScript** >  **w edytorze** > tekstu .**Formatting**

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="automatic-formatting"></a>Automatyczne formatowanie

Te opcje określają, kiedy formatowanie występuje w widoku **źródłowym.**

### <a name="uielement-list"></a>Lista elementów UI

|Opcja|Opis|
|------------|-----------------|
|**Formatowanie wiersza zakończonego na enter**|Po wybraniu tej opcji Edytor kodu automatycznie formatuje wiersz po wybraniu klawisza Enter.|
|**Formatowanie wypełnionego oświadczenia na ;**|Po wybraniu tej opcji Edytor kodu automatycznie formatuje wiersz po wybraniu klucza średnika.|
|**Format otwarty blok na {**|Po wybraniu tej opcji Edytor kodu automatycznie formatuje wiersz po wybraniu otwierającego klawisza nawiasu klamrowego.|
|**Format ukończony blok na }**|Po wybraniu tej opcji Edytor kodu automatycznie formatuje wiersz po wybraniu zamykającego klawisza stężenia.|
|**Format przy wklejać**|Gdy ta opcja jest zaznaczona, Edytor kodu formatuje kod po wklejeniu go do edytora. Edytor używa aktualnie zdefiniowanych reguł formatowania. Jeśli ta opcja nie jest zaznaczona, edytor używa oryginalnego formatowania wklejony kod.|

## <a name="new-lines"></a>Nowe linie

Te opcje określają, czy Edytor kodu umieszcza otwarty nawias klamrowy dla funkcji i bloków sterowania w nowym wierszu.

### <a name="uielement-list"></a>Lista UIElement

|Opcja|Opis|
|------------|-----------------|
|**Umieść otwartą klamrę w nowym wierszu dla funkcji**|Gdy ta opcja jest zaznaczona, Edytor kodu przenosi otwarty nawias klamrowy skojarzony z funkcją do nowego wiersza.|
|**Umieść otwartą klamrę na nowej linii dla bloków sterujących**|Gdy ta opcja jest zaznaczona, Edytor kodu przenosi otwarty nawias klamrowy `if` `while` skojarzony z blokiem sterowania (na przykład i blokami sterującymi) do nowego wiersza.|

## <a name="spacing"></a>Odstępy

Te opcje określają sposób wstawiania spacji w widoku **źródłowym.**

### <a name="uielement-list"></a>Lista UIElement

|Opcja|Opis|
|------------|-----------------|
|**Wstawianie miejsca po ograniczniku przecinka**|Po wybraniu tej opcji Edytor kodu dodaje spację po ogranicznika przecinków.|
|**Wstaw przestrzeń po średnikowej w instrukcjach "for"**|Po wybraniu tej opcji Edytor kodu dodaje spację po każdym średnikowym w pierwszym wierszu `for` pętli.|
|**Wstawianie spacji przed i po operatorach binarnych**|Po wybraniu tej opcji Edytor kodu dodaje spację przed i po operatorach binarnych (na przykład +, -, &&, &#124;&#124;).|
|**Wstawianie spacji po słowach kluczowych w instrukcjach przepływu sterowania**|Po wybraniu tej opcji Edytor kodu dodaje spację po słowach kluczowych JavaScript w instrukcjach przepływu sterowania.|
|**Wstawianie spacji po słowie kluczowym funkcji dla funkcji anonimowych**|Po wybraniu tej opcji Edytor kodu dodaje `function` spację po słowie kluczowym dla funkcji anonimowych.|
|**Wstawianie odstępu po otwarciu i przed zamknięciem niepustego nawiasu**|Gdy ta opcja jest zaznaczona, Edytor kodu dodaje spację po nawiasie otwierającym i przed nawiasem zamykającym, jeśli w nawiasach znajdują się niepuste znaki.|

## <a name="see-also"></a>Zobacz też

- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)