---
title: Rozszerzanie węzła połączenia programu SharePoint w Eksplorator serwera | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6b1d461419497a0a45f50f12589cf3ac978a7666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967360"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Rozwiń węzeł połączenia programu SharePoint w Eksplorator serwera
  W programie Visual Studio można nawiązać połączenie z lokalnymi witrynami programu SharePoint na komputerze deweloperskim przy użyciu węzła **połączenia programu SharePoint** w oknie **Eksplorator serwera** . Ten węzeł wyświetla wiele składników lokalnych witryn programu SharePoint w hierarchicznym widoku drzewa. Na przykład można wyświetlić listy, biblioteki dokumentów i typy zawartości w lokacjach lokalnych. Aby uzyskać więcej informacji na temat używania **Eksplorator serwera** do nawiązywania połączenia z lokalnymi witrynami programu SharePoint, zobacz [przeglądanie połączeń SharePoint przy użyciu Eksplorator serwera](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).

 Węzeł **połączenia SharePoint** można rozszerzać przez tworzenie rozszerzeń dla istniejących węzłów lub przez utworzenie niestandardowego typu węzła i dodanie go do hierarchii węzłów.

## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>Zadania rozszerzania węzła połączenia programu SharePoint
 Aby rozszerzać istniejący węzeł, Utwórz rozszerzenie programu Visual Studio, które implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfejs. Rozszerzając węzeł, można dodać funkcjonalność do węzła, na przykład własne elementy menu skrótów lub właściwości niestandardowe. Aby uzyskać więcej informacji, zobacz [How to: rozszerzając węzeł SharePoint w Eksplorator serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

 Aby utworzyć niestandardowy typ węzła, Utwórz rozszerzenie programu Visual Studio, które implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfejs. Utwórz węzeł niestandardowy, jeśli chcesz wyświetlić składniki witryn programu SharePoint, które nie są domyślnie wyświetlane w **Eksplorator serwera** . Na przykład **Eksplorator serwera** nie wyświetla domyślnie galerii składników Web Part witryny programu SharePoint, ale można dodać do niej niestandardowy węzeł. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie niestandardowego węzła SharePoint do Eksplorator serwera](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) i wskazówki [: rozszerzona Eksplorator serwera do wyświetlania składniki Web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="add-custom-properties-to-nodes"></a>Dodawanie właściwości niestandardowych do węzłów
 Rozszerzając węzeł lub tworząc niestandardowy typ węzła, można dodać właściwości niestandardowe do węzła. Właściwości są wyświetlane w oknie **Właściwości** , gdy jest wybrany węzeł.

 Istnieją dwa typy właściwości niestandardowych, które można dodać do węzła:

- Właściwości, które wyświetlają zestaw danych tylko do odczytu z witryny programu SharePoint. Dane opisują składnik programu SharePoint reprezentowany przez węzeł. Aby zapoznać się z przewodnikiem, który pokazuje, jak to zrobić, zobacz [Przewodnik: rozszerzona Eksplorator serwera w celu wyświetlenia części sieci Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Właściwości, które wyświetlają dane niestandardowe do odczytu/zapisu. Przykładowy kod, który pokazuje, jak to zrobić, można znaleźć [w temacie How to: rozszerzając a SharePoint Node in Eksplorator serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="get-data-for-built-in-nodes"></a>Pobieranie danych dla węzłów wbudowanych
 Wszystkie wbudowane węzły udostępniane przez program Visual Studio obejmują pewne dane dotyczące składnika programu SharePoint, który reprezentuje. Na przykład węzeł, który reprezentuje listę w witrynie programu SharePoint, zawiera pewne dane dotyczące listy, takie jak tytuł i adres URL widoku domyślnego listy.

 Aby uzyskać dostęp do tych danych, Pobierz obiekt danych z <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> obiektu, który reprezentuje interesujący Cię węzeł. Typ obiektu danych zależy od typu węzła.

 Poniższy przykład kodu demonstruje, jak uzyskać obiekt danych dla węzła listy. Aby zobaczyć ten przykład w kontekście większego przykładu, zobacz [jak: pobieranie danych dla wbudowanego węzła programu SharePoint w Eksplorator serwera](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]

 Poniższa tabela zawiera listę typów obiektów danych dla każdego wbudowanego typu węzła.

|Typ węzła|Typ obiektu danych|
|---------------|----------------------|
|Węzeł witryny programu SharePoint|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|
|Typ zawartości|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|
|Cechy|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|
|Pole|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|
|Lista|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|
|Szablon listy|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|
|Widok listy (Microsoft. SharePoint. SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|
|Skojarzenie przepływu pracy|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|
|Szablon przepływu pracy|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|

 Aby uzyskać więcej informacji o używaniu <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości, zobacz [Kojarzenie danych niestandardowych z rozszerzeniami narzędzi programu SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="see-also"></a>Zobacz też
- [Przewodnik: rozszerzona Eksplorator serwera do wyświetlania składników Web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Instrukcje: zwiększanie węzła programu SharePoint w Eksplorator serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Instrukcje: Dodawanie niestandardowego węzła programu SharePoint do Eksplorator serwera](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Instrukcje: pobieranie danych dla wbudowanego węzła programu SharePoint w Eksplorator serwera](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)
- [Kojarzenie danych niestandardowych z rozszerzeniami narzędzi programu SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Przeglądanie połączeń programu SharePoint przy użyciu Eksplorator serwera](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Poszerzanie narzędzi programu SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
