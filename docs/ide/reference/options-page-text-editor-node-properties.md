---
title: Strona opcji, edytor tekstu — Właściwości węzła
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Text Editor node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 19438302-0677-4f4d-9720-5667e6a22ab2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b04897304bc90d35bcf9fd5e61f5329ce922ea91
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55924659"
---
# <a name="options-page-text-editor-node-properties"></a>Strona opcji, edytor tekstu — Właściwości węzła
W tym dokumencie opisano niektóre strony (lub kolekcje właściwości), są skojarzone z **edytora tekstów** kategorii `DTE.Properties("TextEditor", <Property Page>)`, z **opcje** okno dialogowe. Tytuł każdej podsekcji to wywołanie, które jest używane do dostępu `Properties` kolekcji, a tabela w każdej podsekcji zawiera listę właściwości w kolekcji.

 Makra języka Visual Basic w [Controlling Options Settings](https://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d) pokazują, jak wyświetlić bieżące opcje i ich wartości dla każdej strony **opcje** okno dialogowe.

## <a name="general"></a>Ogólne
 `DTE.Properties("TextEditor", "General")`

|Nazwa elementu właściwości|Wartość|Opis|
| - |-----------|-----------------|
|GoToAnchorAfterEscape|Get/Set (wartość logiczna)|Jeśli `True`, wciśnięcie klawisza escape, gdy coś jest zaznaczone powoduje, że punkt wstawiania przejść do której zainicjowano akcję, która utworzyła zaznaczenie. `False` Przenosi punkt wstawiania na drugi koniec zaznaczenia.|
|DragNDropTextEditing|Get/Set (wartość logiczna)|Określa, czy można przeciągać wybrany region tekstu z jednego miejsca do innego dokumentu w celu wykonania operacji Kopiuj lub Wytnij i Wklej.|
|HorizontalScrollBar|Get/Set (wartość logiczna)|Określa, czy w oknach edytora jest poziomy pasek przewijania.|
|VerticalScrollBar|Get/Set (wartość logiczna)|Określa, czy w oknach edytora jest pionowy pasek przewijania.|
|SelectionMargin|Get/Set (wartość logiczna)|Określa, czy jest miejsce po lewej stronie okienka tekstu dla operacji specjalnych zaznaczenia, rysowania ikon przerwania itd.|
|MarginIndicatorBar|Get/Set (wartość logiczna)|Określa, czy istnieje pionowa linia oddzielająca lewy margines okienka tekstu od głównej części okienka tekstu.|
|UndoCaretActions|Get/Set (wartość logiczna)|If `True`. Operacje cofania obejmują ruch punktu wstawiania, polecenia zaznaczania i tak dalej, oprócz edycji czynności, które modyfikują bufor.|
|AutoDelimiterHighlighting|Get/Set (wartość logiczna)|Określa, czy wpisanie ogranicznika kończącego powoduje, że edytor wyróżnia ogranicznik otwierający. Edytor zawsze pogrubia ogranicznik otwierający, niezależnie od wartości tej właściwości.|
|EditorEmulation|Get/Set (Wyliczenie)||
|DetectUTF8WithoutSignature|Get/Set (wartość logiczna)|Wykrywa, czy plik używa kodowania UTF-8, gdy nie ma sygnatury kodowania.|
|TrackChanges|Get/Set (wartość logiczna)||

## <a name="plain-text"></a>Zwykły tekst
 `DTE.Properties("TextEditor", "PlainText")`

 `PlainText` Opcji edytora wpływają na ustawienia edytora podczas edytowania plików tekstowych. Każdy język programowania i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pakiet ma swoje własne szczególne **edytora tekstów** ustawienia. Na przykład, aby wyświetlić lub zmienić [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ustawienia edytora, użyj `DTE.Properties("TextEditor", "CSharp") or DTE.Properties("TextEditor", "CSharp-Specific")`. Aby uzyskać **skrypt SQL** ustawienia edytora, użyj `DTE.Properties("TextEditor", "SQL ")`.

|Nazwa elementu właściwości|Wartość|Opis|
| - |-----------|-----------------|
|AutoListMembers|Get/Set (wartość logiczna)|Określa, czy dostępna lista elementów członkowskich automatycznie się pojawia, gdy użytkownik wpisze kropkę po zmiennej odwołania.|
|AutoListParams|Get/Set (wartość logiczna)|Określa, czy opis listy argumentów automatycznie się pojawia, gdy użytkownik wpisze „(” po nazwie funkcji.|
|HideAdvancedMembers|Get/Set (wartość logiczna)|Określa, czy dokańczanie instrukcji zawiera listę wszystkich elementów członkowskich, czy tylko te często używane.|
|VirtualSpace|Get/Set (wartość logiczna)|Określa, czy znaki odstępu są wyświetlane jako grafika. Ustawienie tej opcji na `true` powoduje, że `WordWrap` element właściwości (na tej liście), należy ustawić `false`.|
|WordWrap|Get/Set (wartość logiczna)|Określa, czy widok będzie zawijał długie wiersze na granicy słowa. Ustawienie tej opcji na `true` powoduje, że `VirtualSpace` element właściwości (na tej liście), należy ustawić `false`.|
|WordWrapGlyphs|Get/Set (wartość logiczna)|Wyświetla znacznik na końcu wiersza; oznacza to, że wiersz jest zawijany do następnego wiersza.|
|EnableLeftClickForURLs|Get/Set (wartość logiczna)|Określa, czy edytor podkreśla adresy URL i umożliwia pojedynczego przejście do adresu URL w przeglądarce internetowej zarejestrowanych systemu.|
|IndentStyle|Get/Set (<xref:EnvDTE.vsIndentStyle>)|Określa styl wcięcia tekstu: Domyślne, inteligentne lub Brak.|
|TabSize|Get/Set (Long)|Reprezentuje liczbę spacji, które są równe tabulatorowi. Ustawienie liczby całkowitej spoza zakresu 1-60 (włącznie) kończy się niepowodzeniem.|
|InsertTabs|Get/Set (wartość logiczna)|Jeśli `True`, są używane znaki tabulacji.|
|IndentSize|Get/Set (Long)|Reprezentuje liczbę spacji, która jest równa jednemu poziomowi wcięcia. Ustawienie wartości całkowitej spoza zakresu 1-60 (włącznie) kończy się niepowodzeniem.|
|ShowLineNumbers|Get/Set (wartość logiczna)|Określa, czy w widoku głównego dokumentu edytora wyświetlają się numery wierszy na lewym marginesie.|
|ShowNavigationBar|Get/Set (wartość logiczna)|Określa, czy listy rozwijane i przyciski są wyświetlane w górnej części okna edytora.|
|CutCopyBlankLines|Get/Set (wartość logiczna)|Wycina lub kopiuje puste wiersze, gdy są zaznaczone.|

## <a name="see-also"></a>Zobacz też

- [Kontrolowanie ustawień opcji](https://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [Określanie nazw elementów właściwości na stronach opcji](https://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [Strona opcji, środowisko — Właściwości węzła](../../ide/reference/options-page-environment-node-properties.md)
- [Strona opcji, czcionki i kolory — Właściwości węzła](../../ide/reference/options-page-fonts-and-colors-node-properties.md)