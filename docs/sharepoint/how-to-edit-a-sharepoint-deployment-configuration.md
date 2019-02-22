---
title: 'Instrukcje: Edytowanie konfiguracji wdrażania SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
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
ms.openlocfilehash: 07788a8d45068b34e5e480c3a8aae8563c907791
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646190"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Instrukcje: Edytowanie konfiguracji wdrażania SharePoint
  Można utworzyć konfiguracji wdrożenia lub Modyfikuj istniejącą konfigurację wdrożenia. Na przykład możesz uruchomić jednym kroku lub zmiana kolejności kroków w procesie wdrażania. Można tworzyć lub modyfikować konfiguracje wdrożenia, ponieważ nie można zmienić konfiguracji programowo dodanych i wbudowane.

## <a name="create-a-sharepoint-deployment-configuration"></a>Tworzenie konfiguracji wdrażania SharePoint

#### <a name="to-create-a-sharepoint-deployment-configuration"></a>Aby utworzyć konfiguracji wdrażania SharePoint

1.  W **Eksploratora rozwiązań**, wybierz projekt programu SharePoint, a następnie na pasku menu wybierz **projektu**, _ProjectName_**właściwości**.

2.  Na **SharePoint** kartę, wybrać **New** przycisku.

     **Dodawanie nowej konfiguracji wdrożenia** pojawi się okno dialogowe.

3.  W **nazwa** tekstu wprowadź nazwę dla konfiguracji wdrażania.

4.  W **dostępne kroki związane z wdrażaniem** okienku wybierz kroki, które chcesz dodać do konfiguracji wdrożenia, wybierz (**>**) przycisk, a następnie wybierz **OK** przycisku.

    > [!NOTE]
    >  Po skonfigurowaniu polecenia przed wdrożeniem lub polecenia po wdrożeniu te kroki uruchamiane tylko wtedy, gdy należy dodać je do konfiguracji wdrożenia dostosowane.

## <a name="change-the-active-deployment-configuration"></a>Zmiana konfiguracji aktywnego wdrożenia

#### <a name="to-change-the-active-deployment-configuration"></a>Zmiana konfiguracji aktywnego wdrożenia

1.  W **Eksploratora rozwiązań**, wybierz projekt programu SharePoint, a następnie na pasku menu wybierz **projektu** > **\<*ProjectName*> Właściwości**.

2.  Wybierz **SharePoint** kartę.

3.  W **aktywnej konfiguracji wdrożenia** pola listy, wybierz nazwę konfiguracji wdrożenia, którego chcesz używać.

## <a name="see-also"></a>Zobacz także
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
