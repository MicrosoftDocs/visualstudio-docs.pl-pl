---
title: 'Instrukcje: Rozszerzanie węzła SharePoint w Eksploratorze serwera | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5eb475c5311ecbe578f169ae07e156e0aa85c068
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870834"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Instrukcje: Rozszerzanie węzła SharePoint w Eksploratorze serwera
  Możesz rozszerzyć węzłów w ramach **połączeń SharePoint** w węźle **Eksploratora serwera**. Jest to przydatne, jeśli chcesz dodać nowe węzły podrzędne, elementy menu skrótów lub właściwości do istniejącego węzła. Aby uzyskać więcej informacji, zobacz [rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Aby rozszerzanie węzła SharePoint w Eksploratorze serwera  
  
1.  Utwórz projekt biblioteki klas.  
  
2.  Dodaj odwołania do następujących zestawów:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfejsu.  
  
4.  Dodaj <xref:System.ComponentModel.Composition.ExportAttribute> do klasy atrybutu. Ten atrybut umożliwia środowisku Visual Studio wykrycie i załadowanie swoje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implementacji. Przekaż <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> typu konstruktora atrybutu.  
  
5.  Dodaj <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> do klasy atrybutu. Ten atrybut określa identyfikator ciągu dla typu węzła, który ma zostać rozszerzony.  
  
     Aby określić typów wbudowanego węzła przez program Visual Studio, należy przekazać jeden z następujących wartości wyliczenia do konstruktora atrybutu:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Użyj tych wartości, aby określić węzeł połączenia witryny (węzły, które wyświetlają adresów URL witryn), lokacji węzłów lub wszystkich innych węzłów nadrzędnych w **Eksploratora serwera**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Aby określić jedną z wbudowanych węzły, które reprezentują poszczególnych składników w witrynie programu SharePoint, takich jak węzeł, który reprezentuje listę, pole lub typ zawartości, należy użyć tych wartości.  
  
6.  W danej implementacji <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> metody, użyj członkowie *nodeType* parametru, aby dodać funkcje do węzła. Ten parametr jest <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> obiektu, który zapewnia dostęp do zdarzenia, zdefiniowany w <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> interfejsu. Na przykład można obsługiwać następujące zdarzenia:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Obsługiwać to zdarzenie, aby dodać nowe węzły podrzędne węzła do węzła. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie niestandardowego węzła SharePoint do Eksploratora serwera](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Obsługiwać to zdarzenie, aby dodać element menu skrótów niestandardowych do węzła.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Obsługiwać to zdarzenie, aby dodać właściwości niestandardowe do węzła. Właściwości są wyświetlane w **właściwości** okna po wybraniu węzła.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak utworzyć dwa różne typy rozszerzeń węzła:  
  
- Rozszerzenie dodaje element menu kontekstowego do węzłów witryny programu SharePoint. Po kliknięciu elementu menu, wyświetla nazwę węzła, który został kliknięty.  
  
- Rozszerzenie, które dodaje właściwość niestandardową o nazwie **ContosoExampleProperty** do każdego węzła, który reprezentuje pole o nazwie **treści**.  
  
  [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
  [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]  
  
  To rozszerzenie dodaje do ciągu można edytować właściwości do węzłów. Można również utworzyć właściwości niestandardowe, które wyświetlają tylko do odczytu danych z serwera programu SharePoint. Na przykład, który pokazuje, jak to zrobić, zobacz [instruktażu: Rozszerzanie Eksploratora serwera na potrzeby wyświetlania składników web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## <a name="compile-the-code"></a>Skompilować kod  
 Ten przykład wymaga odwołania do następujących zestawów:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## <a name="deploy-the-extension"></a>Wdrażanie rozszerzenia  
 Aby wdrożyć **Eksploratora serwera** rozszerzenia, Utwórz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenie (VSIX), pakiet dla zestawu i innych plików, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz także
 [Instrukcje: Dodawanie niestandardowego węzła SharePoint do Eksploratora serwera](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Przewodnik: Rozszerzanie Eksploratora serwera na potrzeby wyświetlania składników web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Kojarzenie danych niestandardowych z rozszerzeniami narzędzi SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
