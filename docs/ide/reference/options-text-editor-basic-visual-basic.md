---
title: Options, Text Editor, Basic (VB), Advanced
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.Advanced
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a7ea9c2efd6a204932e24de0ef250ba143b8b34
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55925465"
---
# <a name="options-text-editor-basic-visual-basic-advanced"></a>Options, Text Editor, Basic (Visual Basic), Advanced
**VB określonych** stronie właściwości, **podstawowe** folderu **edytora tekstów** folderu **opcje** (**narzędzia** menu) okno dialogowe zawiera następujące właściwości:

## <a name="analysis"></a>Analiza

- Włączanie pełnej analizy rozwiązania

   Włącza analizę kodu dla wszystkich plików w rozwiązaniu, nie wystarczy otworzyć plików kodu. Aby uzyskać więcej informacji, zobacz [pełnej analizy rozwiązania](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="using-directives"></a>Dyrektywy Using

- Umieść najpierw dyrektywy "System" podczas sortowania deklaracji Using

   Po wybraniu **Usuń i Sortuj wyrażenia Using** w sortuje menu kliknij prawym przyciskiem myszy polecenie `using` dyrektywy i miejsc przestrzeni nazw "System" w górnej części listy.

- Oddziel grupy dyrektywy using

   Po wybraniu **Usuń i Sortuj wyrażenia Using** oddziela polecenia w menu kliknij prawym przyciskiem myszy `using` dyrektyw, wstawiając pusty wiersz między grupami dyrektyw, które mają ten sam głównej przestrzeni nazw.

- Sugeruj dyrektywy Using dla typów w zestawach referencyjnych
- Sugeruj dyrektywy Using dla typów w pakietach NuGet

   Po wybraniu tych opcji [szybka akcja](../quick-actions.md) jest dostępna zainstalować pakiet NuGet i dodać `using` dyrektywy dla typów bez odwołań.

   ![Szybkie działanie, aby zainstalować pakiet NuGet w programie Visual Studio](media/nuget-lightbulb.png)


## <a name="highlighting"></a>Wyróżnianie

 **Włącz wyróżnianie odwołań i słów kluczowych**

Edytor tekstu można wyróżnić wszystkich wystąpień symbolu lub wszystkie słowa kluczowe w klauzuli takich jak `If..Then`, `While...End While`, lub `Try...Catch...Finally`. Możesz przechodzić między do wyróżnionych odwołań lub słów kluczowych, naciskając klawisz **Ctrl** + **Shift** + **Strzałka w dół** lub **Ctrl**   +  **Shift** + **Strzałka w górę**.

## <a name="outlining"></a>Tworzenie konspektu

**Włącz tryb konspektu**

Po otwarciu pliku w edytorze kodu, możesz wyświetlić dokument w trybie konspektu. Zobacz [konspekt](../../ide/outlining.md) Aby uzyskać więcej informacji. Gdy ta opcja jest zaznaczona, funkcję tworzenia konspektów jest aktywowany po otwarciu pliku.

**Pokaż separatory wierszy procedury**

Edytor tekstu wskazuje zakres visual procedur. Linia jest rysowana *.vb* pliki źródłowe projektu w lokalizacjach wymienione w poniższej tabeli:

|Lokalizacja w pliku źródłowym .vb|Przykład lokalizację wiersza|
|---------------------------------|------------------------------|
|Po zamknięciu bloku konstrukcja deklaracji|-Na końcu klasy, struktury, moduł, interfejs lub wyliczenie<br />-After właściwości, funkcji lub sub<br />-Nie między get i set klauzule we właściwości|
|Po zestaw konstrukcji w jednym wierszu|-After instrukcje importowania, przed definicją typu w pliku klasy<br />-After zmienne zadeklarowane w klasie, zanim wszelkie procedury|
|Po jednym wierszu deklaracji (-block deklaracje poziomu)|— Następujące instrukcje importu dziedziczy instrukcji, deklaracji zmiennych, deklaracji zdarzeń, delegat deklaracje i biblioteki DLL zadeklarować instrukcji|

## <a name="block-structure-guides"></a>Prowadnice struktury blokowej

Po wybraniu wyświetlane pionowe linie w edytorze tego wiersza się przy użyciu bloków kodu ze strukturą, co pozwala łatwo identyfikować poszczególnych bloków kodu. Na przykład, zostanie wyświetlony wiersz między `Sub` i `EndSub` w `Sub` instrukcji.

## <a name="editor-help"></a>Pomoc Edytora

**Formatowania kodu (ponowne formatowanie) kodu** Edytor tekstu formatuje kodu zgodnie z potrzebami. Gdy ta opcja jest zaznaczona, Edytor kodu wykonują następujące czynności:

-   Wyrównaj kod do położenia odpowiedniej karcie

-   Recase słów kluczowych, zmienne i obiekty do odpowiedniej wielkości liter

-   Dodaj brakujące `Then` do `If...Then` — instrukcja

-   Dodaj nawiasy do wywołania funkcji

-   Dodaj brakujące nawiasy zakończenia na ciągi

-   Zapis wykładniczy formatowania

-   Ponowne formatowanie dat

**Automatyczne wstawianie konstrukcji końcowych**

Podczas wpisywania — na przykład pierwszy wiersz deklaracja procedury `Sub Main`— i naciśnij klawisz **Enter**, Edytor tekstu dodaje pasujący obiekt typu `End Sub` wiersza. Podobnie jeśli dodasz [dla](/dotnet/visual-basic/language-reference/statements/for-next-statement) pętli, Edytor tekstu dodaje pasujący obiekt typu `Next` instrukcji. Gdy ta opcja jest zaznaczona, Edytor kodu automatycznie dodaje konstrukcja końcowa.

**Automatyczne wstawianie składowych Interface i MustOverride**

Jeśli zdecydujesz się `Implements` instrukcji lub `Inherits` instrukcji dla klasy, Edytor tekstu wstawia prototypy dla elementów członkowskich, które mają zostać zaimplementowane lub została zastąpiona, odpowiednio.

**Włącz sugestie korekty błędów**

Edytor tekstu można zasugerować rozwiązania typowych problemów i pozwalają wybrać odpowiednią poprawkę, co jest następnie stosowane do kodu.

## <a name="see-also"></a>Zobacz także

- [Ogólne, Środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
- [Opcje, Edytor tekstów, Wszystkie języki, Karty](../../ide/reference/options-text-editor-all-languages-tabs.md)
