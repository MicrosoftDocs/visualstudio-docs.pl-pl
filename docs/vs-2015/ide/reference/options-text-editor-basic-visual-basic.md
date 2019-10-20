---
title: Opcje, Edytor tekstu, Basic (Visual Basic) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1edb7ceae1ba187b01b92d64ca33d41d83364e72
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662370"
---
# <a name="options-text-editor-basic-visual-basic"></a>Opcje, edytor tekstów, Basic (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Strona **właściwości specyficzne dla języka vb** w folderze **podstawowa** folderu **Edytor tekstu** okna dialogowego **Opcje** (menu**Narzędzia** ) zawiera następujące właściwości:

 **Automatyczne wstawianie konstrukcji końcowych** Gdy wpiszesz — na przykład pierwszy wiersz deklaracji procedury, `Sub Main—`and naciśnij klawisz ENTER, Edytor tekstu dodaje pasujący wiersz `End Sub`. Podobnie, jeśli dodasz pętlę [for](https://msdn.microsoft.com/library/f5fc0d51-67ce-4c36-9f09-31c9a91c94e9) , Edytor tekstu dodaje pasującą instrukcję `Next`. Gdy ta opcja jest zaznaczona, Edytor kodu automatycznie dodaje końcową konstrukcję.

 **Łatwa lista (ponowne formatowanie) kodu** Edytor tekstu ponownie sformatuje kod zgodnie z potrzebami. Po wybraniu tej opcji Edytor kodu będzie:

- Dopasuj kod do poprawnej pozycji tabulacji

- Przypadki słowa kluczowego, zmienne i obiekty w poprawnej wielkości liter

- Dodaj brakujące `Then` do instrukcji `If...Then`

- Dodawanie nawiasu do wywołań funkcji

- Dodaj brakujące cudzysłowy końcowe do ciągów

- Formatowanie notacji wykładniczej

- Formatowanie dat

  **Włącz tryb tworzenia konspektu** Po otwarciu pliku w edytorze kodu można wyświetlić dokument w trybie tworzenia konspektu. Aby uzyskać więcej informacji, zobacz [Tworzenie konspektu](../../ide/outlining.md) . Po wybraniu tej opcji funkcja tworzenia konspektu jest uaktywniana po otwarciu pliku.

  **Automatyczne wstawianie elementów członkowskich interfejsu i MustOverride** W przypadku zatwierdzania instrukcji `Implements` lub instrukcji `Inherits` dla klasy Edytor tekstu wstawia prototypy dla elementów członkowskich, które muszą być odpowiednio zaimplementowane lub zastąpione.

  **Pokaż separatory wierszy procedury** Edytor tekstu wskazuje wizualny zakres procedur. Wiersz jest rysowany w plikach źródłowych. vb projektu w lokalizacjach wymienionych w poniższej tabeli:

|Lokalizacja w pliku źródłowym. vb|Przykład lokalizacji wiersza|
|---------------------------------|------------------------------|
|Po zamknięciu konstrukcji deklaracji bloku|-Na końcu klasy, struktury, modułu, interfejsu lub wyliczenia<br />-Po właściwości, funkcji lub sub<br />-Nie między klauzulami get i Set we właściwości|
|Po zestawie pojedynczych konstrukcji|-Po instrukcjach importu przed definicją typu w pliku klasy<br />-Po zmiennych zadeklarowanych w klasie przed wszelkimi procedurami|
|Po deklaracjach pojedynczego wiersza (deklaracje na poziomie niebloku)|-Następujące instrukcje importu, instrukcje dziedziczenia, deklaracje zmiennych, deklaracje zdarzeń, deklaracje delegata i instrukcje dotyczące bibliotek DLL|

 **Włącz sugestie dotyczące korekcji błędów** Edytor tekstu może sugerować rozwiązania typowych błędów i umożliwia wybranie odpowiedniej poprawki, która zostanie następnie zastosowana do Twojego kodu.

 **Włącz podświetlanie odwołań i słów kluczowych** Edytor tekstu może wyróżnić wszystkie wystąpienia symbolu lub wszystkie słowa kluczowe w klauzuli, takie jak `If..Then`, `While...End While` lub `Try...Catch...Finally`. Możesz nawigować między wyróżnionymi odwołaniami i słowami kluczowymi, naciskając klawisze CTRL + SHIFT + Strzałka w dół lub CTRL + SHIFT + Strzałka w górę.

## <a name="see-also"></a>Zobacz też
 [Ogólne, środowisko, opcje okna dialogowego](../../ide/reference/general-environment-options-dialog-box.md) [Opcje, Edytor tekstu, wszystkie języki, karty](../../ide/reference/options-text-editor-all-languages-tabs.md)
