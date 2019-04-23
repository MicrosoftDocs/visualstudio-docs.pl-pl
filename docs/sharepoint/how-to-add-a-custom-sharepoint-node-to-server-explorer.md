---
title: 'Instrukcje: Dodawanie niestandardowego węzła SharePoint do Eksploratora serwera | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8ece5c207a0244a55078ef44f9156e7e95cedf5c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066497"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Instrukcje: Dodawanie niestandardowego węzła SharePoint do Eksploratora serwera
  Możesz dodać niestandardowe węzły w obszarze **połączeń SharePoint** w węźle **Eksploratora serwera**. Jest to przydatne, jeśli chcesz wyświetlić dodatkowe składniki programu SharePoint, które nie są wyświetlane w **Eksploratora serwera** domyślnie. Aby uzyskać więcej informacji, zobacz [rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

 Aby dodać niestandardowy węzeł, najpierw należy utworzyć klasę, która definiuje nowy węzeł. Następnie utwórz rozszerzenie, które dodaje węzeł jako element podrzędny istniejący węzeł.

### <a name="to-define-the-new-node"></a>Aby zdefiniować nowy węzeł

1. Utwórz projekt biblioteki klas.

2. Dodaj odwołania do następujących zestawów:

    - Microsoft.VisualStudio.SharePoint

    - Microsoft.VisualStudio.SharePoint.Explorer.Extensions

    - System.ComponentModel.Composition

    - System.Drawing

3. Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfejsu.

4. Dodaj następujące atrybuty do klasy:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Ten atrybut umożliwia środowisku Visual Studio wykrycie i załadowanie swoje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> implementacji. Przekaż <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> typu konstruktora atrybutu.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. W definicji węzła ten atrybut określa identyfikator ciągu dla nowego węzła. Zalecane jest użycie formatu *nazwa firmy*. *Nazwa węzła* aby upewnić się, że wszystkie węzły mają unikatowy identyfikator.

5. W danej implementacji <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> metody, użyj członkowie *typeDefinition* parametru, aby skonfigurować zachowanie nowego węzła. Ten parametr jest <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> obiektu, który zapewnia dostęp do zdarzenia, zdefiniowany w <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> interfejsu.

     Poniższy przykład kodu demonstruje sposób definiowania nowego węzła. W tym przykładzie przyjęto założenie, że projekt zawiera ikony o nazwie CustomChildNodeIcon jako zasobu osadzonego.

     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]

### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>Aby dodać nowy węzeł jako element podrzędny istniejący węzeł

1. W tym samym projekcie jako swojej definicji węzła, należy utworzyć klasę, która implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfejsu.

2. Dodaj <xref:System.ComponentModel.Composition.ExportAttribute> do klasy atrybutu. Ten atrybut umożliwia środowisku Visual Studio wykrycie i załadowanie swoje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implementacji. Przekaż <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> typu konstruktora atrybutu.

3. Dodaj <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> do klasy atrybutu. W rozszerzeniu węzła ten atrybut określa identyfikator ciągu dla typu węzła, który ma zostać rozszerzony.

     Aby określić typów wbudowanego węzła przez program Visual Studio, należy przekazać jeden z następujących wartości wyliczenia do konstruktora atrybutu:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Użyj tych wartości, aby określić węzeł połączenia witryny (węzły, które wyświetlają adresów URL witryn), lokacji węzłów lub wszystkich innych węzłów nadrzędnych w **Eksploratora serwera**.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Aby określić jedną z wbudowanych węzły, które reprezentują poszczególnych składników w witrynie programu SharePoint, takich jak węzeł, który reprezentuje listę, pole lub typ zawartości, należy użyć tych wartości.

4. W danej implementacji <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> metody, uchwyt <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> zdarzenia <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> parametru.

5. W <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> procedura obsługi zdarzeń, Dodaj nowy węzeł do kolekcji węzłów podrzędnych <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> obiektu uwidocznionego przez parametr argumenty zdarzenia.

     Poniższy przykład kodu demonstruje sposób dodawania nowego węzła jako element podrzędny węzła witryny programu SharePoint w **Eksploratora serwera**.

     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]

## <a name="complete-example"></a>Kompletny przykład
 Poniższy przykład kodu zawiera kompletny kod, aby zdefiniować prostą węzeł i dodaj go jako element podrzędny węzła witryny programu SharePoint w **Eksploratora serwera**.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]

## <a name="compiling-the-code"></a>Kompilowanie kodu
 W tym przykładzie przyjęto założenie, że projekt zawiera ikony o nazwie CustomChildNodeIcon jako zasobu osadzonego. Ten przykład wymaga także odwołania do następujących zestawów:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

- System.Drawing

## <a name="deploy-the-extension"></a>Wdrażanie rozszerzenia
 Aby wdrożyć **Eksploratora serwera** rozszerzenia, Utwórz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenie (VSIX), pakiet dla zestawu i innych plików, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz także
- [Rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Instrukcje: Rozszerzanie węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Przewodnik: Rozszerzanie Eksploratora serwera na potrzeby wyświetlania składników web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
