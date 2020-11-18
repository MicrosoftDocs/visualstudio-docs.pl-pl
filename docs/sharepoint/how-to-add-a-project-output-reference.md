---
title: 'Instrukcje: Dodawanie odwołania do danych wyjściowych projektu | Microsoft Docs'
description: Dowiedz się, jak dodać odwołanie do danych wyjściowych projektu, tak aby można było wdrożyć zestawy projektów spoza programu SharePoint (lub pliki XAP w projektach Silverlight) do programu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 03980eea9d16cde2b6f079e0b33973958fed7a7f
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2020
ms.locfileid: "94849873"
---
# <a name="how-to-add-a-project-output-reference"></a>Instrukcje: Dodawanie odwołania do danych wyjściowych projektu
  Aby wdrożyć zestawy projektów spoza programu SharePoint (pliki. XAP w projektach Silverlight) do programu SharePoint, Dodaj je jako odwołanie do danych wyjściowych projektu.

 Ten proces tworzy zależność kompilacji rozwiązania między dwoma projektami. Projekty skojarzone z odwołaniami wyjściowymi projektu są kompilowane przed skompilowaniem i wdrożeniem projektu programu SharePoint.

### <a name="to-add-a-project-output-reference"></a>Aby dodać odwołanie do danych wyjściowych projektu

1. Załaduj rozwiązanie, które zawiera co najmniej jeden projekt programu SharePoint i jeden projekt spoza programu SharePoint.

2. W **Eksplorator rozwiązań** wybierz element w węźle projektu programu SharePoint.

3. W oknie **Właściwości** wybierz właściwość **odwołania danych wyjściowych projektu** , a następnie wybierz przycisk wielokropka (![ASP.net Mobile Designer](../sharepoint/media/mwellipsis.gif "Wielokropek projektanta ASP.NET Mobile")) obok niego.

4. W oknie dialogowym **odwołania do danych wyjściowych projektu** wybierz przycisk **Dodaj** .

5. W okienku właściwości wybierz strzałkę obok właściwości **typ wdrożenia** , a następnie wybierz odpowiednią wartość dla elementu spoza programu SharePoint, do którego odwołuje się odwołanie, na przykład **elementu**.

6. Wybierz strzałkę obok pozycji **Nazwa projektu**, wybierz nazwę elementu projektu spoza programu SharePoint, a następnie wybierz przycisk **OK** .

## <a name="see-also"></a>Zobacz także
- [Udostępnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Instrukcje: Oznaczanie kontrolek jako bezpiecznych formantów](../sharepoint/how-to-mark-controls-as-safe-controls.md)
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
