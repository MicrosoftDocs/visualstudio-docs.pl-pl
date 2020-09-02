---
title: Strona opcji, Edytor tekstu — właściwości węzła | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Text Editor node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 19438302-0677-4f4d-9720-5667e6a22ab2
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 62dddacaea1846c8e5d5da404ad7a16fde90f209
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662418"
---
# <a name="options-page-text-editor-node-properties"></a>Strona opcji, edytor tekstu — Właściwości węzła
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W tym dokumencie opisano niektóre strony (lub kolekcje właściwości), które są skojarzone z kategorią **Edytor tekstu** , w oknie `DTE.Properties("TextEditor", <Property Page>)` dialogowym **Opcje** . Tytuł każdej podsekcji to wywołanie, które jest używane w celu uzyskania dostępu do `Properties` kolekcji, a tabela w każdej podsekcji wyświetla właściwości w kolekcji.

 Makra Visual Basic w obszarze [Ustawienia opcji sterowania](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) pokazują, jak wyświetlić bieżące opcje i ich wartości dla każdej strony okna dialogowego **Opcje** .

## <a name="general"></a>Ogólne
 `DTE.Properties("TextEditor", "General")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|GoToAnchorAfterEscape|Get/Set (wartość logiczna)|Jeśli `True` , naciśnięcie klawisza Escape, gdy istnieje zaznaczenie powoduje, że punkt wstawiania zostanie przeniesiony do miejsca, w którym zainicjowano akcję, która utworzyła zaznaczenie. `False` Przenosi punkt wstawiania do drugiego końca zaznaczenia.|
|DragNDropTextEditing|Get/Set (wartość logiczna)|Określa, czy można przeciągać wybrany region tekstu z jednego miejsca do innego dokumentu w celu wykonania operacji Kopiuj lub Wytnij i Wklej.|
|HorizontalScrollBar|Get/Set (wartość logiczna)|Określa, czy w oknach edytora jest poziomy pasek przewijania.|
|VerticalScrollBar|Get/Set (wartość logiczna)|Określa, czy w oknach edytora jest pionowy pasek przewijania.|
|SelectionMargin|Get/Set (wartość logiczna)|Określa, czy jest miejsce po lewej stronie okienka tekstu dla operacji specjalnych zaznaczenia, rysowania ikon przerwania itd.|
|MarginIndicatorBar|Get/Set (wartość logiczna)|Określa, czy istnieje pionowa linia oddzielająca lewy margines okienka tekstu od głównej części okienka tekstu.|
|UndoCaretActions|Get/Set (wartość logiczna)|Jeśli `True` . operacje cofania obejmują ruch punktu wstawiania, polecenia wyboru i tak dalej, oprócz czynności edycyjnych, które modyfikują bufor.|
|AutoDelimiterHighlighting|Get/Set (wartość logiczna)|Określa, czy wpisanie ogranicznika kończącego powoduje, że edytor wyróżnia ogranicznik otwierający. Edytor zawsze pogrubia ogranicznik otwierający, niezależnie od wartości tej właściwości.|
|EditorEmulation|Get/Set (Wyliczenie)||
|DetectUTF8WithoutSignature|Get/Set (wartość logiczna)|Wykrywa, czy plik używa kodowania UTF-8, gdy nie ma sygnatury kodowania.|
|TrackChanges|Get/Set (wartość logiczna)||

## <a name="plain-text"></a>Zwykły tekst
 `DTE.Properties("TextEditor", "PlainText")`

 `PlainText`Opcje edytora wpływają na ustawienia edytora, gdy pliki tekstowe są edytowane. Każdy język programowania i [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pakiet ma własne specyficzne ustawienia **edytora tekstu** . Na przykład, aby wyświetlić lub zmienić [!INCLUDE[csprcs](../../includes/csprcs-md.md)] Ustawienia edytora, użyj `DTE.Properties("TextEditor", "CSharp") or DTE.Properties("TextEditor", "CSharp-Specific")` . W ustawieniach edytora **skryptów SQL** Użyj `DTE.Properties("TextEditor", "SQL ")` .

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|AutoListMembers|Get/Set (wartość logiczna)|Określa, czy dostępna lista elementów członkowskich automatycznie się pojawia, gdy użytkownik wpisze kropkę po zmiennej odwołania.|
|AutoListParams|Get/Set (wartość logiczna)|Określa, czy opis listy argumentów automatycznie się pojawia, gdy użytkownik wpisze „(” po nazwie funkcji.|
|HideAdvancedMembers|Get/Set (wartość logiczna)|Określa, czy dokańczanie instrukcji zawiera listę wszystkich elementów członkowskich, czy tylko te często używane.|
|VirtualSpace|Get/Set (wartość logiczna)|Określa, czy znaki odstępu są wyświetlane jako grafika. Ustawienie tej opcji spowoduje `true` , że `WordWrap` element właściwości (na tej liście) ma być ustawiony na `false` .|
|WordWrap|Get/Set (wartość logiczna)|Określa, czy widok będzie zawijał długie wiersze na granicy słowa. Ustawienie tej opcji spowoduje `true` , że `VirtualSpace` element właściwości (na tej liście) ma być ustawiony na `false` .|
|WordWrapGlyphs|Get/Set (wartość logiczna)|Wyświetla znacznik na końcu wiersza; oznacza to, że wiersz jest zawijany do następnego wiersza.|
|EnableLeftClickForURLs|Get/Set (wartość logiczna)|Określa, czy edytor podkreśla adresy URL i włącza przejście do adresu URL w zarejestrowanej systemowej przeglądarce WWW po pojedynczym kliknięciu lewym przyciskiem myszy.|
|IndentStyle|Get/set ( <xref:EnvDTE.vsIndentStyle> )|Określa styl wcięcia tekstu: domyślne, inteligentne lub brak.|
|TabSize|Get/Set (Long)|Reprezentuje liczbę spacji, które są równe tabulacji. Ustawienie liczby całkowitej spoza zakresu od 1 do 60 (włącznie) kończy się niepowodzeniem.|
|InsertTabs|Get/Set (wartość logiczna)|Jeśli `True` znaki tabulacji są używane podczas tworzenia wcięcia.|
|IndentSize|Get/Set (Long)|Reprezentuje liczbę spacji, która jest równa jednemu poziomowi wcięcia. Ustawienie wartości całkowitej spoza zakresu 1-60 (włącznie) kończy się niepowodzeniem.|
|ShowLineNumbers|Get/Set (wartość logiczna)|Określa, czy w widoku głównego dokumentu edytora wyświetlają się numery wierszy na lewym marginesie.|
|ShowNavigationBar|Get/Set (wartość logiczna)|Określa, czy listy rozwijane i przyciski są wyświetlane w górnej części okna edytora.|
|CutCopyBlankLines|Get/Set (wartość logiczna)|Wycina lub kopiuje puste wiersze, gdy są zaznaczone.|

## <a name="see-also"></a>Zobacz też
 [Kontrolowanie ustawień opcji](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) [Określanie nazw elementów właściwości na](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) stronie Opcje strony Opcje, Strona Opcje [właściwości węzła środowiska](../../ide/reference/options-page-environment-node-properties.md) [, czcionki i kolory — właściwości węzła](../../ide/reference/options-page-fonts-and-colors-node-properties.md)
