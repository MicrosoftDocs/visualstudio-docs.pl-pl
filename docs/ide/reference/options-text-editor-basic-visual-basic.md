---
title: Opcje, Edytor tekstu, Basic (VB), zaawansowane
ms.date: 08/12/2020
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
author: akhera99
ms.author: midumont
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 778cd1f9c126b176cafad8b33a147d284bea1b67
ms.sourcegitcommit: 2946d802aec1418e87bfa779d81834eeb7be5c9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2020
ms.locfileid: "88214652"
---
# <a name="options-text-editor-basic-visual-basic-advanced"></a>Opcje, Edytor tekstu, podstawowe (Visual Basic), zaawansowane
Strona **właściwości specyficzne dla języka vb** w folderze **podstawowa** folderu **Edytor tekstu** okna dialogowego **Opcje** (menu**Narzędzia** ) zawiera następujące właściwości:

## <a name="analysis"></a>Analiza

- Analiza kodu na żywo lub zakres analizy w tle

   Skonfiguruj zakres analizy w tle dla kodu zarządzanego. Aby uzyskać więcej informacji, zobacz [How to: Configure Live Code Analysis Scope for Managed Code](../../code-quality/configure-live-code-analysis-scope-managed-code.md).

## <a name="using-directives"></a>Dyrektywy using

- Umieść dyrektywy "system" jako pierwsze podczas sortowania przy użyciu

   Po wybraniu polecenia **Usuń i Sortuj przy użyciu** w menu rozwijanym po kliknięciu prawym przyciskiem myszy sortuje `using` dyrektywy i umieszcza przestrzenie nazw "system" w górnej części listy.

- Oddziel przy użyciu grupy dyrektywy

   Po wybraniu polecenia **Usuń i Sortuj przy użyciu** w menu rozwijanym prawym przyciskiem myszy oddziela `using` dyrektywy przez wstawianie pustego wiersza między grupami dyrektyw, które mają tę samą główną przestrzeń nazw.

- Sugeruj użycie dla typów w zestawach odwołań
- Sugeruj użycie dla typów w pakietach NuGet

   Po wybraniu tych opcji można wykonać [szybką akcję](../quick-actions.md) , aby zainstalować pakiet NuGet i dodać `using` dyrektywę dla typów bez odwołań.

   ![Szybka akcja instalacji pakietu NuGet w programie Visual Studio](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Wyróżnianie

 **Włącz podświetlanie odwołań i słów kluczowych**

Edytor tekstu może wyróżnić wszystkie wystąpienia symbolu lub wszystkie słowa kluczowe w klauzuli, takiej jak `If..Then` , `While...End While` , lub `Try...Catch...Finally` . Możesz przechodzić między wyróżnionymi odwołaniami lub słowami kluczowymi, naciskając **klawisze CTRL**  +  **SHIFT**  +  **Strzałka w dół** lub **Ctrl**  +  **SHIFT**  +  **Strzałka w górę**.

## <a name="outlining"></a>Tworzenie konspektu

**Włącz tryb tworzenia konspektu**

Po otwarciu pliku w edytorze kodu można wyświetlić dokument w trybie tworzenia konspektu. Aby uzyskać więcej informacji, zobacz [Tworzenie konspektu](../../ide/outlining.md) . Po wybraniu tej opcji funkcja tworzenia konspektu jest uaktywniana po otwarciu pliku.

**Pokaż separatory wierszy procedury**

Edytor tekstu wskazuje wizualny zakres procedur. Wiersz jest rysowany w plikach źródłowych *. vb* projektu w lokalizacjach wymienionych w poniższej tabeli:

|Lokalizacja w pliku źródłowym. vb|Przykład lokalizacji wiersza|
|---------------------------------|------------------------------|
|Po zamknięciu konstrukcji deklaracji bloku|-Na końcu klasy, struktury, modułu, interfejsu lub wyliczenia<br />-Po właściwości, funkcji lub sub<br />-Nie między klauzulami get i Set we właściwości|
|Po zestawie pojedynczych konstrukcji|-Po instrukcjach importu przed definicją typu w pliku klasy<br />-Po zmiennych zadeklarowanych w klasie przed wszelkimi procedurami|
|Po deklaracjach pojedynczego wiersza (deklaracje na poziomie niebloku)|-Następujące instrukcje importu, instrukcje dziedziczenia, deklaracje zmiennych, deklaracje zdarzeń, deklaracje delegata i instrukcje dotyczące bibliotek DLL|

## <a name="block-structure-guides"></a>Prowadnice struktury blokowej

Po wybraniu linie pionowe pojawiają się w edytorze, który jest wierszem ze strukturą bloków kodu, dzięki czemu można łatwo identyfikować poszczególne bloki kodu. Na przykład zobaczysz linię między `Sub` i `EndSub` w `Sub` instrukcji.

## <a name="editor-help"></a>Pomoc edytora

::: moniker range=">=vs-2019"
**Wskazówki dotyczące nazwy parametru wbudowanego**    
Po wybraniu wstawia wskazówki dotyczące nazw parametrów dla literałów, literałów rzutowania i wystąpień obiektów przed każdym argumentem w wywołaniach funkcji.  

![Wskazówki dotyczące nazwy parametru wbudowanego dla Visual Basic](media/inline-parameter-name-hints-visualbasic.png)
::: moniker-end

**Łatwa lista (ponowne formatowanie) kodu** Edytor tekstu ponownie sformatuje kod zgodnie z potrzebami. Po wybraniu tej opcji Edytor kodu będzie:

- Dopasuj kod do poprawnej pozycji tabulacji

- Przypadki słowa kluczowego, zmienne i obiekty w poprawnej wielkości liter

- Dodaj brakujący `Then` element do `If...Then` instrukcji

- Dodawanie nawiasu do wywołań funkcji

- Dodaj brakujące cudzysłowy końcowe do ciągów

- Formatowanie notacji wykładniczej

- Formatowanie dat

**Automatyczne wstawianie konstrukcji końcowych**

Gdy wpiszesz — na przykład pierwszy wiersz deklaracji procedury, `Sub Main` — i naciśnij klawisz **Enter**, Edytor tekstu dodaje pasujący `End Sub` wiersz. Podobnie, jeśli dodasz pętlę [for](/dotnet/visual-basic/language-reference/statements/for-next-statement) , Edytor tekstu dodaje pasującą `Next` instrukcję. Gdy ta opcja jest zaznaczona, Edytor kodu automatycznie dodaje końcową konstrukcję.

**Automatyczne wstawianie elementów członkowskich interfejsu i MustOverride**

Podczas zatwierdzania `Implements` instrukcji lub `Inherits` instrukcji dla klasy, Edytor tekstu wstawia prototypy dla elementów członkowskich, które muszą być odpowiednio zaimplementowane lub zastąpione.

**Włącz sugestie dotyczące korekcji błędów**

Edytor tekstu może sugerować rozwiązania typowych błędów i umożliwia wybranie odpowiedniej poprawki, która zostanie następnie zastosowana do Twojego kodu.

## <a name="see-also"></a>Zobacz też

- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
- [Opcje, Edytor tekstów, Wszystkie języki, Karty](../../ide/reference/options-text-editor-all-languages-tabs.md)
