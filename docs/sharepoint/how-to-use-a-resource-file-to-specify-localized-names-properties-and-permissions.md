---
title: Jak używać pliku zasobów w projekcie programu SharePoint | Microsoft Docs
titleSuffix: ''
description: Użyj pliku zasobów w projekcie programu SharePoint, aby udostępnić zlokalizowane nazwy, zdefiniować właściwości i zastosować uprawnienia dla obiektów zdefiniowanych w modelu usługi BDC.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 49546d11dbf4f19bb2fd826ace2850468f780d13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851559"
---
# <a name="how-to-use-a-resource-file-in-a-sharepoint-project"></a>Jak używać pliku zasobów w projekcie programu SharePoint

  Za pomocą pliku zasobów można zapewnić zlokalizowane nazwy, definiować właściwości i stosować uprawnienia tor, które są zdefiniowane w modelu łączności danych biznesowych (BDC). Aby określić te informacje, należy dodać element **zasobu łączności danych firmowych** do projektu, który zawiera element **modelu łączności danych firmowych** . Następnie należy określić nazwy, właściwości i uprawnienia, edytując kod XML dla pliku zasobu.

### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Aby dodać plik zasobów usługi BDC do projektu programu SharePoint

1. W **Eksplorator rozwiązań** rozwiń folder dla projektu programu SharePoint, a następnie wybierz folder, który zawiera model usługi BDC.

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
