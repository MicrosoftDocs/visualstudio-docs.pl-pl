---
title: 'Instrukcje: Ustawianie poleceń wdrażania programu SharePoint | Microsoft Docs'
description: Dowiedz się, jak dostosować proces wdrażania, ustawiając polecenie programu SharePoint przed wdrożeniem i po wdrożeniu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: fc1da67206e5e5c9fde1b5c595424239d1685ac7
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304388"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Instrukcje: Ustawianie poleceń wdrażania SharePoint
  Proces wdrażania można dostosować, ustawiając polecenia przed wdrożeniem i po wdrożeniu. Te polecenia są uruchamiane przed i po innych akcjach wdrażania podczas debugowania rozwiązań programu SharePoint w programie Visual Studio.

### <a name="to-add-a-pre-deployment-command"></a>Aby dodać polecenie przed wdrożeniem

1. Na pasku menu wybierz **Project**  >  **\<*ProjectName*> Właściwości** projektu.

2. Wybierz kartę **SharePoint** .

3. W polu tekstowym **wiersz polecenia przed wdrożeniem** wprowadź polecenie MS-DOS lub MSBuild, aby dostosować ten krok.

     Na przykład aby wyświetlić listę zawartości katalogu przed ukończeniem wdrożenia, wprowadź **dir**.

### <a name="to-add-a-post-deployment-command"></a>Aby dodać polecenie po wdrożeniu

1. Na pasku menu wybierz **Project**  >  **\<*ProjectName*> Właściwości** projektu.

2. Wybierz kartę **SharePoint** .

3. W polu tekstowym **wiersz polecenia po wdrożeniu** wprowadź polecenia systemu MS-DOS lub MSBuild, aby dostosować ten krok.

     Na przykład aby wyświetlić listę zawartości katalogu po zakończeniu wdrażania, wpisz **dir**. Aby użyć zmiennej MSBuild do skopiowania zestawu z katalogu kompilacji, wprowadź **Copy $ (TargetPath) c:\DeploymentDirectory**.

## <a name="see-also"></a>Zobacz też
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
