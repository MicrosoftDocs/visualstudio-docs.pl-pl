---
title: 'Instrukcje: Zarządzanie układem formantu w okienkach akcji'
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
ms.openlocfilehash: 94e3ccc30507ccd7995c4d4fad548fe5ff425365
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60094615"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Instrukcje: Zarządzanie układem formantu w okienkach akcji
  Okienka akcji jest zadokowany po prawej stronie dokument lub skoroszyt, domyślnie; jednak może być zadokowane po lewej stronie, w górę lub w dół. Jeśli używasz wielu kontrolek użytkownika, można napisać kod, aby prawidłowo stosu kontrolki użytkownika w okienku akcji. Aby uzyskać więcej informacji, zobacz [okienko akcji ― omówienie](../vsto/actions-pane-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Kolejność stosu formantów zależy od tego, czy w okienku Akcje jest zadokowany w pionie lub poziomie.

> [!NOTE]
>  Jeśli użytkownik zmieni rozmiar okienka Akcje w czasie wykonywania, można ustawić formanty zmiany rozmiaru za pomocą okienka działań. Możesz użyć <xref:System.Windows.Forms.Control.Anchor%2A> właściwości formantu Windows Forms z kontrolkami zakotwiczenia w okienku Akcje. Aby uzyskać więcej informacji, zobacz [jak: Kotwiczenie formantów na formularzach Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).

> [!NOTE]
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Aby ustawić kolejność stosu kontrolki okienka akcji

1. Otwórz projekt poziomie dokumentu dla programu Microsoft Office Word zawiera okienka akcji przy użyciu wielu kontrolek użytkownika lub kontrolki okienka akcji zagnieżdżonych. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie okienek akcji do dokumentów programu Word i skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

2. Kliknij prawym przyciskiem myszy **ThisDocument.cs** lub **ThisDocument.vb** w **Eksploratora rozwiązań** a następnie kliknij przycisk **Wyświetl kod**.

3. W <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> program obsługi zdarzeń w okienku Akcje, sprawdź, czy orientację w okienku Akcje jest poziomy.

     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]

4. W przypadku orientacji poziomej stosu kontrolki okienka akcji z lewej strony; w przeciwnym razie stosu ich z góry.

     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]

5. W C#, należy dodać program obsługi zdarzeń dla `ActionsPane` do <xref:Microsoft.Office.Tools.Word.Document.Startup> programu obsługi zdarzeń. Aby dowiedzieć się, jak tworzenie procedur obsługi zdarzeń, zobacz [jak: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]

6. Uruchom projekt i sprawdź, kontrolki okienka akcji są ułożone od lewej do prawej w okienku Akcje jest zadokowany w górnej części dokumentu, gdy formanty są ułożone od góry do dołu, gdy jest zadokowany w okienku Akcje, po prawej stronie dokumentu.

## <a name="example"></a>Przykład
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]

## <a name="compile-the-code"></a>Skompilować kod
 Ten przykład wymaga:

- Określa projekt poziomu dokumentu programu Word z okienka akcji, która zawiera wiele kontrolek użytkownika lub w okienku Akcje zagnieżdżonych.

## <a name="see-also"></a>Zobacz także
- [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)
- [Instrukcje: Dodawanie okienek akcji do dokumentów programu Word lub arkuszy programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Instrukcje: Dodaj okienko akcji do dokumentów programu Word lub Excel skoroszytów](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Przewodnik: Wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Przewodnik: Wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
