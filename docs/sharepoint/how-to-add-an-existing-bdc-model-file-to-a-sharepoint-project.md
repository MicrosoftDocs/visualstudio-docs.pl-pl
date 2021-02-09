---
title: 'Instrukcje: Dodawanie istniejącego pliku modelu BDC do projektu programu SharePoint | Microsoft Docs'
titleSuffix: ''
description: Dodaj istniejący plik modelu łączności danych biznesowych (BDC) do projektu programu SharePoint w programie Visual Studio, aby można było dostosować, spakować i ponownie wdrożyć model usługi BDC.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: af0768b4834eb1cad3654b6d74ee8f02cf464245
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882677"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Instrukcje: Dodawanie istniejącego pliku modelu BDC do projektu programu SharePoint
  Można dostosować, spakować i ponownie wdrożyć model łączności danych biznesowych (BDC) przy użyciu programu Visual Studio, aby dodać plik modelu (*. bdcm*) do dowolnego projektu farmy programu SharePoint. Aby uzyskać więcej informacji, zobacz [Tworzenie modelu łączności danych firmowych](../sharepoint/creating-a-business-data-connectivity-model.md).

### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Aby dodać plik modelu usługi BDC do projektu programu SharePoint

1. W **Eksplorator rozwiązań** wybierz folder dla projektu programu SharePoint.

2. Na pasku menu wybierz **projekt**  >  **Dodaj istniejący element**.

3. W oknie dialogowym **Dodaj istniejący element** przejdź do lokalizacji pliku definicji modelu, który chcesz dodać do projektu, wybierz plik, a następnie wybierz przycisk **Dodaj** .

    Jeśli model nie definiuje *systemu LOB typu zestawu .NET*, zostanie otwarte okno dialogowe **Dodawanie klasy LobSystem zestawu platformy .NET** .

4. Jeśli zostanie wyświetlone okno dialogowe, wykonaj jedną z następujących czynności:

   - Jeśli chcesz napisać kod niestandardowy i użyć projektanta do zdefiniowania metadanych dla zaimportowanego modelu, wybierz przycisk **tak** , nazwij system, a następnie wybierz przycisk **OK** .

   - W przeciwnym razie wybierz przycisk **nie** , a następnie wybierz przycisk **OK** .

     Element **modelu łączności danych firmowych** jest dodawany do projektu.

## <a name="see-also"></a>Zobacz też
- [Tworzenie modelu łączności danych firmy](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Instrukcje: Tworzenie modelu usługi BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Instrukcje: korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości i uprawnień](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Instrukcje: uwzględnianie niestandardowego zestawu w funkcji BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrowanie danych firmowych z programem SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
