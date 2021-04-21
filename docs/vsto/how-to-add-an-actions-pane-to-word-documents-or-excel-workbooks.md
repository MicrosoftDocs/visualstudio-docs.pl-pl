---
title: Dodawanie okienka Akcje do dokumentów programu Word lub skoroszytów programu Excel
description: Aby dodać okienko akcji do dokumentu programu Microsoft Office Word lub skoroszytu programu Microsoft Excel, należy najpierw utworzyć Windows Forms użytkownika.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9cf079727581b9cec4b6cb77a0a0c3f0b503b3a0
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825527"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Porady: dodawanie okienek akcji do dokumentów programu Word lub arkuszy programu Excel
  Aby dodać okienko akcji do Microsoft Office programu Word lub skoroszytu programu Microsoft Excel, najpierw utwórz Windows Forms użytkownika. Następnie dodaj kontrolkę użytkownika do właściwości <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> pola `ThisDocument.ActionsPane` (Word) lub pola `ThisWorkbook.ActionsPane` (Excel) w projekcie.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="creating-the-user-control"></a>Tworzenie kontrolki użytkownika
 W poniższej procedurze pokazano, jak utworzyć kontrolkę użytkownika w projekcie programu Word lub Excel. Dodaje również przycisk do kontrolki użytkownika, który zapisuje tekst w dokumencie lub skoroszycie po jego kliknięciu.

#### <a name="to-create-the-user-control"></a>Aby utworzyć kontrolkę użytkownika

1. Otwórz projekt programu Word lub Excel na poziomie dokumentu w Visual Studio.

2. W menu **Project (Projekt)** kliknij pozycję **Add New Item (Dodaj nowy element).**

3. W **oknie dialogowym Dodawanie nowego** elementu wybierz pozycję **Kontrolka okienka Akcje,** nadaj jej **nazwę HelloControl** i kliknij przycisk **Dodaj**.

    > [!NOTE]
    > Możesz też dodać element **Kontrola użytkownika** do projektu. Klasy generowane przez kontrolkę okienka **akcji i** elementy **kontrolki** użytkownika są funkcjonalnie równoważne.

4. Z **Windows Forms** **przybornika** przeciągnij kontrolkę **Przycisk** na kontrolkę.

    > [!NOTE]
    > Jeśli kontrolka nie jest widoczna w projektancie, kliknij dwukrotnie **kontrolkę HelloControl** **w Eksplorator rozwiązań**.

5. Dodaj kod do <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń przycisku. W poniższym przykładzie pokazano kod dla Microsoft Office programu Word.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb" id="Snippet12":::

6. W języku C# należy dodać program obsługi zdarzeń dla kliknięcia przycisku. Ten kod można umieścić w `HelloControl` konstruktorze po wywołaniu klasy `InitializeComponent` .

     Aby uzyskać informacje na temat tworzenia programów obsługi zdarzeń, zobacz [Jak utworzyć procedury obsługi zdarzeń w projektach pakietu Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs" id="Snippet13":::

## <a name="add-the-user-control-to-the-actions-pane"></a>Dodawanie kontrolki użytkownika do okienka akcji
 Aby wyświetlić okienko akcji, dodaj kontrolkę użytkownika do właściwości <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> pola `ThisDocument.ActionsPane` (Word) lub `ThisWorkbook.ActionsPane` pola (Excel).

### <a name="to-add-the-user-control-to-the-actions-pane"></a>Aby dodać kontrolkę użytkownika do okienka akcji

1. Dodaj następujący kod do klasy lub jako deklarację na poziomie klasy `ThisDocument` `ThisWorkbook` (nie dodawaj tego kodu do metody).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet14":::

2. Dodaj następujący kod do programu `ThisDocument_Startup` obsługi zdarzeń klasy lub programu obsługi zdarzeń klasy `ThisDocument` `ThisWorkbook_Startup` `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet15":::

## <a name="see-also"></a>Zobacz też
- [Omówienie okienka Akcje](../vsto/actions-pane-overview.md)
- [Przewodnik: wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [How to: Manage control layout on actions panes (Jak zarządzać układem kontrolek w okienkach akcji)](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Przewodnik: wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
