---
title: 'How to: Add a custom task pane to an application (2. Tworzyć niestandardowe okienko zadań do aplikacji)'
description: Dowiedz się, jak dodać niestandardowe okienko zadań do aplikacji przy użyciu Visual Studio Tools dla pakietu Office (VSTO).
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d85edb9773783abe6282918c432fc1a4eff83944
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826723"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>How to: Add a custom task pane to an application (2. Tworzyć niestandardowe okienko zadań do aplikacji)
  Niestandardowe okienko zadań można dodać do aplikacji wymienionych powyżej przy użyciu dodatku narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [Niestandardowe okienka zadań.](../vsto/custom-task-panes.md)

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="add-a-custom-task-pane-to-an-application"></a>Dodawanie niestandardowego okienka zadań do aplikacji

### <a name="to-add-a-custom-task-pane-to-an-application"></a>Aby dodać niestandardowe okienko zadań do aplikacji

1. Otwórz lub utwórz projekt dodatku VSTO dla jednej z aplikacji wymienionych powyżej. Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. W menu **Project (Projekt)** kliknij pozycję **Add User Control (Dodaj kontrolkę użytkownika).**

3. W **oknie dialogowym Dodawanie** nowego elementu zmień nazwę nowej kontrolki użytkownika na **MyUserControl,** a następnie kliknij przycisk **Dodaj**.

     Kontrolka użytkownika zostanie otwarta w projektancie.

4. Dodaj co najmniej jedną kontrolkę Windows Forms z **przybornika** do kontrolki użytkownika.

5. Otwórz plik **kodu ThisAddIn.cs** lub **ThisAddIn.vb.**

6. Dodaj poniższy kod do klasy `ThisAddIn`. Ten kod deklaruje wystąpienia klas `MyUserControl` i <xref:Microsoft.Office.Tools.CustomTaskPane> jako składowe klasy `ThisAddIn` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs" id="Snippet1":::

7. Dodaj następujący kod do procedury `ThisAddIn_Startup` obsługi zdarzeń. Ten kod tworzy nowy <xref:Microsoft.Office.Tools.CustomTaskPane> przez dodanie obiektu do `MyUserControl` `CustomTaskPanes` kolekcji. Kod wyświetla również okienko zadań.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs" id="Snippet2":::

    > [!NOTE]
    > Ten kod kojarzy niestandardowe okienko zadań z aktywnym oknem w aplikacji. W przypadku niektórych aplikacji możesz zmodyfikować ten kod, aby upewnić się, że okienko zadań będzie wyświetlane z innymi dokumentami lub elementami w aplikacji. Aby uzyskać więcej informacji, zobacz [Niestandardowe okienka zadań.](../vsto/custom-task-panes.md)

## <a name="see-also"></a>Zobacz też
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)
- [Przewodnik: automatyzowanie aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
