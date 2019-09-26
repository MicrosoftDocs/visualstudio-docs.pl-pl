---
title: 'Instrukcje: Zarządzanie układem kontrolek w okienkach akcji'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 043f93c12181d34e9d2a92435c854cdf76f18904
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255826"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Instrukcje: Zarządzanie układem kontrolek w okienkach akcji
  Okienko akcji jest domyślnie zadokowane po prawej stronie dokumentu lub arkusza; można go jednak zadokować do lewej, do góry lub do dołu. Jeśli używasz wielu kontrolek użytkownika, możesz napisać kod, aby prawidłowo ułożyć kontrolki użytkownika w okienku Akcje. Aby uzyskać więcej informacji, zobacz [Omówienie okienka Akcje](../vsto/actions-pane-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Kolejność stosu formantów zależy od tego, czy okienko akcje jest zadokowane w pionie czy w poziomie.

> [!NOTE]
> Jeśli użytkownik zmieni rozmiar okienka Akcje w czasie wykonywania, można ustawić kontrolki do zmiany rozmiaru w okienku Akcje. Za pomocą <xref:System.Windows.Forms.Control.Anchor%2A> właściwości kontrolki Windows Forms można zakotwiczyć kontrolki w okienku Akcje. Aby uzyskać więcej informacji, zobacz [jak: Kontrolki kotwicowe](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms)na Windows Forms.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Aby ustawić kolejność stosu formantów okienka Akcje

1. Otwórz projekt na poziomie dokumentu dla Microsoft Office Word, który zawiera okienko akcji z wieloma kontrolkami użytkownika lub okienkami zagnieżdżonych akcji. Aby uzyskać więcej informacji, zobacz [jak: Dodaj okienko akcji do dokumentów programu Word lub skoroszytów](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)programu Excel.

2. Kliknij prawym przyciskiem myszy pozycję **ThisDocument.cs** lub **ThisDocument. vb** w **Eksplorator rozwiązań** a następnie kliknij pozycję **Wyświetl kod**.

3. W procedurze obsługi zdarzeń okienka Akcje Sprawdź, czy orientacja okienka Akcje jest w poziomie. <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged>

     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]

4. Jeśli orientacja jest pozioma, Ułóż kontrolki okienka akcji z lewej strony; w przeciwnym razie ułóż je od góry.

     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]

5. W C#programie należy dodać procedurę obsługi `ActionsPane` <xref:Microsoft.Office.Tools.Word.Document.Startup> zdarzeń do programu obsługi zdarzeń. Aby uzyskać informacje na temat tworzenia programów obsługi zdarzeń [, zobacz How to: Tworzenie obsługi zdarzeń w projektach](../vsto/how-to-create-event-handlers-in-office-projects.md)pakietu Office.

     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]

6. Uruchom projekt i sprawdź, czy kontrolki okienka Akcje są ułożone w dół do prawej, gdy okienko akcje jest zadokowane u góry dokumentu, a kontrolki są układane od góry do dołu, gdy okienko akcje jest zadokowane po prawej stronie dokumentu.

## <a name="example"></a>Przykład
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]

## <a name="compile-the-code"></a>Skompilować kod
 Ten przykład wymaga:

- Projekt na poziomie dokumentu programu Word z okienkiem akcje zawierającym wiele kontrolek użytkownika lub okienka akcji zagnieżdżonych.

## <a name="see-also"></a>Zobacz także
- [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)
- [Instrukcje: Dodawanie okienka akcji do dokumentów programu Word lub skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Instrukcje: Dodawanie okienka akcji do dokumentów programu Word lub skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Przewodnik: Wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Przewodnik: Wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
