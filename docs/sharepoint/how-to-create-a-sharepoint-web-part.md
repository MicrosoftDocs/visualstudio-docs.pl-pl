---
title: 'Instrukcje: Tworzenie części sieciowej SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b66cd0b380612502bb982efd464607a4759f9c4b
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870795"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Instrukcje: Tworzenie składnika web part programu SharePoint
  Można tworzyć i dostosowywać składnika web part, dodając **składnika Web Part** element do każdego projektu programu SharePoint, a następnie edytując plik kodu dla składnika web part lub za pomocą projektanta. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie części sieciowej SharePoint za pomocą projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
### <a name="to-create-a-sharepoint-web-part"></a>Aby utworzyć składnik web part programu SharePoint
  
1.  Utwórz lub Otwórz projekt programu SharePoint.  
  
     Aby uzyskać więcej informacji, zobacz [SharePoint szablony elementu projektu i projektu](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Wybierz węzeł projektu programu SharePoint w **Eksploratora rozwiązań** , a następnie wybierz **projektu** > **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element** okna dialogowego rozwiń **SharePoint** węzła, a następnie wybierz **2010** węzła.  
  
4.  Na liście szablonów programu SharePoint, wybierz opcję **składnika Web Part**.  
  
5.  W **nazwa** , określ nazwę dla składnika web part, a następnie wybierz **Dodaj** przycisku.  
  
     Składnik web part, który pojawia się w **Eksploratora rozwiązań**. Aby uzyskać więcej informacji o plikach, które zawiera składnik web part, zobacz [utworzyć składniki web Part programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
6.  W **Eksploratora rozwiązań**, otwórz plik kodu dla składnika web part, który został utworzony.  
  
     Na przykład, jeśli nazwa składnika web part jest *WebPart1*, otwórz *WebPart1.vb* (w języku Visual Basic) lub *WebPart1.cs* (w C#).  
  
7.  W pliku kodu, należy dodać formanty do <xref:System.Web.UI.Control.CreateChildControls%2A> metody.  
  
     Aby uzyskać przykład, zobacz [instruktażu: Tworzenie składnika web part programu SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie składników web Part programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Instrukcje: Tworzenie części sieciowej SharePoint za pomocą projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Przewodnik: Tworzenie składnika web part programu SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Przewodnik: Tworzenie składnika web part programu SharePoint przy użyciu narzędzia Projektant](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
