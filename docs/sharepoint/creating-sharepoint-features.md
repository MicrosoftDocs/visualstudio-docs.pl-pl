---
title: Tworzenie funkcji programu SharePoint | Microsoft Docs
description: Utwórz funkcję programu SharePoint, aby pogrupować powiązane elementy projektu programu SharePoint w celu łatwiejszego wdrażania. Dodaj funkcje do rozwiązania SharePoint. Użyj projektanta funkcji.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8fc572f6fc5c0444fda619af5af49c6c2e52ac5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949119"
---
# <a name="create-sharepoint-features"></a>Tworzenie funkcji programu SharePoint
  Za pomocą funkcji SharePoint można grupować powiązane elementy projektu programu SharePoint w celu łatwiejszego wdrażania. Można tworzyć funkcje, ustawiać zakresy i oznaczyć inne funkcje jako zależności przy użyciu projektanta funkcji programu SharePoint. Projektant generuje również manifest, który jest plikiem XML, który opisuje każdą funkcję.

## <a name="add-features-to-the-sharepoint-solution"></a>Dodawanie funkcji do rozwiązania SharePoint
 Funkcję można dodać do rozwiązania programu SharePoint za pomocą Eksplorator rozwiązań lub Eksploratora pakietów. Aby dodać funkcję, można użyć jednej z poniższych metod.

- W **Eksplorator rozwiązań** Otwórz menu skrótów dla **funkcji**, a następnie wybierz polecenie **Dodaj funkcję**.

- W **Eksploratorze pakietów** Otwórz menu skrótów dla pakietu, a następnie wybierz polecenie **Dodaj funkcję**.

## <a name="using-the-feature-designer"></a>Korzystanie z projektanta funkcji
 Rozwiązanie SharePoint może zawierać jedną lub więcej funkcji programu SharePoint, które są zgrupowane w węźle funkcji w Eksplorator rozwiązań. Każda funkcja ma własny **Projektant funkcji** , którego można użyć do dostosowania właściwości funkcji. Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md). Aby odróżnić funkcje od siebie, można skonfigurować właściwości funkcji, takie jak tytuł, opis, wersja i zakres.

### <a name="feature-designer-options"></a>Opcje projektanta funkcji
 Po utworzeniu funkcji można dostosować ją przy użyciu projektanta funkcji.

 W poniższej tabeli opisano właściwości funkcji, które są wyświetlane w Projektancie funkcji.

|Właściwość|Opis|
|--------------|-----------------|
|Tytuł|Opcjonalny. Domyślny *tytuł funkcji jest* ustawiany na wartość *SolutionName* .|
|Opis|Opcjonalny. Opis funkcji programu SharePoint.|
|Zakres|Wymagane. Jeśli funkcja jest tworzona przy użyciu **Eksplorator rozwiązań**, zakres jest domyślnie ustawiany na Web.<br /><br /> -Farma: Aktywuj funkcję dla całej farmy serwerów.<br /><br /> -Site: Aktywuj funkcję dla wszystkich witryn sieci Web w zbiorze witryn.<br /><br /> -Web: Aktywuj funkcję dla określonej witryny sieci Web.<br /><br /> -WebApplication: Aktywuj funkcję dla wszystkich witryn sieci Web w aplikacji sieci Web.|
|Elementy w rozwiązaniu|Wszystkie elementy programu SharePoint, które można dodać do funkcji.|
|Elementy w funkcji|Elementy projektu programu SharePoint, które zostały dodane do funkcji.|

## <a name="add-and-remove-sharepoint-project-items"></a>Dodawanie i usuwanie elementów projektu programu SharePoint
 Możesz wybrać elementy projektu programu SharePoint, do których chcesz dodać funkcję programu SharePoint do wdrożenia. Za pomocą **projektanta funkcji** można dodawać i usuwać elementy do funkcji oraz wyświetlać manifest funkcji. Aby uzyskać więcej informacji, zobacz [How to: Add and Remove Items to SharePoint Features](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).

## <a name="add-feature-dependencies"></a>Dodawanie zależności funkcji
 Można skonfigurować manifest funkcji tak, aby serwer programu SharePoint uaktywniał pewne funkcje przed aktywowaniem funkcji. Na przykład, jeśli funkcja programu SharePoint zależy od innych funkcji dla funkcjonalności lub danych, serwer programu SharePoint może najpierw spróbować aktywować dowolne funkcje, od których zależy dana funkcja. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie zależności funkcji](../sharepoint/how-to-add-and-remove-feature-dependencies.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Dostosowywanie funkcji programu SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Instrukcje: Dodawanie i usuwanie elementów do funkcji programu SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
- [Instrukcje: Dodawanie i usuwanie zależności funkcji](../sharepoint/how-to-add-and-remove-feature-dependencies.md)
