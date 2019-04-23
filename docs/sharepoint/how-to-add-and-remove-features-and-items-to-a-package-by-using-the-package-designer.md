---
title: 'Instrukcje: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu projektanta pakietów | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerDesign
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 654773f5a5e46960f8c015cc6f731e16332fcdd7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60094323"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>Instrukcje: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu projektanta pakietów
  Podczas tworzenia rozwiązania programu SharePoint, Visual Studio dodaje funkcje programu SharePoint domyślne do pakietu w rozwiązaniu. Przed wdrożeniem końcowego może Dodawanie i usuwanie elementów projektu programu SharePoint oraz funkcje, aby zmodyfikować pakiet programu SharePoint.

 Alternatywnie można użyć Eksploratora pakietów do dodawania i usuwania elementów projektu programu SharePoint. Można również wyświetlić i zmienić hierarchię elementów projektu programu SharePoint i funkcje, które są umieszczane w pakietu (wsp). Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu Eksploratora pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

## <a name="add-features-to-a-sharepoint-package"></a>Dodawanie funkcji do pakietu programu SharePoint
 Aby dodać funkcje do pakietu programu SharePoint, można użyć projektanta pakietów.

#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>Aby dodać funkcje programu SharePoint przy użyciu projektanta pakietów

1. Otwórz **pakietu projektanta**.

    Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Dodaj jeden lub więcej funkcji programu SharePoint, wykonując jedną lub więcej z następujących czynności:

   1. Kliknij dwukrotnie każdego elementu w **elementów w rozwiązaniu** listy, który chcesz dodać.

   2. Wybierz element, który chcesz dodać, a następnie wybierz **Dodaj** przycisku (>).

   3. Wybierz **Dodaj wszystkie** przycisku (>>) aby dodać wszystkich elementów jednocześnie.

      Można na przykład kliknij dwukrotnie element **elementów w rozwiązaniu** listy, aby dodać go do **elementów w pakiecie** listy.

      Elementy projektu programu SharePoint i funkcje są wyświetlane w **elementów w pakiecie** listy.

## <a name="remove-features-from-a-sharepoint-package"></a>Usuwanie funkcji z pakietu programu SharePoint
 Projektanta pakietów służy do usuwania funkcji do pakietu programu SharePoint.

#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>Aby usunąć funkcji programu SharePoint przy użyciu projektanta pakietów

1. W **elementów w pakiecie** , wybierz element, który chcesz usunąć, a następnie wybierz **Usuń** (<) przycisku, lub wybierz **Usuń wszystkie** przycisku (<<) do usunięcia wszystkie elementy.

     Elementy programu SharePoint są wyświetlane w **elementów w rozwiązaniu** listy.

## <a name="see-also"></a>Zobacz także
- [Tworzenie pakietów rozwiązania SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Instrukcje: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Instrukcje: Utwórz pakiet](https://msdn.microsoft.com/b24be45c-e91d-49bb-afb0-7b265404214b)
