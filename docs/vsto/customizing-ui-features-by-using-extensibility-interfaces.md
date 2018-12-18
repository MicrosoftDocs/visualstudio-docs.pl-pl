---
title: Dostosowywanie funkcji interfejsu użytkownika, korzystając z rozszerzalności interfejsów
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ec1f538515c8765629e812b8d7f4070476dd95ba
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670848"
---
# <a name="customize-ui-features-by-using-extensibility-interfaces"></a>Dostosowywanie funkcji interfejsu użytkownika, korzystając z rozszerzalności interfejsów
  Narzędzi programistycznych pakietu Office w programie Visual Studio zawierają klasy i projektantów, które obsługują wiele szczegółów implementacji, gdy ich użyć do tworzenia niestandardowych okienek zadań, dostosowań Wstążki i regionach formularzy programu Outlook w dodatku VSTO. Jednak możesz również wdrożyć *interfejsu rozszerzalności* dla każdej funkcji samodzielnie, jeśli masz specjalne wymagania.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="overview-of-extensibility-interfaces"></a>Omówienie rozszerzalności interfejsów  
 Microsoft Office definiuje zestaw rozszerzalności interfejsów, które można zaimplementować dodatki COM, VSTO, aby dostosować niektóre funkcje, takie jak wstążki. Te interfejsy zapewniają pełną kontrolę nad funkcjami, które zapewniają dostęp do. Jednak wdrażanie tych interfejsów wymaga pewną wiedzę na temat współdziałania COM w kodzie zarządzanym. W niektórych przypadkach model programowania tych interfejsów również nie jest intuicyjna dla deweloperów, którzy są przyzwyczajeni do programu .NET Framework.  
  
 Podczas tworzenia dodatku narzędzi VSTO przy użyciu szablonów projektów pakietu Office w programie Visual Studio, nie trzeba implementować interfejsy rozszerzalności, aby dostosować funkcje, takie jak wstążki. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Implementuje te interfejsy dla Ciebie. Zamiast tego można użyć bardziej intuicyjne klasy i projektanci dostarczane przez program Visual Studio. Jednak możesz nadal zaimplementować rozszerzalności interfejsów bezpośrednio w dodatku narzędzi VSTO dla programów, jeśli chcesz.  
  
 Aby uzyskać więcej informacji o klasach i projektantów, udostępnianych przez program Visual Studio w ramach tych funkcji, zobacz [niestandardowych okienek zadań](../vsto/custom-task-panes.md), [projektanta wstążki](../vsto/ribbon-designer.md), i [tworzenie regionach formularzy programu Outlook](../vsto/creating-outlook-form-regions.md).  
  
## <a name="extensibility-interfaces-you-can-implement-in-a-vsto-add-in"></a>Rozszerzalność interfejsów, które można zaimplementować w dodatku narzędzi VSTO  
 W poniższej tabeli wymieniono rozszerzalności interfejsów, które można zaimplementować i aplikacje, które je obsługują.  
  
|Interface|Opis|Aplikacje|  
|---------------|-----------------|------------------|  
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|Implementuje ten interfejs, aby dostosować interfejs użytkownika wstążki. **Uwaga:** można dodać **wstążki (XML)** elementu do projektu, aby wygenerować domyślny <xref:Microsoft.Office.Core.IRibbonExtensibility> implementacji w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Visio<br /><br /> Word|  
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|Implementuje ten interfejs do tworzenia niestandardowego okienka zadań.|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|  
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Implementuje ten interfejs do tworzenia regionów formularzy programu Outlook.|Outlook|  
  
 Istnieje kilka interfejsów rozszerzalności, w które są definiowane przez Microsoft Office, takich jak <xref:Microsoft.Office.Core.IBlogExtensibility>, <xref:Microsoft.Office.Core.EncryptionProvider>, i <xref:Microsoft.Office.Core.SignatureProvider>. Program Visual Studio nie obsługuje wykonywania tych interfejsów w dodatku narzędzi VSTO utworzone przy użyciu szablonów projektów pakietu Office.  
  
## <a name="use-extensibility-interfaces"></a>Użyj rozszerzalności interfejsów  
 Dostosowywanie funkcji interfejsu użytkownika przy użyciu interfejsu rozszerzalności, należy zaimplementować odpowiedni interfejs w projekcie dodatku narzędzi VSTO. Następnie zastąp <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metodę, aby zwrócić wystąpienia klasy, która implementuje interfejs.  
  
 Dla przykładowej aplikacji, który demonstruje sposób implementacji <xref:Microsoft.Office.Core.IRibbonExtensibility>, <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>, i <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> interfejsy w dodatku narzędzi VSTO dla programu Outlook, zobacz przykład interfejsu użytkownika menedżera w [Office development ― przykłady](../vsto/office-development-samples.md).  
  
### <a name="example-of-implementing-an-extensibility-interface"></a>Przykład implementacji interfejsów rozszerzalności  
 Poniższy przykład kodu demonstruje proste wdrażanie <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> interfejs do tworzenia niestandardowego okienka zadań. Ten przykład definiuje dwie klasy:  
  
- `TaskPaneHelper` Klasy implementuje <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> zostać utworzony i wyświetlony niestandardowego okienka zadań.  
  
- `TaskPaneUI` Klasa udostępnia interfejs użytkownika okienka zadań. Wartości atrybutów `TaskPaneUI` klasy widoczności klasy COM, który umożliwia aplikacji Microsoft Office odnaleźć klasy. W tym przykładzie interfejs użytkownika jest pusta <xref:System.Windows.Forms.UserControl>, ale można dodać formanty, modyfikując kod.  
  
  > [!NOTE]  
  >  Aby udostępnić `TaskPaneUI` klasy dla modelu COM, należy także ustawić **Zarejestruj dla współdziałania COM** właściwość dla projektu.  
  
  [!code-vb[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#1)]
  [!code-csharp[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#1)]  
  
  Aby uzyskać więcej informacji o implementowaniu <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>, zobacz [Tworzenie niestandardowych okienek zadań w 2007 Office system](/previous-versions/office/developer/office-2007/aa338197(v=office.12)) w dokumentacji programu Microsoft Office.  
  
### <a name="example-of-overriding-the-requestservice-method"></a>Zastępowanie metody RequestService przykład  
 Poniższy przykład kodu demonstruje sposób zastąpienia <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metodę, aby zwrócić wystąpienia `TaskPaneHelper` klasy z poprzedniego przykładu kodu. Sprawdza wartość *serviceGuid* parametru, aby określić, który interfejs jest wymagana, a następnie zwraca obiekt, który implementuje ten interfejs.  
  
 [!code-vb[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#2)]
 [!code-csharp[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#2)]  
  
## <a name="see-also"></a>Zobacz także  
 [Office development ― przykłady i przewodniki](../vsto/office-development-samples-and-walkthroughs.md)   
 [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Opracowywania rozwiązań pakietu Office](../vsto/developing-office-solutions.md)   
 [Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)  
  
  