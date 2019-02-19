---
title: Opcje, Edytor tekstów, Basic (Visual Basic) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 244c7224d0008c21250da68b518c1a0a55755545
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54800714"
---
# <a name="options-text-editor-basic-visual-basic"></a>Opcje, edytor tekstów, Basic (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
**VB określonych** stronie właściwości, **podstawowe** folderu **edytora tekstów** folderu **opcje** (**narzędzia** menu) okno dialogowe zawiera następujące właściwości:  
  
 **Automatyczne wstawianie konstrukcji końcowych**  
 Podczas wpisywania — na przykład pierwszy wiersz deklaracja procedury `Sub Main—`i naciśnij klawisz ENTER, Edytor tekstu dodaje pasujący obiekt typu `End Sub` wiersza. Podobnie jeśli dodasz [dla](http://msdn.microsoft.com/library/f5fc0d51-67ce-4c36-9f09-31c9a91c94e9) pętli, Edytor tekstu dodaje pasujący obiekt typu `Next` instrukcji. Gdy ta opcja jest zaznaczona, Edytor kodu automatycznie dodaje konstrukcja końcowa.  
  
 **Lista pretty (ponowne formatowanie) kodu**  
 Edytor tekstu formatuje kodu zgodnie z potrzebami. Gdy ta opcja jest zaznaczona, Edytor kodu wykonują następujące czynności:  
  
- Wyrównaj kod do położenia odpowiedniej karcie  
  
- Recase słów kluczowych, zmienne i obiekty do odpowiedniej wielkości liter  
  
- Dodaj brakujące `Then` do `If...Then` — instrukcja  
  
- Dodaj nawiasy do wywołania funkcji  
  
- Dodaj brakujące nawiasy zakończenia na ciągi  
  
- Zapis wykładniczy formatowania  
  
- Ponowne formatowanie dat  
  
  **Włącz tryb konspektu**  
  Po otwarciu pliku w edytorze kodu, możesz wyświetlić dokument w trybie konspektu. Zobacz [konspekt](../../ide/outlining.md) Aby uzyskać więcej informacji. Gdy ta opcja jest zaznaczona, funkcję tworzenia konspektów jest aktywowany po otwarciu pliku.  
  
  **Automatyczne wstawianie składowych Interface i MustOverride**  
  Jeśli zdecydujesz się `Implements` instrukcji lub `Inherits` instrukcji dla klasy, Edytor tekstu wstawia prototypy dla elementów członkowskich, które mają zostać zaimplementowane lub została zastąpiona, odpowiednio.  
  
  **Pokaż separatory wierszy procedury**  
  Edytor tekstu wskazuje zakres visual procedur. Linia jest rysowana w plikach źródłowych .vb projektu w lokalizacjach, wymienione w poniższej tabeli:  
  
|Lokalizacja w pliku źródłowym .vb|Przykład lokalizację wiersza|  
|---------------------------------|------------------------------|  
|Po zamknięciu bloku konstrukcja deklaracji|-Na końcu klasy, struktury, moduł, interfejs lub wyliczenie<br />-After właściwości, funkcji lub sub<br />-Nie między get i set klauzule we właściwości|  
|Po zestaw konstrukcji w jednym wierszu|-After instrukcje importowania, przed definicją typu w pliku klasy<br />-After zmienne zadeklarowane w klasie, zanim wszelkie procedury|  
|Po jednym wierszu deklaracji (-block deklaracje poziomu)|— Następujące instrukcje importu dziedziczy instrukcji, deklaracji zmiennych, deklaracji zdarzeń, delegat deklaracje i biblioteki DLL zadeklarować instrukcji|  
  
 **Włącz sugestie korekty błędów**  
 Edytor tekstu można zasugerować rozwiązania typowych problemów i pozwalają wybrać odpowiednią poprawkę, co jest następnie stosowane do kodu.  
  
 **Włącz wyróżnianie odwołań i słów kluczowych**  
 Edytor tekstu można wyróżnić wszystkich wystąpień symbolu lub wszystkich słów kluczowych w klauzuli takich jak `If..Then`, `While...End While`, lub `Try...Catch...Finally`. Możesz przechodzić między do wyróżnionych odwołań lub słów kluczowych, naciskając klawisz Strzałka CTRL + SHIFT + Strzałka w dół lub CTRL + SHIFT + Strzałka w górę Strzałka.  
  
## <a name="see-also"></a>Zobacz też  
 [Ogólne, środowisko, okno dialogowe Opcje](../../ide/reference/general-environment-options-dialog-box.md)   
 [Opcje, Edytor tekstów, Wszystkie języki, Karty](../../ide/reference/options-text-editor-all-languages-tabs.md)
