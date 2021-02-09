---
title: 'Instrukcje: Dodawanie niestandardowego węzła programu SharePoint do Eksplorator serwera | Microsoft Docs'
titleSuffix: ''
description: Dodaj niestandardowy węzeł programu SharePoint do Eksplorator serwera w programie Visual Studio. Wyświetl dodatkowe składniki programu SharePoint, które domyślnie nie są wyświetlane w Eksplorator serwera.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: be772075be27cc8d6e58b6b54bb281a127f4677f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878126"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Instrukcje: Dodawanie niestandardowego węzła programu SharePoint do Eksplorator serwera
  Węzły niestandardowe można dodać w węźle **połączenia programu SharePoint** w **Eksplorator serwera**. Jest to przydatne, gdy chcesz wyświetlić dodatkowe składniki programu SharePoint, które nie są domyślnie wyświetlane w **Eksplorator serwera** . Aby uzyskać więcej informacji, zobacz sekcję Rozpoznaj [węzeł połączenia SharePoint w Eksplorator serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

 Aby dodać węzeł niestandardowy, najpierw Utwórz klasę, która definiuje nowy węzeł. Następnie utwórz rozszerzenie, które dodaje węzeł jako element podrzędny istniejącego węzła.

### <a name="to-define-the-new-node"></a>Aby zdefiniować nowy węzeł

1. Utwórz projekt biblioteki klas.

2. Dodaj odwołania do następujących zestawów:

    - Microsoft. VisualStudio. SharePoint

    - Microsoft. VisualStudio. SharePoint. Explorer. Extensions

    - System. ComponentModel. kompozycji

    - System. Drawing

3. Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfejs.

4. Dodaj następujące atrybuty do klasy:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Ten atrybut umożliwia programowi Visual Studio odnajdywanie i ładowanie <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> implementacji. Przekaż <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> Typ do konstruktora atrybutu.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. W definicji węzła ten atrybut określa identyfikator ciągu dla nowego węzła. Zalecamy użycie formatu *Nazwa firmy*. *nazwa węzła* , aby upewnić się, że wszystkie węzły mają unikatowy identyfikator.

5. W implementacji <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> metody należy użyć elementów członkowskich parametru *typeDefinition* , aby skonfigurować zachowanie nowego węzła. Ten parametr jest <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> obiektem, który zapewnia dostęp do zdarzeń zdefiniowanych w <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> interfejsie.

     Poniższy przykład kodu demonstruje sposób definiowania nowego węzła. W tym przykładzie przyjęto założenie, że projekt zawiera ikonę o nazwie CustomChildNodeIcon jako zasób osadzony.

     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]

### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>Aby dodać nowy węzeł jako element podrzędny istniejącego węzła

1. W tym samym projekcie, w którym znajduje się definicja węzła, Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfejs.

2. Dodaj <xref:System.ComponentModel.Composition.ExportAttribute> atrybut do klasy. Ten atrybut umożliwia programowi Visual Studio odnajdywanie i ładowanie <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implementacji. Przekaż <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Typ do konstruktora atrybutu.

3. Dodaj <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> atrybut do klasy. W rozszerzeniu węzła ten atrybut określa identyfikator ciągu dla typu węzła, który ma zostać rozszerzona.

     Aby określić wbudowane typy węzłów dostarczone przez program Visual Studio, Przekaż jedną z następujących wartości wyliczenia do konstruktora atrybutów:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Użyj tych wartości, aby określić węzły połączenia lokacji (węzły, które wyświetlają adresy URL lokacji), węzły lokacji lub wszystkie węzły nadrzędne w **Eksplorator serwera**.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Użyj tych wartości, aby określić jeden z wbudowanych węzłów, które reprezentują poszczególne składniki w witrynie programu SharePoint, takie jak węzeł, który reprezentuje listę, pole lub typ zawartości.

4. W implementacji <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> metody należy obsłużyć <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> zdarzenie <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> parametru.

5. W programie <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> obsługi zdarzeń Dodaj nowy węzeł do kolekcji węzłów podrzędnych <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> obiektu, który jest udostępniany przez parametr argumenty zdarzenia.

     Poniższy przykład kodu pokazuje, jak dodać nowy węzeł jako element podrzędny węzła witryny programu SharePoint w **Eksplorator serwera**.

     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]

## <a name="complete-example"></a>Pełny przykład
 Poniższy przykład kodu zawiera kompletny kod definiujący prosty węzeł i dodaj go jako element podrzędny węzła witryny programu SharePoint w **Eksplorator serwera**.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]

## <a name="compiling-the-code"></a>Kompilowanie kodu
 W tym przykładzie przyjęto założenie, że projekt zawiera ikonę o nazwie CustomChildNodeIcon jako zasób osadzony. Ten przykład wymaga również odwołań do następujących zestawów:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. kompozycji

- System. Drawing

## <a name="deploy-the-extension"></a>Wdróż rozszerzenie
 Aby wdrożyć rozszerzenie **Eksplorator serwera** , Utwórz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiet rozszerzenia (VSIX) dla zestawu i innych plików, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też
- [Rozwiń węzeł połączenia programu SharePoint w Eksplorator serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Instrukcje: zwiększanie węzła programu SharePoint w Eksplorator serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Przewodnik: rozszerzona Eksplorator serwera do wyświetlania składników Web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
