---
title: 'Instrukcje: Dodawanie pliku zasobów | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 657eb473adcff40a62d2fc9b09518ebe8135eeb4
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015183"
---
# <a name="how-to-add-a-resource-file"></a>Instrukcje: Dodawanie pliku zasobów
  Polecenia służące do dodawania plików zasobów znajduje się w menu skrótów węzła rozwiązania i funkcji w Eksplorator rozwiązań. Aby uzyskać więcej informacji, zobacz [Lokalizowanie rozwiązań SharePoint](../sharepoint/localizing-sharepoint-solutions.md).

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Aby dodać globalny plik zasobów do rozwiązania programu SharePoint

1. W programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwórz rozwiązanie SharePoint.

2. W **Eksplorator rozwiązań**wybierz węzeł projektu programu SharePoint, a następnie na pasku menu wybierz pozycję **projekt**  >  **Dodaj nowy element**.

3. W oknie dialogowym **Dodaj nowy element** wybierz szablon **plik zasobów globalnych** , a następnie wybierz przycisk **Dodaj** .

   > [!NOTE]
   > Szablon elementu projekt pliku zasobów globalnych pojawia się tylko wtedy, gdy wybrano element projektu programu SharePoint.

4. W oknie dialogowym **Dodawanie zasobu** wybierz kulturę dla pliku zasobów, na przykład angielski (Stany Zjednoczone).

    Ten krok powoduje dodanie globalnego pliku zasobów do rozwiązania w formacie, Resource_x_**.** <em>kultura</em><strong>.</strong> resx, np. *Resource1. pl-US. resx*.

5. Gdy **Edytor zasobów** zostanie otwarty w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , Dodaj zasoby do pliku zasobów.

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Aby dodać plik zasobów funkcji do funkcji programu SharePoint

1. Jeśli rozwiązanie SharePoint nie jest jeszcze otwarte w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , Otwórz rozwiązanie.

2. W **Eksplorator rozwiązań**Otwórz menu skrótów dla nazwy funkcji w węźle **funkcje** , a następnie wybierz pozycję **Dodaj zasób funkcji**.

     Ten krok powoduje dodanie pliku zasobów do funkcji w formacie, _nazwaplikuzasobów_**.** _Culture_**. resx**, np. *Feature1. pl-US. resx*.

3. Gdy **Edytor zasobów** zostanie otwarty w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , Dodaj zasoby do pliku zasobów.

## <a name="see-also"></a>Zobacz także
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
