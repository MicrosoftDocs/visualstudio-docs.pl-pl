---
title: 'Instrukcje: Dodawanie niestandardowego okienka zadań do aplikacji'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 047728f00fae9dbf3cf2511300beaa84c2201cdd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039833"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>Instrukcje: Dodawanie niestandardowego okienka zadań do aplikacji
  Możesz dodawać niestandardowego okienka zadań do aplikacji z wymienionych powyżej, za pomocą dodatku narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [niestandardowych okienek zadań](../vsto/custom-task-panes.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="add-a-custom-task-pane-to-an-application"></a>Dodawanie niestandardowego okienka zadań do aplikacji

### <a name="to-add-a-custom-task-pane-to-an-application"></a>Dodawanie niestandardowego okienka zadań do aplikacji

1. Otwórz lub Utwórz projekt dodatku narzędzi VSTO dla jednej z aplikacji wymienionych powyżej. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Na **projektu** menu, kliknij przycisk **Dodaj kontrolkę użytkownika**.

3. W **Dodaj nowy element** okna dialogowego pole, Zmień nazwę nowej kontrolki użytkownika w celu **MyUserControl**, a następnie kliknij przycisk **Dodaj**.

     Formant użytkownika zostanie otwarty w projektancie.

4. Dodaj co najmniej jednej kontrolki Windows Forms z **przybornika** do kontrolki użytkownika.

5. Otwórz **ThisAddIn.cs** lub **ThisAddIn.vb** pliku kodu.

6. Dodaj następujący kod do `ThisAddIn` klasy. Ten kod deklaruje wystąpień `MyUserControl` i <xref:Microsoft.Office.Tools.CustomTaskPane> jako elementy członkowskie `ThisAddIn` klasy.

     [!code-vb[Trin_TaskPaneBasic#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#1)]
     [!code-csharp[Trin_TaskPaneBasic#1](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#1)]

7. Dodaj następujący kod do `ThisAddIn_Startup` programu obsługi zdarzeń. Ten kod tworzy nową <xref:Microsoft.Office.Tools.CustomTaskPane> , dodając `MyUserControl` obiekt `CustomTaskPanes` kolekcji. Kod jest również wyświetlane w okienku zadań.

     [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
     [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]

    > [!NOTE]
    >  Ten kod kojarzy niestandardowego okienka zadań z aktywnego okna aplikacji. W przypadku niektórych aplikacji można modyfikować ten kod, aby upewnić się, że w okienku zadań pojawia się z innych dokumentów lub elementów w aplikacji. Aby uzyskać więcej informacji, zobacz [niestandardowych okienek zadań](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Zobacz także
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)
- [Przewodnik: Automatyzacja aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
