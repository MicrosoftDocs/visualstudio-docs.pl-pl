---
title: 'Instrukcje: zwiększanie węzła programu SharePoint w Eksplorator serwera | Microsoft Docs'
description: Zapoznaj się z tematem jak zwiększyć węzeł programu SharePoint w Eksplorator serwera przy użyciu węzła połączenia programu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e38f1d18736c18f5273eb2e202de52af81e73f85
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217453"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Instrukcje: zwiększanie węzła programu SharePoint w Eksplorator serwera
  Węzły można rozciągnąć w węźle **połączenia programu SharePoint** w **Eksplorator serwera**. Jest to przydatne, gdy chcesz dodać nowe węzły podrzędne, elementy menu skrótów lub właściwości do istniejącego węzła. Aby uzyskać więcej informacji, zobacz sekcję Rozpoznaj [węzeł połączenia SharePoint w Eksplorator serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Aby zwiększyć węzeł programu SharePoint w Eksplorator serwera

1. Utwórz projekt biblioteki klas.

2. Dodaj odwołania do następujących zestawów:

    - Microsoft. VisualStudio. SharePoint

    - Microsoft. VisualStudio. SharePoint. Explorer. Extensions

    - System. ComponentModel. kompozycji

3. Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfejs.

4. Dodaj <xref:System.ComponentModel.Composition.ExportAttribute> atrybut do klasy. Ten atrybut umożliwia programowi Visual Studio odnajdywanie i ładowanie <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implementacji. Przekaż <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Typ do konstruktora atrybutu.

5. Dodaj <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> atrybut do klasy. Ten atrybut określa identyfikator ciągu dla typu węzła, który ma zostać rozszerzona.

     Aby określić wbudowane typy węzłów dostarczone przez program Visual Studio, Przekaż jedną z następujących wartości wyliczenia do konstruktora atrybutów:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Użyj tych wartości, aby określić węzły połączenia lokacji (węzły, które wyświetlają adresy URL lokacji), węzły lokacji lub wszystkie węzły nadrzędne w **Eksplorator serwera**.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Użyj tych wartości, aby określić jeden z wbudowanych węzłów, które reprezentują poszczególne składniki w witrynie programu SharePoint, takie jak węzeł, który reprezentuje listę, pole lub typ zawartości.

6. W implementacji <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> metody należy użyć elementów członkowskich parametru *NodeType* , aby dodać funkcje do węzła. Ten parametr jest <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> obiektem, który zapewnia dostęp do zdarzeń zdefiniowanych w <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> interfejsie. Można na przykład obsłużyć następujące zdarzenia:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Obsłuż to zdarzenie, aby dodać nowe węzły podrzędne do węzła. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie niestandardowego węzła SharePoint do Eksplorator serwera](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Obsłuż to zdarzenie, aby dodać niestandardowy element menu skrótów do węzła.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Obsłuż to zdarzenie, aby dodać do węzła właściwości niestandardowe. Właściwości są wyświetlane w oknie **Właściwości** , gdy jest wybrany węzeł.

## <a name="example"></a>Przykład
 Poniższy przykład kodu demonstruje, jak utworzyć dwa różne typy rozszerzeń węzłów:

- Rozszerzenie, które dodaje element menu kontekstowego do węzłów witryny programu SharePoint. Po kliknięciu elementu menu zostanie wyświetlona nazwa klikniętego węzła.

- Rozszerzenie, które dodaje właściwość niestandardową o nazwie **ContosoExampleProperty** do każdego węzła, który reprezentuje pole o nazwie **Body**.

  :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs" id="Snippet9":::
  :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb" id="Snippet9":::

  To rozszerzenie dodaje edytowalną właściwość ciągu do węzłów. Można również utworzyć niestandardowe właściwości, które wyświetlają dane tylko do odczytu z serwera programu SharePoint. Aby zapoznać się z przykładem, który ilustruje, jak to zrobić, zobacz [Przewodnik: rozszerzona Eksplorator serwera w celu wyświetlenia części sieci Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład wymaga odwołania do następujących zestawów:

- Microsoft. VisualStudio. SharePoint

- Microsoft. VisualStudio. SharePoint. Explorer. Extensions

- System. ComponentModel. kompozycji

- System. Windows. Forms

## <a name="deploy-the-extension"></a>Wdróż rozszerzenie
 Aby wdrożyć rozszerzenie **Eksplorator serwera** , Utwórz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiet rozszerzenia (VSIX) dla zestawu i innych plików, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Dodawanie niestandardowego węzła programu SharePoint do Eksplorator serwera](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Rozwiń węzeł połączenia programu SharePoint w Eksplorator serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Przewodnik: rozszerzona Eksplorator serwera do wyświetlania składników Web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Kojarzenie danych niestandardowych z rozszerzeniami narzędzi programu SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
