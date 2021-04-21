---
title: Dostosowywanie funkcji interfejsu użytkownika przy użyciu interfejsów rozszerzalności
description: Dowiedz się, że narzędzia programistyczne pakietu Office Visual Studio interfejsy rozszerzalności, które ułatwiają dostosowywanie funkcji interfejsu użytkownika.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 86f4e5f286d817fb3f657e40399eccd3a2b4de73
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828036"
---
# <a name="customize-ui-features-by-using-extensibility-interfaces"></a>Dostosowywanie funkcji interfejsu użytkownika przy użyciu interfejsów rozszerzalności
  Narzędzia deweloperskie pakietu Office w programie Visual Studio oferują klasy i projektantów, które obsługują wiele szczegółów implementacji, gdy są one potrzebne do tworzenia niestandardowych okienek zadań, dostosowań wstążki i regionów formularzy programu Outlook w dodatku narzędzi VSTO. Można jednak również samodzielnie zaimplementować *interfejs* rozszerzalności dla każdej funkcji, jeśli masz specjalne wymagania.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="overview-of-extensibility-interfaces"></a>Omówienie interfejsów rozszerzalności
 Microsoft Office definiuje zestaw interfejsów rozszerzalności, które dodatki COM VSTO można zaimplementować w celu dostosowania niektórych funkcji, takich jak wstążka. Te interfejsy zapewniają pełną kontrolę nad funkcjami, do których zapewniają dostęp. Jednak implementacja tych interfejsów wymaga znajomości współdziałania com w kodzie zarządzanym. W niektórych przypadkach model programowania tych interfejsów nie jest również intuicyjny dla deweloperów, którzy są przywykli do .NET Framework.

 Podczas tworzenia dodatku VSTO przy użyciu szablonów projektów pakietu Office w programie Visual Studio nie trzeba implementować interfejsów rozszerzalności w celu dostosowania funkcji, takich jak wstążka. Interfejs [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] implementuje te interfejsy za Ciebie. Zamiast tego można używać bardziej intuicyjnych klas i projektantów dostarczanych przez Visual Studio. Można jednak nadal implementować interfejsy rozszerzalności bezpośrednio w dodatku VSTO, jeśli chcesz.

 Aby uzyskać więcej informacji na temat klas i projektantów, które Visual Studio dla tych funkcji, zobacz Niestandardowe okienka [zadań,](../vsto/custom-task-panes.md)Projektant [wstążki](../vsto/ribbon-designer.md)i Tworzenie regionów [formularzy programu Outlook.](../vsto/creating-outlook-form-regions.md)

## <a name="extensibility-interfaces-you-can-implement-in-a-vsto-add-in"></a>Interfejsy rozszerzalności, które można zaimplementować w dodatku VSTO
 W poniższej tabeli wymieniono interfejsy rozszerzalności, które można zaimplementować, oraz aplikacje, które je obsługują.

|Interfejs|Opis|Aplikacje|
|---------------|-----------------|------------------|
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|Zaim implementuj ten interfejs, aby dostosować interfejs użytkownika wstążki. **Uwaga:**  Element wstążki **(XML)** można dodać do projektu, aby wygenerować domyślną implementację <xref:Microsoft.Office.Core.IRibbonExtensibility> w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [Xml wstążki](../vsto/ribbon-xml.md).|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word|
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|Zaim implementuj ten interfejs, aby utworzyć niestandardowe okienko zadań.|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Zaim implementuj ten interfejs, aby utworzyć region formularza programu Outlook.|Outlook|

 Istnieje kilka innych interfejsów rozszerzalności, które są definiowane przez Microsoft Office, takie jak <xref:Microsoft.Office.Core.IBlogExtensibility> , <xref:Microsoft.Office.Core.EncryptionProvider> i <xref:Microsoft.Office.Core.SignatureProvider> . Visual Studio nie obsługuje implementowania tych interfejsów w dodatku VSTO utworzonym przy użyciu szablonów projektów pakietu Office.

## <a name="use-extensibility-interfaces"></a>Korzystanie z interfejsów rozszerzalności
 Aby dostosować funkcję interfejsu użytkownika przy użyciu interfejsu rozszerzalności, zaim implementuj odpowiedni interfejs w projekcie dodatku VSTO. Następnie zastąp metodę <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> , aby zwrócić wystąpienie klasy, która implementuje interfejs.

 Przykładowa aplikacja, która demonstruje sposób implementowania interfejsów , i w dodatku VSTO dla programu Outlook, zobacz przykładowy menedżer interfejsu użytkownika w przykładach deweloperycznych <xref:Microsoft.Office.Core.IRibbonExtensibility> <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> pakietu <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> [Office.](../vsto/office-development-samples.md)

### <a name="example-of-implementing-an-extensibility-interface"></a>Przykład implementacji interfejsu rozszerzalności
 Poniższy przykład kodu przedstawia prostą implementację <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> interfejsu w celu utworzenia niestandardowego okienka zadań. W tym przykładzie zdefiniowano dwie klasy:

- Klasa `TaskPaneHelper` implementuje tworzenie <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> i wyświetlanie niestandardowego okienka zadań.

- Klasa `TaskPaneUI` udostępnia interfejs użytkownika okienka zadań. Atrybuty klasy sprawiają, że klasa jest widoczna dla com, co `TaskPaneUI` Microsoft Office aplikacji do odnajdywania klasy. W tym przykładzie interfejs użytkownika jest <xref:System.Windows.Forms.UserControl> pusty, ale możesz dodać kontrolki, modyfikując kod.

  > [!NOTE]
  > Aby `TaskPaneUI` uwidocznić klasę dla com, należy również ustawić zarejestruj dla **com interop** właściwości dla projektu.

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb" id="Snippet1":::
  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs" id="Snippet1":::

  Aby uzyskać więcej informacji na temat implementowania programu , zobacz Tworzenie niestandardowych okienek zadań w systemie <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> [pakietu Office 2007](/previous-versions/office/developer/office-2007/aa338197(v=office.12)) w Microsoft Office dokumentacji.

### <a name="example-of-overriding-the-requestservice-method"></a>Przykład zastępowania metody RequestService
 Poniższy przykład kodu pokazuje, jak zastąpić metodę w celu zwrócenia wystąpienia <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> `TaskPaneHelper` klasy z poprzedniego przykładu kodu. Sprawdza wartość parametru *serviceGuid,* aby określić żądany interfejs, a następnie zwraca obiekt, który implementuje ten interfejs.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs" id="Snippet2":::

## <a name="see-also"></a>Zobacz też
- [Office development samples and walkthroughs (Przykłady i wskazówki dotyczące tworzenia aplikacji pakietu Office)](../vsto/office-development-samples-and-walkthroughs.md)
- [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md)
- [Opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Wywołanie kodu w dodatki VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
