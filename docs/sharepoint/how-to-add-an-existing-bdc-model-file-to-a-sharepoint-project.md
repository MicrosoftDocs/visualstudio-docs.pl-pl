---
title: 'Instrukcje: Dodawanie istniejącego modelu BDC do projektu programu SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fa799e54f2fc8be22b78eca837d6aee2e683b1d3
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863906"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Instrukcje: Dodawanie istniejącego modelu BDC do projektu programu SharePoint
  Można dostosować, pakowanie i ponowne wdrażanie modelu łączności danych biznesowych (BDC) przy użyciu programu Visual Studio, aby dodać plik modelu (*.bdcm*) do każdego projektu programu SharePoint w farmie. Aby uzyskać więcej informacji, zobacz [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Aby dodać plik modelu usługi BDC do projektu programu SharePoint  
  
1. W **Eksploratora rozwiązań**, wybierz folder dla projektu programu SharePoint.  
  
2. Na pasku menu wybierz **projektu** > **Dodaj istniejący element**.  
  
3. W **Dodaj istniejący element** okno dialogowe, przejdź do lokalizacji pliku definicji modelu, który chcesz dodać do projektu, wybierz plik a następnie wybierz **Dodaj** przycisku.  
  
    Jeśli nie zdefiniowano modelu *Line of Business (LOB) systemu typu zestawu .NET*, **element LobSystem zestawu .NET Dodawanie** zostanie otwarte okno dialogowe.  
  
4. Jeśli pojawi się okno dialogowe, wykonaj jedną z następujących czynności:  
  
   - Jeśli chcesz napisać kod niestandardowy i zdefiniuj metadanych dla modelu importowany, wybierz za pomocą projektanta **tak** przycisk, system nazwę, a następnie wybierz **OK** przycisku.  
  
   - W przeciwnym razie wybierz **nie** przycisk, a następnie wybierz **OK** przycisku.  
  
     **Model usługi łączności danych biznesowych** element zostanie dodany do projektu.  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Instrukcje: Tworzenie modelu BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Instrukcje: Korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości oraz uprawnień](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Instrukcje: Dołączanie niestandardowego zestawu w funkcji BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrowanie danych biznesowych programu SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
