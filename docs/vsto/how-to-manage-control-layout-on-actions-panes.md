---
title: 'How to: Manage control layout on actions panes (Jak zarządzać układem kontrolek w okienkach akcji)'
description: Dowiedz się, jak zarządzać układem kontrolek w okienkach akcji, pisząc kod do prawidłowego stosu kontrolek użytkownika.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 182dee248f161f3dde721c50ee996d6f621dd9af
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827451"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>How to: Manage control layout on actions panes (Jak zarządzać układem kontrolek w okienkach akcji)
  Okienko akcji jest domyślnie zadokowane po prawej stronie dokumentu lub arkusza. Można go jednak zadokować do lewej, górnej lub dolnej części. Jeśli używasz wielu kontrolek użytkownika, możesz napisać kod w celu prawidłowego napisania stosu kontrolek użytkownika w okienku akcji. Aby uzyskać więcej informacji, zobacz [Omówienie okienka Akcje](../vsto/actions-pane-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Kolejność stosu kontrolek zależy od tego, czy okienko akcji jest zadokowane w pionie, czy w poziomie.

> [!NOTE]
> Jeśli użytkownik zmieni rozmiar okienka akcji w czasie działania, możesz ustawić rozmiar kontrolek w okienku akcji. Możesz użyć właściwości <xref:System.Windows.Forms.Control.Anchor%2A> kontrolki Windows Forms do zakotwiczenia kontrolek w okienku akcji. Aby uzyskać więcej informacji, zobacz How to: Anchor controls on Windows Forms ( Jak [zakotwiczyć kontrolki na Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms)).

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Aby ustawić kolejność stosu kontrolek okienka akcji

1. Otwórz projekt na poziomie dokumentu dla programu Microsoft Office Word, który zawiera okienko akcji z wieloma kontrolkami użytkownika lub zagnieżdżone kontrolki okienka akcji. Aby uzyskać więcej informacji, zobacz [Jak dodać okienko akcji do dokumentów programu Word lub skoroszytów programu Excel.](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)

2. Kliknij prawym przyciskiem **myszy pozycję ThisDocument.cs** lub **ThisDocument.vb** Eksplorator rozwiązań **a** następnie kliknij pozycję **Wyświetl kod**.

3. W <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> programie obsługi zdarzeń okienka akcji sprawdź, czy orientacja okienka akcji jest pozioma.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet30":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet30":::

4. Jeśli orientacja jest pozioma, stosuj kontrolki okienka akcji od lewej strony. W przeciwnym razie ułóż je od góry.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet31":::

5. W języku C# należy dodać program obsługi zdarzeń dla programu `ActionsPane` do programu <xref:Microsoft.Office.Tools.Word.Document.Startup> obsługi zdarzeń. Aby uzyskać informacje na temat tworzenia programów obsługi zdarzeń, zobacz [Jak tworzyć procedury obsługi zdarzeń w projektach pakietu Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet32":::

6. Uruchom projekt i sprawdź, czy kontrolki okienka akcji są skumulowane od lewej do prawej, gdy okienko akcji jest zadokowane w górnej części dokumentu, a kontrolki są ułożone od góry do dołu, gdy okienko akcji jest zadokowane po prawej stronie dokumentu.

## <a name="example"></a>Przykład
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet29":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet29":::

## <a name="compile-the-code"></a>Kompilowanie kodu
 Ten przykład wymaga:

- Projekt na poziomie dokumentu programu Word z okienkiem akcji zawierającym wiele kontrolek użytkownika lub zagnieżdżonych kontrolek okienka akcji.

## <a name="see-also"></a>Zobacz też
- [Omówienie okienka Akcje](../vsto/actions-pane-overview.md)
- [How to: Add an actions pane to Word documents or Excel workbooks (Jak dodać okienko akcji do dokumentów programu Word lub skoroszytów programu Excel)](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [How to: Add an actions Pane to Word Documents or Excel workbooks (Jak dodać okienko akcji do dokumentów programu Word lub skoroszytów programu Excel)](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Przewodnik: wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Przewodnik: wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
