---
title: 'Instrukcje: Dodaj plik zasobów | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 928a306640c449db4fa168ffcdbdd7efaeea0ae1
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54862879"
---
# <a name="how-to-add-a-resource-file"></a>Instrukcje: Dodawanie pliku zasobu
  Polecenia służące do dodawania plików zasobów znajduje się w menu skrótów dla węzła rozwiązania i funkcja węzły w Eksploratorze rozwiązań. Aby uzyskać więcej informacji, zobacz [rozwiązań SharePoint lokalizowanie](../sharepoint/localizing-sharepoint-solutions.md).  
  
### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Aby dodać plik globalnych zasobów do rozwiązania programu SharePoint  
  
1. W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], otwórz rozwiązanie programu SharePoint.  
  
2. W **Eksploratora rozwiązań**, wybierz węzeł projektu programu SharePoint, a następnie na pasku menu wybierz **projektu** > **Dodaj nowy element**.  
  
3. W **Dodaj nowy element** okna dialogowego wybierz **plik zasobów globalnych** szablonu, a następnie wybierz **Dodaj** przycisku.  
  
   > [!NOTE]  
   >  Plik zasobów globalnych szablonu elementu projektu pojawia się tylko w przypadku wybrania elementu projektu programu SharePoint.  
  
4. W **Dodaj zasób** okna dialogowego Wybierz kulturę pliku zasobów, takich jak angielski (Stany Zjednoczone).  
  
    Ten krok powoduje dodanie plik globalnych zasobów do swojego rozwiązania w formacie Resource_x_**.** <em>kultury</em><strong>.</strong> Program resx, takich jak *Resource1.en US.resx*.  
  
5. Gdy **Edytor zasobów** zostanie otwarty w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], dodać zasoby do pliku zasobów.  
  
### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Aby dodać plik zasobów funkcji do funkcji SharePoint  
  
1.  Jeśli rozwiązania programu SharePoint nie jest już otwarty w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], otwórz rozwiązanie.  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla nazwy funkcji w obszarze **funkcji** węzła, a następnie wybierz **Dodaj zasób funkcji**.  
  
     Ten krok powoduje dodanie pliku zasobu do funkcji w formacie _Nazwaplikuzasobów_**.** _kultury_**resx**, takich jak *Feature1.en US.resx*.  
  
3.  Gdy **Edytor zasobów** zostanie otwarty w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], dodać zasoby do pliku zasobów.  
  
## <a name="see-also"></a>Zobacz także
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
