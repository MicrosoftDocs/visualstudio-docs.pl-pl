---
title: Opcje, Edytor tekstu, Podstawowy (VB), Zaawansowane
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 562358ca90e223a07926aaa383ded41a5f7557cc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79431478"
---
# <a name="options-text-editor-basic-visual-basic-advanced"></a>Opcje, Edytor tekstu, Podstawowy (Visual Basic), Zaawansowane
Strona właściwości **VB Specific** w folderze **Podstawowe** folderu **Edytor tekstu** w oknie dialogowym **Opcje** **(Narzędzia)** zawiera następujące właściwości:

## <a name="analysis"></a>Analiza

- Analiza kodu na żywo lub zakres analizy w tle

   Skonfiguruj zakres analizy w tle dla kodu zarządzanego. Aby uzyskać więcej informacji, zobacz [Jak: Konfigurowanie zakresu analizy kodu na żywo dla kodu zarządzanego](../../code-quality/configure-live-code-analysis-scope-managed-code.md).

## <a name="using-directives"></a>Korzystanie z dyrektyw

- Umieść dyrektywy "System" na pierwszym miejscu podczas sortowania za pomocą

   Po wybraniu tej opcji polecenie **Usuń i posortuj usings** w menu prawym przyciskiem myszy sortuje `using` dyrektywy i umieszcza obszary nazw "System" u góry listy.

- Oddzielanie grup dyrektyw przy użyciu

   Po wybraniu tej opcji polecenie **Usuń i sortuj usings** w menu po kliknięciu prawym przyciskiem myszy oddziela `using` dyrektywy, wstawiając pustą linię między grupami dyrektyw, które mają ten sam główny obszar nazw.

- Sugerowanie użycia typów w złożeniach referencyjnych
- Sugerowanie użycia typów w pakietach NuGet

   Gdy te opcje są zaznaczone, [szybka akcja](../quick-actions.md) jest dostępna `using` do zainstalowania pakietu NuGet i dodać dyrektywę dla typów bez odwołań.

   ![Szybka akcja instalowania pakietu NuGet w programie Visual Studio](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Wyróżnianie

 **Włączanie wyróżniania odwołań i słów kluczowych**

Edytor tekstu może wyróżnić wszystkie wystąpienia symbolu lub wszystkie `If..Then`słowa `While...End While`kluczowe `Try...Catch...Finally`w klauzuli, takie jak , lub . Możesz poruszać się między wyróżnionymi odniesieniami lub słowami kluczowymi, naciskając **klawisze Ctrl** + **Shift** + **w dół** lub klawisz **Ctrl** + **Shift** + w**górę**.

## <a name="outlining"></a>Tworzenie konspektu

**Włącz tryb tworzenia zamielenia**

Po otwarciu pliku w edytorze kodu można wyświetlić dokument w trybie tworzenia. Zobacz [Tworzenie przedstawiające, aby](../../ide/outlining.md) uzyskać więcej informacji. Po wybraniu tej opcji funkcja tworzenia wartości jest aktywowana po otwarciu pliku.

**Pokaż separatory linii procedury**

Edytor tekstu wskazuje wizualny zakres procedur. Linia jest rysowana w plikach *źródłowych .vb* projektu w lokalizacjach wymienionych w poniższej tabeli:

|Lokalizacja w pliku źródłowym .vb|Przykład lokalizacji wiersza|
|---------------------------------|------------------------------|
|Po zamknięciu konstrukcji deklaracji bloku|- Na końcu klasy, struktury, modułu, interfejsu lub wyliczenia<br />- Po właściwości, funkcji lub sub<br />- Nie między get i set klauzule w właściwości|
|Po zestawie konstrukcji jednoliniowych|- Po instrukcjach importu przed definicją typu w pliku klasy<br />- Po zmiennych zadeklarowanych w klasie, przed jakimikolwiek procedurami|
|Po deklaracjach jednowierszowych (deklaracje na poziomie nieblokowym)|- Po instrukcji importu, dziedziczy instrukcje, deklaracje zmiennych, deklaracje zdarzeń, deklaracje delegata i dll zadeklarować instrukcje|

## <a name="block-structure-guides"></a>Prowadnice struktury bloków

Po zaznaczeniu tej opcji w edytorze pojawiają się pionowe linie, które są zgodne ze strukturalnymi blokami kodu, co umożliwia łatwą identyfikację poszczególnych bloków kodu. Na przykład zostanie wyświetlony wiersz `Sub` `EndSub` między `Sub` i w instrukcji.

## <a name="editor-help"></a>Pomoc edytora

**Ładna lista (formatowanie) kodu** Edytor tekstu formatuje kod odpowiednio. Po wybraniu tej opcji edytor kodu:

- Wyrównaj kod do prawidłowego położenia karty

- Ponowne przywróć słowa kluczowe, zmienne i obiekty do prawidłowej sprawy

- Dodawanie brakujących `Then` `If...Then` do instrukcji

- Dodawanie nawiasów do wywołań funkcji

- Dodawanie brakujących cudzysłowów końcowych do ciągów

- Sformatowanie wykładniczego notacji

- Daty formaty

**Automatyczne wstawianie konstrukcji końcowych**

Po wpisaniu — na przykład pierwszym wierszu `Sub Main`deklaracji procedury — i naciśnięciu **klawisza Enter**edytor tekstu dodaje pasujący `End Sub` wiersz. Podobnie po dodaniu [For](/dotnet/visual-basic/language-reference/statements/for-next-statement) pętli, edytor tekstu `Next` dodaje pasujące instrukcji. Gdy ta opcja jest zaznaczona, edytor kodu automatycznie dodaje konstruktora końcowego.

**Automatyczne wstawianie elementów członkowskich interfejsu i mustoverride**

Podczas zatwierdzania `Implements` instrukcji `Inherits` lub instrukcji dla klasy edytor tekstu wstawia prototypy dla elementów członkowskich, które muszą być zaimplementowane lub zastąpione, odpowiednio.

**Włączanie sugestii korekcji błędów**

Edytor tekstu może sugerować rozwiązania typowych błędów i umożliwia wybranie odpowiedniej korekty, która jest następnie stosowana do kodu.

## <a name="see-also"></a>Zobacz też

- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
- [Opcje, Edytor tekstów, Wszystkie języki, Karty](../../ide/reference/options-text-editor-all-languages-tabs.md)
