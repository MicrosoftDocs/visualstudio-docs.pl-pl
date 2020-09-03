---
title: 'Bookmark, formant:'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Bookmark
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, controlling
- Bookmark control, data binding
- Bookmark control, events
- Bookmark control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2b8557581e93c8d2ba5a54a13c04d5de74b24f71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255148"
---
# <a name="bookmark-control"></a>Bookmark, formant:
  <xref:Microsoft.Office.Tools.Word.Bookmark>Kontrolka jest zakładką, która ma unikatową nazwę, uwidacznia zdarzenia i może być powiązana z danymi. Zakładka może służyć jako symbol zastępczy do oznaczania elementu lub lokalizacji w Microsoft Office dokumencie programu Word. <xref:Microsoft.Office.Tools.Word.Bookmark>Kontrolka jest kombinacją <xref:Microsoft.Office.Interop.Word.Bookmark> obiektu i <xref:Microsoft.Office.Interop.Word.Range> obiektu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 W projektach na poziomie dokumentu można dodawać <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki do dokumentu w czasie projektowania lub w czasie wykonywania. W projektach dodatku VSTO można dodać <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki do dowolnego otwartego dokumentu w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie kontrolek zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

## <a name="bind-data-to-the-control"></a>Powiąż dane z kontrolką
 <xref:Microsoft.Office.Tools.Word.Bookmark>Kontrolka obsługuje proste powiązanie danych. Zakładka powinna być powiązana ze źródłem danych przy użyciu <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> właściwości. Domyślną właściwością powiązania danych zakładki jest <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> Właściwość.

 Jeśli dane w powiązanym zestawie danych zostaną zaktualizowane, <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolka wyświetli te zmiany.

 W projektach na poziomie dokumentu można także powiązać dane z zakładkami przy użyciu okna **źródła danych** . Aby uzyskać więcej informacji, zobacz [How to: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md).

## <a name="formatting"></a>Formatowanie
 Formatowanie, które można zastosować do elementu, <xref:Microsoft.Office.Interop.Word.Bookmark> można zastosować do <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki. To formatowanie obejmuje czcionki, wcięcia, odstępy, numerację i style.

## <a name="assign-text-to-the-bookmark"></a>Przypisywanie tekstu do zakładki
 Dodatkowa różnica między <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> obiektem a <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> kontrolką jest zachowaniem, gdy tekst jest przypisany do zakładki. W przypadku przypisywania tekstu do długości zerowej <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> tekst jest dołączany po prawej stronie zakładki, a zakładki pozostają zerowej długości. Jeśli jednak tekst zostanie przypisany do zerowej długości <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> , tekst zostanie wstawiony do zakładki, a długość zakładki zostanie rozwinięta do całkowitej liczby wstawionych znaków.

 <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>Kontrolka ma również <xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType> Właściwość. Ta właściwość różni się od <xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType> właściwości, która jest dostępna we <xref:Microsoft.Office.Tools.Word.Bookmark.Range?displayProperty=nameWithType> właściwości <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> kontrolki lub <xref:Microsoft.Office.Interop.Word.Bookmark.Range?displayProperty=nameWithType> właściwości <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> obiektu.

|Właściwość Text|Opis|
|-------------------|-----------------|
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType>|Ta właściwość służy do wyświetlania tekstu w zakładce i pozostawiania zakładki w dokumencie. Przypisanie tekstu do zakładki rozszerza zakres zakładek i nie usuwa zakładki.<br /><br /> Na przykład `Bookmark1.Text = "Hello world"` wstawia tekst do zakładki i pozostawia zakładkę bez zmian.|
|<xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType>|Użyj tej właściwości, aby wyświetlić tekst w lokalizacji zakładki i automatycznie usunąć zakładkę. Na przykład `Bookmark1.Range.Text = "Hello world"` wstawia tekst do zakładki i usuwa zakładkę.|

## <a name="rename-the-control-at-design-time"></a>Zmień nazwę kontrolki w czasie projektowania
 W projektach na poziomie dokumentu, gdy przeciągasz <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolkę z **przybornika** do dokumentu, program Visual Studio automatycznie generuje nazwę formantu. Nazwę kontrolki można zmienić w oknie **Właściwości** .

## <a name="overlapping-controls"></a>Nakładające się kontrolki
 Kontrolki zakładki mogą nakładać się na siebie nawzajem. Ten sam tekst może być współużytkowany przez więcej niż jedną zakładkę. Po przypisaniu nowego tekstu do jednej z nakładających się zakładek zawiera on tylko nowy tekst, a zakładki nie nakładają się na siebie. Inna zakładka zawiera teraz tylko tekst, który nie został udostępniony między oryginalnymi nakładającymi się zakładkami.

 W poniższej tabeli pokazano, jak zdanie "to jest przykładowy tekst". jest współużytkowany przez dwie nakładające się zakładki:

|Zakładka|Tekst|
|--------------|----------|
|Nakładające się zakładki|[to jest tekst {Sample].}|
|Bookmark1|Jest to przykład|
|Bookmark2|Przykładowy tekst.|

 Jeśli przypiszesz nowy tekst "to jest zastąpienie". Aby Bookmark1, zakładki nie nakładają się, a Bookmark2 zachowuje tylko tekst, który nie był pierwotnie częścią Bookmark1.

|Zakładka|Tekst|
|--------------|----------|
|Dwie oddzielne zakładki|[to jest zastąpienie] {Text.}|
|Bookmark1|To zastępuje|
|Bookmark2|Opis.|

Jeśli zmienisz tekst zakładki zawierającej inną zakładkę, wewnętrzna zakładka nie zostanie usunięta. Jednak zakładka wewnętrzna staje się pustą zakładką i przechodzi do końca zakładki zewnętrznej.

W poniższej tabeli pokazano, jak zdanie "to jest przykładowy tekst". jest współużytkowany przez zakładkę, która jest zawarta w innej zakładki:

|Zakładka|Tekst|
|--------------|----------|
|Nakładające się zakładki|[to jest tekst {Sample}.]|
|Bookmark1|To jest przykładowy tekst.|
|Bookmark2|przykład|

 Jeśli przypiszesz nowy tekst "to jest zastąpienie". Aby Bookmark1, zakładki nie nakładają się na siebie, a Bookmark2 stają się pustą zakładką, która znajduje się na końcu Bookmark1.

|Zakładka|Tekst|
|--------------|----------|
|Dwie oddzielne zakładki|[to jest zastąpienie.]{}|
|Bookmark1|To zastępuje.|
|Bookmark2|*\<empty>*|

## <a name="events"></a>Zdarzenia

Dla kontrolki dostępne są następujące zdarzenia <xref:Microsoft.Office.Tools.Word.Bookmark> :

- <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>

- <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>

## <a name="see-also"></a>Zobacz też

- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Instrukcje: Dodawanie kontrolek zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Przewodnik: Tworzenie menu skrótów dla zakładek](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)