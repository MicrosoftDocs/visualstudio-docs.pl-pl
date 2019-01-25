---
title: 'Instrukcje: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu Eksploratora pakietów | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
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
ms.openlocfilehash: 1cbcdc11eab419c6f98ab1ec823c6073286ffe2f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868134"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Instrukcje: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu Eksploratora pakietów
  Aby skonfigurować pakiet do wdrożenia programu SharePoint elementy i funkcje, można użyć Eksploratora pakietów. Elementów projektu programu SharePoint i funkcje można dostosować w pliku wsp.  
  
 Alternatywnie można użyć projektanta pakietu do wyświetlania i zmieniać ich kolejność te funkcje, aby zmienić kolejność aktywacji. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu projektanta pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
## <a name="open-the-packaging-explorer"></a>Otwórz Eksploratora pakietów  
 Jeśli rozwiązanie programu Visual Studio ma co najmniej jeden projekt programu SharePoint, można użyć poniższej procedury można otworzyć Eksploratora pakietów. Alternatywnie Eksploratora pakietów zostanie otwarty automatycznie po wyświetleniu funkcji lub pakietu projektanta. Po zamknięciu wszystkich funkcji i pakietów projektantów zamyka się również Eksploratora pakietów  
  
#### <a name="to-open-the-packaging-explorer"></a>Aby otworzyć Eksploratora pakietów  
  
1.  Na pasku menu wybierz **widoku** > **Windows inne** > **Eksploratora pakietów**.  
  
     **Eksploratora pakietów** pojawia się w **przybornika**.  
  
## <a name="adding-a-feature-to-a-package"></a>Dodanie funkcji do pakietu  
 Nowe i istniejące funkcje można dodać do pakietu przy użyciu Eksploratora pakietów.  
  
#### <a name="to-add-a-sharepoint-feature"></a>Aby dodać funkcję programu SharePoint
  
1.  Otwórz **Eksploratora pakietów**, otwórz menu skrótów dla projektu, a następnie wybierz **Dodaj funkcję**.  
  
#### <a name="to-move-an-existing-sharepoint-feature"></a>Aby przenieść istniejącą funkcję programu SharePoint  
  
1.  Otwórz **Eksploratora pakietów**, a następnie wykonaj jedną z następujących czynności:  
  
    -   Przeciągnij **funkcji** z jednego projektu do innego projektu.  
  
    -   Otwórz menu skrótów dla funkcji, wybierz polecenie **Wytnij**, otwórz menu skrótów dla projektu, do którego chcesz przenieść tę funkcję, a następnie wybierz **Wklej**.  
  
    > [!NOTE]  
    >  Użyj tej procedury, jeśli masz więcej niż jeden projekt programu SharePoint w rozwiązaniu.  
  
## <a name="validate-a-feature-or-package"></a>Sprawdzanie poprawności funkcji lub pakietów  
 Potencjalne problemy w funkcji programu SharePoint i pakietów można zidentyfikować, sprawdzając poprawność plików. Ostrzeżenia i błędy są wyświetlane w oknie danych wyjściowych i oknie Lista błędów.  
  
#### <a name="to-validate-a-sharepoint-feature-or-package"></a>Aby sprawdzić poprawność funkcji programu SharePoint lub pakietu
  
1.  Otwórz **Eksploratora pakietów**.  
  
2.  Otwórz menu skrótów dla funkcji lub pakietu, a następnie wybierz **weryfikacji**.  
  
## <a name="see-also"></a>Zobacz także
 [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
