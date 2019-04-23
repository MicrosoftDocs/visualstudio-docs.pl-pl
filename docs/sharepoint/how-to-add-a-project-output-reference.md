---
title: 'Instrukcje: Dodawanie odwołania wyjścia projektu | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 2ae3965647416d7a8e11cf0ea5e24cef1e54a09b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079788"
---
# <a name="how-to-add-a-project-output-reference"></a>Instrukcje: Dodawanie odwołania wyjścia projektu
  Aby wdrożyć zestawy projektu programu SharePoint (lub pliki XAP w projektach programu Silverlight) do programu SharePoint, należy dodać ich jako odwołania wyjścia projektu.

 Ten proces tworzy zależność kompilacji rozwiązania, między dwa projekty. Projekty skojarzone z odwołania danych wyjściowych projektu są skompilowane, zanim projekt programu SharePoint jest utworzeniu i wdrożeniu.

### <a name="to-add-a-project-output-reference"></a>Aby dodać odwołania wyjścia projektu

1. Załaduj rozwiązanie, które zawiera co najmniej jeden projekt programu SharePoint i jeden projekt programu SharePoint.

2. W **Eksploratora rozwiązań**, wybierz element z węzła projektu programu SharePoint.

3. W **właściwości** okna, wybierz **odwołania danych wyjściowych projektu** właściwości, a następnie wybierz przycisk wielokropka (![elipsy projektanta Mobile ASP.NET](../sharepoint/media/mwellipsis.gif "ASP. Projektant Mobile NET elipsy")) przycisk obok niej.

4. W **odwołania danych wyjściowych projektu** okna dialogowego wybierz **Dodaj** przycisku.

5. W okienku właściwości wybierz strzałkę obok **typu wdrożenia** właściwości, a następnie wybierz odpowiednią wartość dla elementu programu SharePoint, odwołujesz się do, takich jak **plik elementu**.

6. Wybierz strzałkę obok **Nazwa projektu**, wybierz nazwę elementu projektu programu SharePoint, a następnie wybierz **OK** przycisku.

## <a name="see-also"></a>Zobacz także
- [Podaj informacji opakowań i wdrażania w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Instrukcje: Oznaczanie kontrolek pojęciem bezpiecznych kontrolek](../sharepoint/how-to-mark-controls-as-safe-controls.md)
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
