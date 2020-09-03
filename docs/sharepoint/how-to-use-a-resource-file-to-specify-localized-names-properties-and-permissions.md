---
title: 'Instrukcje: korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości i uprawnień | Microsoft Docs'
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
ms.openlocfilehash: a87cc8a3eb8f98ea19a87e93c37aae5303151ecf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015401"
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>Instrukcje: korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości i uprawnień
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
