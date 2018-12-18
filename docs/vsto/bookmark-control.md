---
title: 'Bookmark, formant:'
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 242a4692bc75715e661244dc8f513d30cc9480ed
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248195"
---
# <a name="bookmark-control"></a>Bookmark, formant:
  <xref:Microsoft.Office.Tools.Word.Bookmark> Formant jest zakładki, która ma unikatową nazwę, udostępnia zdarzenia i może być powiązana z danymi. Zakładka może służyć jako symbol zastępczy, aby oznaczyć element lub lokalizacji w dokumencie programu Microsoft Office Word. <xref:Microsoft.Office.Tools.Word.Bookmark> Kontroli jest kombinacją <xref:Microsoft.Office.Interop.Word.Bookmark> obiektu i <xref:Microsoft.Office.Interop.Word.Range> obiektu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 W projektach na poziomie dokumentu, można dodać <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki do dokumentu w czasie projektowania lub w czasie wykonywania. W projektach dodatku narzędzi VSTO dla programów, można dodać <xref:Microsoft.Office.Tools.Word.Bookmark> formantów dowolnego otwartego dokumentu w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie formantów zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

## <a name="bind-data-to-the-control"></a>Wiązanie danych do kontrolki
 A <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolka obsługuje proste powiązanie danych. Zakładki ma zostać powiązana z źródła danych przy użyciu <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> właściwości. Domyślna właściwość powiązania danych zakładka jest <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> właściwości.

 Jeśli dane w powiązanej zestaw danych zostanie zaktualizowane, <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolka pokazuje zmiany.

 W projektach na poziomie dokumentu, możesz również powiązać dane do zakładek przy użyciu **źródeł danych** okna. Aby uzyskać więcej informacji, zobacz [jak: Zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md).

## <a name="formatting"></a>Formatowanie
 Formatowanie, które mogą być stosowane do <xref:Microsoft.Office.Interop.Word.Bookmark> mogą być stosowane do <xref:Microsoft.Office.Tools.Word.Bookmark> kontroli. To formatowanie obejmuje czcionek, wcięć, odstępów, numerowanie i stylów.

## <a name="assign-text-to-the-bookmark"></a>Przypisywanie tekstu do zakładki
 Dodatkowe różnicy <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> obiektu i <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> formant jest, jak działa, jeśli tekst jest przypisana do zakładki. Jeśli tekst jest przypisana do zerowej długości <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType>, tekst jest dołączany po prawej stronie zakładka i Zakładka pozostanie o zerowej długości. Jednak jeśli tekst jest przypisana do zerowej długości <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>, tekst jest wstawiany do zakładki, a długość zakładki rozszerza całkowitą liczbę znaków wstawiony.

 <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> Kontroli ma również <xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType> właściwości. Ta właściwość jest inny niż <xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType> właściwość, która jest dostępna w <xref:Microsoft.Office.Tools.Word.Bookmark.Range?displayProperty=nameWithType> właściwość <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> kontroli, lub <xref:Microsoft.Office.Interop.Word.Bookmark.Range?displayProperty=nameWithType> właściwość <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> obiektu.

|Właściwość Text|Opis|
|-------------------|-----------------|
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType>|Ta właściwość służy do wyświetlania tekstu w zakładce i pozostawić zakładki w dokumencie. Przypisywanie tekstu do zakładki rozszerza zakres zakładki i nie powoduje usunięcia zakładki.<br /><br /> Na przykład `Bookmark1.Text = "Hello world"` wstawia tekst do zakładki i pozostawia zakładki bez zmian.|
|<xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType>|Ta właściwość służy do wyświetlania tekstu w lokalizacji zakładki i automatycznie usunąć zakładki. Na przykład `Bookmark1.Range.Text = "Hello world"` wstawia tekst do zakładki, a następnie usuwa zakładki.|

## <a name="rename-the-control-at-design-time"></a>Zmień nazwę kontrolki w czasie projektowania
 W przypadku projektów na poziomie dokumentu, podczas przeciągania <xref:Microsoft.Office.Tools.Word.Bookmark> z kontrolować **przybornika** do dokumentu, program Visual Studio automatycznie generuje nazwę dla formantu. Możesz zmienić nazwę kontrolki **właściwości** okna.

## <a name="overlapping-controls"></a>Nakładanie się formantów
 Formanty zakładek może nakładać się na siebie nawzajem. Ten sam tekst mogą być współdzielone przez więcej niż jedną zakładkę. Po przypisaniu nowego tekstu do jednego z nakładającymi się zakładki zawiera nowy tekst i zakładki nie nakładają się na siebie. Inne zakładki teraz zawiera tylko tekst, który nie został udostępniony między oryginalnego zakładkami nakładających się.

 W poniższej tabeli przedstawiono, jak zdania "To jest tekst przykładowy." jest współużytkowana przez dwie nakładające się zakładek:

|Zakładka|Tekst|
|--------------|----------|
|Nakładające się zakładki|[to jest przykładowy {] tekst.}|
|Bookmark1|To jest przykładowy|
|Bookmark2|Przykładowy tekst.|

 Jeśli przypiszesz nowy tekst "Jest zastąpienie". Aby Bookmark1 zakładki nie nakładają się i Bookmark2 zachowuje tylko tekst, który nie został pierwotnie część Bookmark1.

|Zakładka|Tekst|
|--------------|----------|
|Dwa oddzielne zakładki|[to jest zastąpienie] {tekst}.|
|Bookmark1|To zastąpienie|
|Bookmark2|Tekst.|

W przypadku zmiany tekstu zakładki, która zawiera inny zakładki wewnętrzny zakładki nie jest usuwany. Jednak wewnętrzny zakładki staje się puste zakładki i przenosi do końca zakładki zewnętrzne.

W poniższej tabeli przedstawiono, jak zdania "To jest tekst przykładowy." jest współużytkowany przez zakładki, która znajduje się w innym zakładkę:

|Zakładka|Tekst|
|--------------|----------|
|Nakładające się zakładki|[to jest tekst {przykładowy}].|
|Bookmark1|To jest tekst przykładowy.|
|Bookmark2|przykład|

 Jeśli przypiszesz nowy tekst "Jest zastąpienie". Aby Bookmark1 już nie nakładają się na zakładki, a następnie Bookmark2 staje się puste zakładki, która znajduje się na końcu Bookmark1.

|Zakładka|Tekst|
|--------------|----------|
|Dwa oddzielne zakładki|[to jest zastąpienie.]{}|
|Bookmark1|To zastąpienie.|
|Bookmark2|*\<pusty >*|

## <a name="events"></a>Zdarzenia

Następujące zdarzenia są dostępne dla <xref:Microsoft.Office.Tools.Word.Bookmark> sterowania:

-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>

-   <xref:System.ComponentModel.IComponent.Disposed>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>

## <a name="see-also"></a>Zobacz także

- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Instrukcje: Dodawanie formantów zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Wskazówki: Tworzenie menu skrótów dla zakładek](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)