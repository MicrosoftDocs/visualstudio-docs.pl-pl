---
title: 'How to: Add Bookmark controls to Word documents (Jak dodać kontrolki zakładek do dokumentów programu Word)'
description: Dowiedz się, że w projektach na poziomie dokumentu możesz dodać kontrolki zakładki do dokumentu w projekcie w czasie projektowania lub w czasie uruchamiania.
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VST.Bookmark.Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Bookmark control, adding to documents
- Create Bookmark Control dialog box
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0a5520582db9919417b1c70d773355901ac0b0a5
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826606"
---
# <a name="how-to-add-bookmark-controls-to-word-documents"></a>How to: Add Bookmark controls to Word documents (Jak dodać kontrolki zakładek do dokumentów programu Word)
  W projektach na poziomie dokumentu można dodawać kontrolki do dokumentu w projekcie w <xref:Microsoft.Office.Tools.Word.Bookmark> czasie projektowania lub w czasie uruchamiania. W projektach dodatków VSTO można dodawać kontrolki <xref:Microsoft.Office.Tools.Word.Bookmark> do dowolnego otwartego dokumentu w czasie uruchamiania.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 W tym temacie opisano następujące zadania:

- [Dodawanie kontrolek zakładki w czasie projektowania](#designtime)

- [Dodawanie kontrolek zakładki w czasie uruchamiania w projekcie na poziomie dokumentu](#runtimedoclevel)

- [Dodawanie kontrolek zakładki w czasie uruchamiania w projekcie dodatku VSTO](#runtimeaddin)

  Aby uzyskać więcej informacji na temat <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolek, zobacz [Kontrolka zakładki](../vsto/bookmark-control.md).

## <a name="add-bookmark-controls-at-design-time"></a><a name="designtime"></a> Dodawanie kontrolek zakładki w czasie projektowania
 Istnieje kilka sposobów dodawania <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolek do dokumentu w projekcie na poziomie dokumentu w czasie projektowania:

- W przyborniku **Visual Studio narzędzi .**

   Możesz przeciągnąć <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolkę z **przybornika** do dokumentu. Możesz wybrać tę opcję, jeśli używasz  już przybornika do dodawania kontrolek Windows Forms do dokumentu.

- Z poziomu programu Word.

   Kontrolkę można dodać do dokumentu w taki sam sposób, jak w <xref:Microsoft.Office.Tools.Word.Bookmark> przypadku dodania zakładki natywnej. Zaletą dodania jej w ten sposób jest możliwość nadawania nazwy kontrolce podczas jej tworzenia.

- W **oknie Źródła** danych.

   Kontrolkę można <xref:Microsoft.Office.Tools.Word.Bookmark> przeciągnąć do dokumentu z okna **Źródła** danych. Jest to przydatne, gdy chcesz powiązać kontrolkę z danymi w tym samym czasie. Kontrolkę hosta można dodać w taki sam sposób, jak kontrolkę Formularz systemu Windows z okna **Źródła** danych. Aby uzyskać więcej informacji, zobacz [Powiązanie danych i Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

#### <a name="to-add-a-bookmark-control-to-a-document-from-the-toolbox"></a>Aby dodać kontrolkę Zakładka do dokumentu z przybornika

1. Otwórz **przybornik i** kliknij **kartę Kontrolki** wyrazów.

2. Przeciągnij <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolkę do dokumentu.

     Zostanie **wyświetlone okno dialogowe Dodawanie** zakładki.

3. Wybierz tekst lub inne elementy, które chcesz dołączyć do zakładki.

4. Kliknij przycisk **OK**.

     Jeśli nie chcesz zachować domyślnej nazwy zakładki, możesz zmienić nazwę w **oknie** Właściwości.

#### <a name="to-add-a-bookmark-control-to-a-document-in-word"></a>Aby dodać kontrolkę Zakładka do dokumentu w programie Word

1. W dokumencie hostowany w projektancie umieść kursor w miejscu, w którym chcesz dodać zakładkę, lub wybierz tekst, który ma zostać ujęty [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] w zakładkę.

2. Na karcie **Wstawianie** wstążki w grupie **Linki** kliknij przycisk **Zakładka.**

3. W **oknie** dialogowym Zakładka wpisz nazwę nowej zakładki, a następnie kliknij przycisk **Dodaj**.

## <a name="add-bookmark-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Dodawanie kontrolek zakładki w czasie uruchamiania w projekcie na poziomie dokumentu
 Kontrolki można dodawać programowo do dokumentu w czasie działania przy użyciu metod właściwości <xref:Microsoft.Office.Tools.Word.Bookmark> <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> klasy w `ThisDocument` projekcie. Istnieją dwa przeciążenia metod, których można użyć do dodania <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki w następujący sposób:

- Dodaj <xref:Microsoft.Office.Tools.Word.Bookmark> wartość w określonym zakresie.

- Dodaj w dokumencie zakładkę opartą na <xref:Microsoft.Office.Tools.Word.Bookmark> zakładce natywnej (czyli <xref:Microsoft.Office.Interop.Word.Bookmark> ).

  Dynamicznie tworzone <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki nie są utrwalane w dokumencie po zamknięciu dokumentu. Jednak w dokumencie <xref:Microsoft.Office.Interop.Word.Bookmark> pozostaje natywna. Przy następnym otwarciu dokumentu można ponownie utworzyć zakładkę opartą na <xref:Microsoft.Office.Tools.Word.Bookmark> zakładce natywnej. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie rzeczywistym.](../vsto/adding-controls-to-office-documents-at-run-time.md)

#### <a name="to-add-a-bookmark-control-to-a-document-programmatically"></a>Aby programowo dodać kontrolkę Zakładka do dokumentu

1. W programie obsługi zdarzeń w projekcie wstaw następujący kod, aby dodać kontrolkę do `ThisDocument_Startup` <xref:Microsoft.Office.Tools.Word.Bookmark> pierwszego akapitu w dokumencie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb" id="Snippet1":::

    > [!NOTE]
    > Jeśli chcesz utworzyć <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolkę z istniejącej <xref:Microsoft.Office.Interop.Word.Bookmark> kontrolki , użyj metody i przekaż <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> istniejący element <xref:Microsoft.Office.Interop.Word.Bookmark> .

## <a name="add-bookmark-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Dodawanie kontrolek zakładki w czasie uruchamiania w projekcie dodatku VSTO
 Kontrolki można dodać programowo do dowolnego otwartego dokumentu w czasie <xref:Microsoft.Office.Tools.Word.Bookmark> uruchamiania za pomocą dodatku VSTO. W tym celu wygeneruj element hosta oparty na otwartym dokumencie, a następnie użyj metod właściwości <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> tego elementu hosta. Istnieją dwa przeciążenia metod, których można użyć, aby dodać <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolkę w następujący sposób:

- Dodaj <xref:Microsoft.Office.Tools.Word.Bookmark> wartość w określonym zakresie.

- Dodaj w dokumencie zakładkę opartą na <xref:Microsoft.Office.Tools.Word.Bookmark> zakładce natywnej (czyli <xref:Microsoft.Office.Interop.Word.Bookmark> ).

  Dynamicznie tworzone <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki nie są utrwalane w dokumencie po zamknięciu dokumentu. Jednak w dokumencie <xref:Microsoft.Office.Interop.Word.Bookmark> pozostaje natywna. Przy następnym otwarciu dokumentu można ponownie utworzyć zakładkę opartą na <xref:Microsoft.Office.Tools.Word.Bookmark> zakładce natywnej. Aby uzyskać więcej informacji, zobacz [Utrwalanie kontrolek dynamicznych w dokumentach pakietu Office.](../vsto/persisting-dynamic-controls-in-office-documents.md)

  Aby uzyskać więcej informacji na temat generowania elementów hosta w projektach dodatków VSTO, zobacz Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w [czasie uruchamiania.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

#### <a name="to-add-a-bookmark-control-at-a-specified-range"></a>Aby dodać kontrolkę Zakładka w określonym zakresie

1. Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> metody i przekaż do miejsca, <xref:Microsoft.Office.Interop.Word.Range> w którym chcesz dodać . <xref:Microsoft.Office.Tools.Word.Bookmark>

     Poniższy przykład kodu dodaje nowy <xref:Microsoft.Office.Tools.Word.Bookmark> na początku aktywnego dokumentu. Aby użyć tego przykładu, uruchom kod z procedury obsługi `ThisAddIn_Startup` zdarzeń w projekcie dodatku Word VSTO.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet4":::

#### <a name="to-add-a-bookmark-control-that-is-based-on-a-native-bookmark-control"></a>Aby dodać kontrolkę Zakładka opartą na natywnej kontrolce Zakładka

1. Użyj metody i przekaż istniejącą, której chcesz użyć jako <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> <xref:Microsoft.Office.Interop.Word.Bookmark> podstawy dla nowego . <xref:Microsoft.Office.Tools.Word.Bookmark>

     Poniższy przykład kodu tworzy nową, <xref:Microsoft.Office.Tools.Word.Bookmark> która jest oparta na pierwszym w aktywnym <xref:Microsoft.Office.Interop.Word.Bookmark> dokumencie. Aby użyć tego przykładu, uruchom kod z programu obsługi `ThisAddIn_Startup` zdarzeń w projekcie dodatku Word VSTO.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet5":::

## <a name="see-also"></a>Zobacz też
- [Automatyzowanie programu Word przy użyciu obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie uruchamiania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md)
- [Zaprogramowanie dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)
- [Jak zmienić rozmiar kontrolek zakładki](../vsto/how-to-resize-bookmark-controls.md)
