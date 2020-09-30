---
title: Dostosowywanie funkcji interfejsu użytkownika przy użyciu interfejsów rozszerzalności
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], customizing
- application-level add-ins [Office development in Visual Studio], extensibility interfaces
- customizing UI features [Office development in Visual Studio]
- FormRegionStartup interface
- add-ins [Office development in Visual Studio], extensibility interfaces
- extensibility interfaces [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 07b62903388012dac3459c86011e349f8053762c
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583843"
---
# <a name="customize-ui-features-by-using-extensibility-interfaces"></a>Dostosowywanie funkcji interfejsu użytkownika przy użyciu interfejsów rozszerzalności
  Narzędzia programistyczne pakietu Office w programie Visual Studio udostępniają klasy i projektanci, którzy obsługują wiele szczegółów implementacji, gdy są używane do tworzenia niestandardowych okienek zadań, dostosowań Wstążki i regionów formularzy programu Outlook w dodatku VSTO. Można jednak również zaimplementować *interfejs rozszerzalności* dla każdej funkcji, jeśli masz specjalne wymagania.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="overview-of-extensibility-interfaces"></a>Omówienie interfejsów rozszerzalności
 Microsoft Office definiuje zestaw interfejsów rozszerzalności, które można zaimplementować dla dodatków VSTO COM, aby dostosować niektóre funkcje, takie jak Wstążka. Te interfejsy zapewniają pełną kontrolę nad funkcjami, do których mają dostęp. Jednak wdrożenie tych interfejsów wymaga pewnej znajomości współdziałania modelu COM w kodzie zarządzanym. W niektórych przypadkach model programowania tych interfejsów nie jest również intuicyjny dla deweloperów, którzy są przyzwyczajoni do .NET Framework.

 Podczas tworzenia dodatku narzędzi VSTO przy użyciu szablonów projektu pakietu Office w programie Visual Studio nie trzeba implementować interfejsów rozszerzalności, aby dostosować funkcje takie jak Wstążka. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Implementuje te interfejsy. Zamiast tego można użyć bardziej intuicyjnych klas i projektantów udostępnianych przez program Visual Studio. Jednak nadal można zaimplementować interfejsy rozszerzalności bezpośrednio w dodatku VSTO, jeśli chcesz.

 Aby uzyskać więcej informacji na temat klas i projektantów oferowanych przez program Visual Studio dla tych funkcji, zobacz [niestandardowe okienka zadań](../vsto/custom-task-panes.md), [Projektant wstążki](../vsto/ribbon-designer.md)i [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="extensibility-interfaces-you-can-implement-in-a-vsto-add-in"></a>Interfejsy rozszerzalności, które można zaimplementować w dodatku narzędzi VSTO
 W poniższej tabeli przedstawiono interfejsy rozszerzalności, które można zaimplementować, oraz aplikacje, które je obsługują.

|Interfejs|Opis|Aplikacje|
|---------------|-----------------|------------------|
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|Zaimplementuj ten interfejs, aby dostosować interfejs użytkownika wstążki. **Uwaga:**  Możesz dodać element **wstążki (XML)** do projektu, aby wygenerować domyślną <xref:Microsoft.Office.Core.IRibbonExtensibility> implementację w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [kod XML wstążki](../vsto/ribbon-xml.md).|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word|
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|Zaimplementuj ten interfejs, aby utworzyć niestandardowe okienko zadań.|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Zaimplementuj ten interfejs, aby utworzyć region formularza programu Outlook.|Outlook|

 Istnieje kilka innych interfejsów rozszerzalności zdefiniowanych przez Microsoft Office, takich jak <xref:Microsoft.Office.Core.IBlogExtensibility> , <xref:Microsoft.Office.Core.EncryptionProvider> , i <xref:Microsoft.Office.Core.SignatureProvider> . Program Visual Studio nie obsługuje implementowania tych interfejsów w dodatku VSTO utworzonym przy użyciu szablonów projektu pakietu Office.

## <a name="use-extensibility-interfaces"></a>Korzystanie z interfejsów rozszerzalności
 Aby dostosować funkcję interfejsu użytkownika przy użyciu interfejsu rozszerzalności, zaimplementuj odpowiedni interfejs w projekcie dodatku VSTO. Następnie zastąp <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metodę, aby zwrócić wystąpienie klasy, która implementuje interfejs.

 Aby uzyskać przykładową aplikację, która pokazuje, jak <xref:Microsoft.Office.Core.IRibbonExtensibility> zaimplementować <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> interfejsy, i <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> w dodatku narzędzi VSTO dla programu Outlook, zobacz przykład Menedżera interfejsu użytkownika w przykładach [deweloperskich pakietu Office](../vsto/office-development-samples.md).

### <a name="example-of-implementing-an-extensibility-interface"></a>Przykład implementacji interfejsu rozszerzalności
 Poniższy przykład kodu ilustruje prostą implementację <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> interfejsu w celu utworzenia niestandardowego okienka zadań. Ten przykład definiuje dwie klasy:

- `TaskPaneHelper`Klasa implementuje <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> Tworzenie i wyświetlanie niestandardowego okienka zadań.

- `TaskPaneUI`Klasa udostępnia interfejs użytkownika okienka zadań. Atrybuty `TaskPaneUI` klasy sprawiają, że Klasa jest widoczna dla modelu COM, co umożliwia aplikacjom Microsoft Office odnajdywanie klasy. W tym przykładzie interfejs użytkownika jest pusty <xref:System.Windows.Forms.UserControl> , ale można dodać kontrolki, modyfikując kod.

  > [!NOTE]
  > Aby uwidocznić `TaskPaneUI` klasę modelu COM, należy również ustawić właściwość **Zarejestruj dla międzyoperacyjności modelu COM** dla projektu.

  [!code-vb[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#1)]
  [!code-csharp[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#1)]

  Aby uzyskać więcej informacji na temat implementowania <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> , zobacz [Tworzenie niestandardowych okienek zadań w systemie 2007 pakietu Office](/previous-versions/office/developer/office-2007/aa338197(v=office.12)) w dokumentacji Microsoft Office.

### <a name="example-of-overriding-the-requestservice-method"></a>Przykład zastąpienia metody RequestService
 Poniższy przykład kodu demonstruje, jak zastąpić metodę, <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> Aby zwrócić wystąpienie `TaskPaneHelper` klasy z poprzedniego przykładu kodu. Sprawdza wartość parametru *serviceGuid* , aby określić, który interfejs jest żądany, a następnie zwraca obiekt, który implementuje ten interfejs.

 [!code-vb[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#2)]
 [!code-csharp[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#2)]

## <a name="see-also"></a>Zobacz też
- [Przykłady i przewodniki dotyczące programowania pakietu Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
