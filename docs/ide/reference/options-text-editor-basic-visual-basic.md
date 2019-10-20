---
title: Opcje, Edytor tekstu, Basic (VB), zaawansowane
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a07645597846bd85f3152da866a253b079bc3963
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666343"
---
# <a name="options-text-editor-basic-visual-basic-advanced"></a>Opcje, Edytor tekstu, podstawowe (Visual Basic), zaawansowane
Strona **właściwości specyficzne dla języka vb** w folderze **podstawowa** folderu **Edytor tekstu** okna dialogowego **Opcje** (menu**Narzędzia** ) zawiera następujące właściwości:

## <a name="analysis"></a>Analiza

- Włączanie pełnej analizy rozwiązania

   Włącza analizę kodu dla wszystkich plików w rozwiązaniu, a nie tylko otwartych plików kodu. Aby uzyskać więcej informacji, zobacz [Pełna analiza rozwiązania](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="using-directives"></a>Dyrektywy using

- Umieść dyrektywy "system" jako pierwsze podczas sortowania przy użyciu

   Po wybraniu polecenia **Usuń i Sortuj przy użyciu** w menu rozwijanym prawym przyciskiem myszy sortuje dyrektywy `using` i umieszcza przestrzenie nazw "system" na początku listy.

- Oddziel przy użyciu grupy dyrektywy

   Po wybraniu polecenia **Usuń i Sortuj przy użyciu** w menu rozwijanym prawym przyciskiem myszy oddziela dyrektywy `using`, wstawiając pusty wiersz między grupami dyrektyw, które mają tę samą główną przestrzeń nazw.

- Sugeruj użycie dla typów w zestawach odwołań
- Sugeruj użycie dla typów w pakietach NuGet

   Po wybraniu tych opcji można wykonać [szybką akcję](../quick-actions.md) , aby zainstalować pakiet NuGet i dodać dyrektywę `using` dla typów bez odwołań.

   ![Szybka akcja instalacji pakietu NuGet w programie Visual Studio](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Wyróżnianie

 **Włącz podświetlanie odwołań i słów kluczowych**

Edytor tekstu może wyróżnić wszystkie wystąpienia symbolu lub wszystkie słowa kluczowe w klauzuli, takie jak `If..Then`, `While...End While` lub `Try...Catch...Finally`. Możesz nawigować między wyróżnionymi odwołaniami i słowami kluczowymi, naciskając klawisz **Ctrl**  + **SHIFT**  + **strzałkę w dół** lub **Ctrl**  + **SHIFT**  + **strzałkę w górę**.

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

Po wybraniu linie pionowe pojawiają się w edytorze, który jest wierszem ze strukturą bloków kodu, dzięki czemu można łatwo identyfikować poszczególne bloki kodu. Na przykład zobaczysz linię między `Sub` i `EndSub` w instrukcji `Sub`.

## <a name="editor-help"></a>Pomoc edytora

**Łatwa lista (ponowne formatowanie) kodu** Edytor tekstu ponownie sformatuje kod zgodnie z potrzebami. Po wybraniu tej opcji Edytor kodu będzie:

- Dopasuj kod do poprawnej pozycji tabulacji

- Przypadki słowa kluczowego, zmienne i obiekty w poprawnej wielkości liter

- Dodaj brakujące `Then` do instrukcji `If...Then`

- Dodawanie nawiasu do wywołań funkcji

- Dodaj brakujące cudzysłowy końcowe do ciągów

- Formatowanie notacji wykładniczej

- Formatowanie dat

**Automatyczne wstawianie konstrukcji końcowych**

Gdy wpiszesz — na przykład pierwszy wiersz deklaracji procedury, `Sub Main` — i naciśnij klawisz **Enter**, Edytor tekstu dodaje pasujący wiersz `End Sub`. Podobnie, jeśli dodasz pętlę [for](/dotnet/visual-basic/language-reference/statements/for-next-statement) , Edytor tekstu dodaje pasującą instrukcję `Next`. Gdy ta opcja jest zaznaczona, Edytor kodu automatycznie dodaje końcową konstrukcję.

**Automatyczne wstawianie elementów członkowskich interfejsu i MustOverride**

W przypadku zatwierdzania instrukcji `Implements` lub instrukcji `Inherits` dla klasy Edytor tekstu wstawia prototypy dla elementów członkowskich, które muszą być odpowiednio zaimplementowane lub zastąpione.

**Włącz sugestie dotyczące korekcji błędów**

Edytor tekstu może sugerować rozwiązania typowych błędów i umożliwia wybranie odpowiedniej poprawki, która zostanie następnie zastosowana do Twojego kodu.

## <a name="see-also"></a>Zobacz także

- [Ogólne, Środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
- [Opcje, Edytor tekstów, Wszystkie języki, Karty](../../ide/reference/options-text-editor-all-languages-tabs.md)
