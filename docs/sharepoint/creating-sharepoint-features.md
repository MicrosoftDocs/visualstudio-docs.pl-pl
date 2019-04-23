---
title: Tworzenie funkcji SharePoint | Dokumentacja firmy Microsoft
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d3f453770dbb389a688db0a9edcc8e97e179858
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60051323"
---
# <a name="create-sharepoint-features"></a>Tworzenie funkcji SharePoint
  Funkcja programu SharePoint można użyć do grupowania powiązanych elementów projektu programu SharePoint dla łatwiejsze wdrażanie. Możesz tworzyć funkcje, ustaw zakresy i oznaczyć inne funkcje za pomocą programu SharePoint Designer funkcji jako zależności. Projektant generuje również manifest, który jest plikiem XML, który opisuje każdą z funkcji.

## <a name="add-features-to-the-sharepoint-solution"></a>Dodawanie funkcji do rozwiązań SharePoint
 Funkcję można dodać do rozwiązania programu SharePoint przy użyciu Eksploratora rozwiązań lub Eksploratora pakietów. Można dodać funkcji, można użyć jednej z następujących metod.

- W **Eksploratora rozwiązań**, otwórz menu skrótów dla **funkcji**, a następnie wybierz **Dodaj funkcję**.

- W **Eksploratora pakietów**, otwórz menu skrótów dla pakietu, a następnie wybierz **Dodaj funkcję**.

## <a name="using-the-feature-designer"></a>Za pomocą projektanta funkcji
 Rozwiązania programu SharePoint może zawierać jedną lub więcej funkcji programu SharePoint, które są pogrupowane w węźle funkcji w Eksploratorze rozwiązań. Każda funkcja ma swój własny **projektanta funkcji** służące do dostosowywania właściwości funkcji. Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md). Aby rozróżnić funkcje od siebie nawzajem, można skonfigurować właściwości funkcji, takich jak tytuł, opis, wersji i zakresu.

### <a name="feature-designer-options"></a>Opcje projektanta funkcji
 Po utworzeniu funkcji, można użyć projektanta funkcji zgodnie z własnymi.

 W poniższej tabeli opisano właściwości funkcji, które są wyświetlane w Projektancie funkcji.

|Właściwość|Opis|
|--------------|-----------------|
|Tytuł|Opcjonalna. Ustawiono domyślny tytuł funkcji *SolutionName* *FeatureName*.|
|Opis|Opcjonalna. Opis funkcji programu SharePoint.|
|Zakres|Wymagana. Jeśli funkcja jest tworzona przy użyciu **Eksploratora rozwiązań**, zakres jest domyślnie w sieci Web.<br /><br /> -Farmy: Aktywuj funkcję dla całej farmy serwerów.<br /><br /> -Lokacja: Aktywuj funkcję dla wszystkich witryn sieci web w zbiorze witryn.<br /><br /> -Sieci web: Aktywuj funkcję dla określonej witryny sieci web.<br /><br /> -WebApplication: Aktywuj funkcję dla wszystkich witryn sieci web w aplikacji sieci web.|
|Elementów w rozwiązaniu|Wszystkie elementy programu SharePoint, które mogą być dodawane do tej funkcji.|
|Elementy w funkcji|Elementy projektu programu SharePoint, które zostały dodane do funkcji.|

## <a name="add-and-remove-sharepoint-project-items"></a>Dodawanie i usuwanie elementów projektu programu SharePoint
 Możesz wybrać elementy projektu programu SharePoint, które chcesz dodać funkcję programu SharePoint do wdrożenia. Użyj **projektanta funkcji** do dodawania i usuwania elementów do funkcji i wyświetlić manifest funkcji. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie elementów do funkcji SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).

## <a name="add-feature-dependencies"></a>Dodaj zależności funkcji
 Manifest funkcji można skonfigurować tak, aby serwer programu SharePoint aktywuje niektórych funkcji, zanim Twoja funkcja jest aktywowana. Na przykład jeśli Twojej funkcji programu SharePoint jest zależna od innych funkcji dla funkcji lub dane, serwer programu SharePoint można najpierw spróbują aktywować żadnych funkcji, które Twoja funkcja jest zależna od. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie zależności funkcji](../sharepoint/how-to-add-and-remove-feature-dependencies.md).

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Instrukcje: Dodawanie i usuwanie elementów do funkcji SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
- [Instrukcje: Dodawanie i usuwanie zależności funkcji](../sharepoint/how-to-add-and-remove-feature-dependencies.md)
