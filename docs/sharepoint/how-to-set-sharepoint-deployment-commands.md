---
title: 'Instrukcje: Ustawianie poleceń wdrażania SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 7664dfcfe11d7ab7dc6ab03045533bbd9e69fb9c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077787"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Instrukcje: Ustawianie poleceń wdrażania SharePoint
  Możesz dostosować proces wdrażania przez ustawienie polecenia przed wdrożeniem i po wdrożeniu. Te polecenia są uruchamiane przed i po nim inne akcje wdrażania podczas debugowania rozwiązania programu SharePoint z programu Visual Studio.

### <a name="to-add-a-pre-deployment-command"></a>Aby dodać polecenia przed wdrożeniem

1. Na pasku menu wybierz **projektu** > **\<*ProjectName*> właściwości**.

2. Wybierz **SharePoint** kartę.

3. W **wiersz polecenia przed wdrożeniem** tekstu wprowadź poleceń systemu MS-DOS lub MSBuild, aby dostosować ten krok.

     Na przykład, aby wyświetlić listę zawartości katalogu ukończenia wdrożenia, wprowadź **dir**.

### <a name="to-add-a-post-deployment-command"></a>Aby dodać polecenia po wdrożeniu

1. Na pasku menu wybierz **projektu** > **\<*ProjectName*> właściwości**.

2. Wybierz **SharePoint** kartę.

3. W **wiersz polecenia po wdrożeniu** tekstu wprowadź poleceń systemu MS-DOS lub MSBuild, aby dostosować ten krok.

     Na przykład, aby wyświetlić listę zawartości katalogu, po zakończeniu wdrożenia, wprowadź **dir**. Aby użyć zmiennej MSBuild Skopiuj zestaw z katalogu kompilacji, wprowadź **skopiuj $(TargetPath) c:\DeploymentDirectory**.

## <a name="see-also"></a>Zobacz także
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
