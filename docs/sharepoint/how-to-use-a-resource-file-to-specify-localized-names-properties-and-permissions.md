---
title: Jak używać pliku zasobów w projekcie programu SharePoint | Microsoft Docs
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1693308c591e60a2df0e4d8e18ece8cc9b598fd2
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585748"
---
# <a name="how-to-use-a-resource-file-in-a-sharepoint-project"></a>Jak używać pliku zasobów w projekcie programu SharePoint

  Za pomocą pliku zasobów można zapewnić zlokalizowane nazwy, definiować właściwości i stosować uprawnienia tor, które są zdefiniowane w modelu łączności danych biznesowych (BDC). Aby określić te informacje, należy dodać element **zasobu łączności danych firmowych** do projektu, który zawiera element **modelu łączności danych firmowych** . Następnie należy określić nazwy, właściwości i uprawnienia, edytując kod XML dla pliku zasobu.

### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Aby dodać plik zasobów usługi BDC do projektu programu SharePoint

1. W **Eksplorator rozwiązań**rozwiń folder dla projektu programu SharePoint, a następnie wybierz folder, który zawiera model usługi BDC.

2. Na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

3. Rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

4. W oknie dialogowym **Dodaj nowy element** wybierz **element zasób łączności danych firmowych**.

5. W polu **Nazwa** Określ nazwę pliku zasobów, a następnie wybierz przycisk **Dodaj** .

     Plik zasobów, który ma rozszerzenie. BCDR, jest dodawany do projektu i otwarty do edycji.

6. Dodaj plik XML, aby zdefiniować zlokalizowane nazwy, właściwości i uprawnienia, które mają zostać zastosowane w modelu usługi BDC.

     Aby uzyskać informacje na temat sposobu definiowania tych elementów, zobacz [model i pliki zasobów](/previous-versions/office/developer/sharepoint-2010/aa674515(v=office.14)).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Dodawanie istniejącego pliku modelu BDC do projektu programu SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Tworzenie modelu łączności danych firmy](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Instrukcje: Tworzenie modelu usługi BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Instrukcje: uwzględnianie niestandardowego zestawu w funkcji BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrowanie danych firmowych z programem SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
