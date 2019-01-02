---
title: 'Instrukcje: Korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości oraz uprawnień | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c61e996380ff2cca6ddc3c60ad4c6d13d10c93f2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53819468"
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>Instrukcje: Korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości oraz uprawnień
  Za pomocą pliku zasobów, można podać zlokalizowanych nazw, zdefiniuj właściwości i stosować uprawnienia tor obiekty, które są zdefiniowane w modelu łączności danych biznesowych (BDC). Aby podać te informacje, należy dodać **zasobu łączności danych biznesowych** elementu do projektu, który zawiera **Model usługi łączności danych biznesowych** elementu. Następnie można określić nazwy, właściwości i uprawnienia, edytując XML pliku zasobu.  
  
### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Aby dodać plik zasobu usługi łączności danych biznesowych do projektu programu SharePoint  
  
1.  W **Eksploratora rozwiązań**, rozwiń folder dla projektu programu SharePoint, a następnie wybierz folder, który zawiera model usługi łączności danych biznesowych.  
  
2.  Na pasku menu wybierz **projektu** > **Dodaj nowy element**.  
  
3.  Rozwiń **SharePoint** węzła, a następnie wybierz **2010** węzła.  
  
4.  W **Dodaj nowy element** okna dialogowego wybierz **element zasobu usługi łączności danych biznesowych**.  
  
5.  W **nazwa** , określ nazwę pliku zasobów, a następnie wybierz **Dodaj** przycisku.  
  
     Plik zasobów, który ma rozszerzenie .bdcr jest dodawany do projektu i otworzyć do edycji.  
  
6.  Dodaj kod XML do definiowania zlokalizowanych nazw, właściwości i uprawnienia, które chcesz zastosować modelu usługi BDC.  
  
     Aby dowiedzieć się, jak zdefiniować te elementy, zobacz [modelu i pliki zasobów](http://go.microsoft.com/fwlink/?LinkID=169283).  
  
## <a name="see-also"></a>Zobacz także
 [Instrukcje: Dodawanie istniejącego modelu BDC do projektu programu SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Instrukcje: Tworzenie modelu BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Instrukcje: Dołączanie niestandardowego zestawu w funkcji BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrowanie danych biznesowych programu SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
