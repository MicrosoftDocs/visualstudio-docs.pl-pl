---
title: 'Projektant pakietów: Dodawanie & usuwanie funkcji i elementów do pakietu'
titleSuffix: ''
description: Zapoznaj się z tematem Dodawanie i usuwanie funkcji oraz elementów do pakietu programu SharePoint przy użyciu projektanta pakietów w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 45c8da30a059599a291b18155dc48c4521d6d875
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914949"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>Instrukcje: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu projektanta pakietów
  Podczas tworzenia rozwiązania programu SharePoint program Visual Studio dodaje domyślne funkcje programu SharePoint do pakietu w rozwiązaniu. Przed ostatecznym wdrożeniem można dodawać i usuwać elementy projektu programu SharePoint oraz funkcje, aby zmodyfikować pakiet programu SharePoint.

 Alternatywnie można użyć Eksploratora pakietów do dodawania i usuwania elementów projektu programu SharePoint. Możesz również wyświetlić i zmienić hierarchię elementów projektu programu SharePoint i funkcji umieszczanych w pakiecie (wsp). Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu Eksploratora pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

## <a name="add-features-to-a-sharepoint-package"></a>Dodawanie funkcji do pakietu programu SharePoint
 Za pomocą projektanta pakietów można dodawać funkcje do pakietu programu SharePoint.

#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>Aby dodać funkcje programu SharePoint za pomocą projektanta pakietów

1. Otwórz **projektanta pakietów**.

    Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Dodaj co najmniej jedną funkcję programu SharePoint, wykonując następujące czynności:

   1. Kliknij dwukrotnie każdy element w elementach listy **rozwiązań** , który chcesz dodać.

   2. Wybierz element, który chcesz dodać, a następnie wybierz przycisk **Dodaj** (>).

   3. Wybierz przycisk **Dodaj wszystko** (>>), aby dodać wszystkie elementy jednocześnie.

      Na przykład można kliknąć dwukrotnie element w elementach **na liście rozwiązania** , aby dodać go do **elementów na liście pakietów** .

      Elementy projektu programu SharePoint i funkcje pojawiają się na liście **elementów listy pakietów** .

## <a name="remove-features-from-a-sharepoint-package"></a>Usuwanie funkcji z pakietu programu SharePoint
 Możesz użyć projektanta pakietów, aby usunąć funkcje pakietu programu SharePoint.

#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>Aby usunąć funkcje programu SharePoint za pomocą projektanta pakietów

1. Z listy **elementy na liście pakiet** wybierz element, który chcesz usunąć, a następnie wybierz przycisk **Usuń** (<) lub wybierz przycisk **Usuń wszystko** (<<), aby usunąć wszystkie elementy.

     Elementy programu SharePoint są wyświetlane w **elementach listy rozwiązań** .

## <a name="see-also"></a>Zobacz też
- [Tworzenie pakietów rozwiązania SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Instrukcje: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Instrukcje: Tworzenie pakietu](/previous-versions/ee231585(v=vs.110))