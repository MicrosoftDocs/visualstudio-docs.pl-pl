---
title: 'Instrukcje: Dodawanie odwołania do danych wyjściowych projektu | Microsoft Docs'
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
ms.openlocfilehash: bea0f39ae161d8b695f872cb634c35d0cb205c91
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016753"
---
# <a name="how-to-add-a-project-output-reference"></a>Instrukcje: Dodawanie odwołania do danych wyjściowych projektu
  Aby wdrożyć zestawy projektów spoza programu SharePoint (pliki. XAP w projektach Silverlight) do programu SharePoint, Dodaj je jako odwołanie do danych wyjściowych projektu.

 Ten proces tworzy zależność kompilacji rozwiązania między dwoma projektami. Projekty skojarzone z odwołaniami wyjściowymi projektu są kompilowane przed skompilowaniem i wdrożeniem projektu programu SharePoint.

### <a name="to-add-a-project-output-reference"></a>Aby dodać odwołanie do danych wyjściowych projektu

1. Załaduj rozwiązanie, które zawiera co najmniej jeden projekt programu SharePoint i jeden projekt spoza programu SharePoint.

2. W **Eksplorator rozwiązań**wybierz element w węźle projektu programu SharePoint.

3. W oknie **Właściwości** wybierz właściwość **odwołania danych wyjściowych projektu** , a następnie wybierz przycisk wielokropka (![ASP.net Mobile Designer](../sharepoint/media/mwellipsis.gif "Wielokropek projektanta ASP.NET Mobile")) obok niego.

4. W oknie dialogowym **odwołania do danych wyjściowych projektu** wybierz przycisk **Dodaj** .

5. W okienku właściwości wybierz strzałkę obok właściwości **typ wdrożenia** , a następnie wybierz odpowiednią wartość dla elementu spoza programu SharePoint, do którego odwołuje się odwołanie, na przykład **elementu**.

6. Wybierz strzałkę obok pozycji **Nazwa projektu**, wybierz nazwę elementu projektu spoza programu SharePoint, a następnie wybierz przycisk **OK** .

## <a name="see-also"></a>Zobacz też
- [Udostępnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Instrukcje: Oznaczanie kontrolek jako bezpiecznych formantów](../sharepoint/how-to-mark-controls-as-safe-controls.md)
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
