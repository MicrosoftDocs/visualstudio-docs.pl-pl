---
title: 'Instrukcje: ukrywanie kontrolek w arkuszach podczas drukowania'
description: Dowiedz się, czy podczas drukowania Microsoft Office arkusza programu Excel, który zawiera kontrolki Windows Forms, można ukryć kontrolki.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: acc90986dd394e69de12893aac01e0a4f662b1a3
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846496"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Instrukcje: ukrywanie kontrolek w arkuszach podczas drukowania
  Podczas drukowania Microsoft Office dokumentu programu Excel, który zawiera kontrolki Windows Forms, formanty są widoczne w arkuszu wydrukowanym. Kontrolki można ukryć podczas drukowania arkusza.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Jeśli ukryjesz kontrolki, które wyświetlają dane, takie jak <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> , dane w kontrolce nie będą widoczne w drukowanym arkuszu.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Aby ukryć kontrolki podczas drukowania arkusza

1. Utwórz lub Otwórz projekt programu Excel w programie Visual Studio i sprawdź, czy na **arkuszu Arkusz1** jest widoczny w projektancie. Aby uzyskać informacje na temat tworzenia projektów, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Na karcie **Formanty standardowe** **przybornika** przeciągnij <xref:Microsoft.Office.Tools.Excel.Controls.Button> kontrolkę do komórki na `Sheet1` .

3. W oknie **Właściwości** Ustaw <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> Właściwość na **false**.

## <a name="see-also"></a>Zobacz także
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Kontrolki Windows Forms w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Instrukcje: Dodawanie formantów Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Instrukcje: zmiana rozmiaru kontrolek w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md)
