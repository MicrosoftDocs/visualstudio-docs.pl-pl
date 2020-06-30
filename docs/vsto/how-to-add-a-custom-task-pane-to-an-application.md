---
title: 'Instrukcje: Dodawanie niestandardowego okienka zadań do aplikacji'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], adding to application
- custom task panes [Office development in Visual Studio], adding to application
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0df4d51795f01c98790f1d5b0525c45cc71899ab
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546214"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>Instrukcje: Dodawanie niestandardowego okienka zadań do aplikacji
  Możesz dodać niestandardowe okienko zadań do aplikacji wymienionych powyżej przy użyciu dodatku VSTO. Aby uzyskać więcej informacji, zobacz [niestandardowe okienka zadań](../vsto/custom-task-panes.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="add-a-custom-task-pane-to-an-application"></a>Dodawanie niestandardowego okienka zadań do aplikacji

### <a name="to-add-a-custom-task-pane-to-an-application"></a>Aby dodać niestandardowe okienko zadań do aplikacji

1. Otwórz lub Utwórz projekt dodatku VSTO dla jednej z aplikacji wymienionych powyżej. Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. W menu **projekt** kliknij polecenie **Dodaj kontrolkę użytkownika**.

3. W oknie dialogowym **Dodaj nowy element** Zmień nazwę nowego formantu użytkownika na **UserControl**, a następnie kliknij przycisk **Dodaj**.

     Formant użytkownika zostanie otwarty w projektancie.

4. Dodaj co najmniej jedną kontrolkę Windows Forms z **przybornika** do kontrolki użytkownika.

5. Otwórz plik kodu **ThisAddIn.cs** lub **ThisAddIn. vb** .

6. Dodaj następujący kod do `ThisAddIn` klasy. Ten kod deklaruje wystąpienia `MyUserControl` <xref:Microsoft.Office.Tools.CustomTaskPane> elementów i jako elementy członkowskie `ThisAddIn` klasy.

     [!code-vb[Trin_TaskPaneBasic#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#1)]
     [!code-csharp[Trin_TaskPaneBasic#1](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#1)]

7. Dodaj następujący kod do `ThisAddIn_Startup` programu obsługi zdarzeń. Ten kod tworzy nowe <xref:Microsoft.Office.Tools.CustomTaskPane> przez dodanie `MyUserControl` obiektu do `CustomTaskPanes` kolekcji. Kod wyświetla również okienko zadań.

     [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
     [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]

    > [!NOTE]
    > Ten kod kojarzy niestandardowe okienko zadań z aktywnym oknem w aplikacji. W przypadku niektórych aplikacji można zmodyfikować ten kod, aby upewnić się, że okienko zadań pojawia się z innymi dokumentami lub elementami w aplikacji. Aby uzyskać więcej informacji, zobacz [niestandardowe okienka zadań](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Zobacz też
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)
- [Przewodnik: Automatyzowanie aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
