---
title: Rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 36e99b5d239b48add1de5c281c35e698607500d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53933930"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera
  W programie Visual Studio, można nawiązać lokalnych witryn programu SharePoint na komputerze deweloperskim za pomocą **połączeń SharePoint** w węźle **Eksploratora serwera** okna. Ten węzeł Wyświetla wielu składników lokalnych witryn programu SharePoint w hierarchicznym widoku drzewa. Na przykład można wyświetlić listy, biblioteki dokumentów i typów zawartości w lokacji lokalnej. Aby uzyskać więcej informacji o korzystaniu z **Eksploratora serwera** połączyć się z lokalnych witryn programu SharePoint, zobacz [połączeń Przeglądaj SharePoint za pomocą Eksploratora serwera](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).  
  
 Możesz rozszerzyć **połączeń SharePoint** węzła, tworząc rozszerzeń dla istniejących węzłów lub przez tworzenie niestandardowego typu i dodając go do hierarchię węzłów.  
  
## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>Zadania dla rozszerzanie węzła połączeń SharePoint
 Aby rozszerzyć istniejący węzeł, tworzyć rozszerzenia programu Visual Studio, który implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfejsu. Podczas rozszerzania węzła można dodawać funkcjonalność do węzła, takie jak własne elementy menu skrótów lub właściwości niestandardowe. Aby uzyskać więcej informacji, zobacz [jak: Rozszerzanie węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
 Typ węzła niestandardowych, utworzyć rozszerzenie programu Visual Studio, który implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfejsu. Tworzenie niestandardowych węzła, jeśli chcesz wyświetlić składniki witryny programu SharePoint, które nie są wyświetlane w **Eksploratora serwera** domyślnie. Na przykład **Eksploratora serwera** jest nie jest wyświetlana galerii składników Web Part witryny programu SharePoint przez domyślne, ale można dodać niestandardowy węzeł, który wykonuje to. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie niestandardowego węzła SharePoint do Eksploratora serwera](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) i [instruktażu: Rozszerzanie Eksploratora serwera na potrzeby wyświetlania składników Web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## <a name="add-custom-properties-to-nodes"></a>Dodawanie właściwości niestandardowych do węzłów
 Rozszerzanie węzła lub utworzenie typu niestandardowego, można dodać właściwości niestandardowe do węzła. Właściwości są wyświetlane w **właściwości** okna po wybraniu węzła.  
  
 Istnieją dwa typy właściwości niestandardowych, które można dodać do węzła:  
  
-   Właściwości, które wyświetla zestaw danych tylko do odczytu z witryny programu SharePoint. Dane w tym artykule opisano składnik programu SharePoint, który reprezentuje węzeł. Aby uzyskać wskazówki, które pokazuje, jak to zrobić, zobacz [instruktażu: Rozszerzanie Eksploratora serwera na potrzeby wyświetlania składników web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Właściwości, które wyświetlają dane niestandardowe odczytu/zapisu. Dla przykładu kodu, który pokazuje, jak to zrobić, zobacz [jak: Rozszerzanie węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="get-data-for-built-in-nodes"></a>Pobieranie danych dla wbudowanego węzłów
 Wszystkie węzły wbudowanych dostarczane przez program Visual Studio obejmują dane informacje o składniku programu SharePoint, które reprezentują one. Na przykład węzeł, który reprezentuje listę w witrynie programu SharePoint udostępnia dane dotyczące listy, takie jak tytuł i adres URL domyślny widok listy.  
  
 Aby uzyskać dostęp do tych danych, Pobierz obiekt danych z <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwość <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> obiekt, który reprezentuje węzeł, który Cię interesuje. Typ obiektu danych zależy od typu węzła.  
  
 Poniższy przykład kodu pokazuje, jak można pobrać obiektu danych dla węzła listy. Aby wyświetlić ten przykład w kontekście większego przykładu, zobacz [jak: Pobieranie danych dla wbudowanego węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]  
  
 W poniższej tabeli wymieniono typy obiektów danych dla każdego typu wbudowanego węzła.  
  
|Typ węzła|Typ obiektu danych|  
|---------------|----------------------|  
|Węzeł witryny programu SharePoint|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|Typ zawartości|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|Funkcja|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|Pole|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|Lista|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|Szablon listy|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|Widok listy (Microsoft.SharePoint.SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|Skojarzenie przepływu pracy|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|Szablon przepływu pracy|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 Aby uzyskać więcej informacji o korzystaniu z <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości, zobacz [rozszerzeń narzędzi kojarzenie danych niestandardowych z programem SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="see-also"></a>Zobacz także
 [Przewodnik: Rozszerzanie Eksploratora serwera na potrzeby wyświetlania składników web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Instrukcje: Rozszerzanie węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Instrukcje: Dodawanie niestandardowego węzła SharePoint do Eksploratora serwera](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Instrukcje: Pobieranie danych dla wbudowanego węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [Kojarzenie danych niestandardowych z rozszerzeniami narzędzi SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Przeglądanie połączeń SharePoint za pomocą Eksploratora serwera](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Rozszerzanie narzędzi SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
