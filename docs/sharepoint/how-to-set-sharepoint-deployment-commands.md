---
title: 'Instrukcje: Ustawianie poleceń wdrażania programu SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c2329efef64e7d8605f8483ff7dce3107cd702fa
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015511"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Instrukcje: Ustawianie poleceń wdrażania SharePoint
  Proces wdrażania można dostosować, ustawiając polecenia przed wdrożeniem i po wdrożeniu. Te polecenia są uruchamiane przed i po innych akcjach wdrażania podczas debugowania rozwiązań programu SharePoint w programie Visual Studio.

### <a name="to-add-a-pre-deployment-command"></a>Aby dodać polecenie przed wdrożeniem

1. Na pasku menu wybierz **Project**  >  ** \<*ProjectName*> Właściwości**projektu.

2. Wybierz kartę **SharePoint** .

3. W polu tekstowym **wiersz polecenia przed wdrożeniem** wprowadź polecenie MS-DOS lub MSBuild, aby dostosować ten krok.

     Na przykład aby wyświetlić listę zawartości katalogu przed ukończeniem wdrożenia, wprowadź **dir**.

### <a name="to-add-a-post-deployment-command"></a>Aby dodać polecenie po wdrożeniu

1. Na pasku menu wybierz **Project**  >  ** \<*ProjectName*> Właściwości**projektu.

2. Wybierz kartę **SharePoint** .

3. W polu tekstowym **wiersz polecenia po wdrożeniu** wprowadź polecenia systemu MS-DOS lub MSBuild, aby dostosować ten krok.

     Na przykład aby wyświetlić listę zawartości katalogu po zakończeniu wdrażania, wpisz **dir**. Aby użyć zmiennej MSBuild do skopiowania zestawu z katalogu kompilacji, wprowadź **Copy $ (TargetPath) c:\DeploymentDirectory**.

## <a name="see-also"></a>Zobacz także
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
