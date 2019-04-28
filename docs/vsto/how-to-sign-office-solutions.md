---
title: 'Instrukcje: Podpisywanie rozwiązań pakietu Office'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1fff7555c17f4fdac43de2690f8e133cc32881db
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62971124"
---
# <a name="how-to-sign-office-solutions"></a>Instrukcje: Podpisywanie rozwiązań pakietu Office
  Jeśli utworzysz rozwiązanie, możesz udzielić zaufania do rozwiązania przy użyciu certyfikatu jako dowód. Możesz użyć tego samego certyfikatu dla wielu rozwiązań, a wszystkie rozwiązania pozostaną zaufane, nie dodatkowe aktualizacje zasad.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Jeśli ręcznie edytować aplikację i manifesty wdrożenia za pomocą narzędzia do edytowania i Manifest Generation (*mage.exe* i *mageui.exe*), musisz ją ponownie podpisać manifesty, zanim będzie można ich użyć. Aby uzyskać więcej informacji, zobacz [jak: Ponowne podpisywanie manifestów aplikacji i wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="sign-by-using-a-certificate"></a>Zaloguj się przy użyciu certyfikatu
 Certyfikat jest plik, który zawiera unikatowego klucza oraz tożsamość wydawcy rozwiązań. Można kupić certyfikaty z urzędu certyfikacji, lub utworzyć własny certyfikat i podpisać go urzędu certyfikacji.

 Program Visual Studio podpisuje rozwiązań pakietu Office przy użyciu tymczasowego certyfikatu, aby włączyć debugowanie. Nie należy używać tymczasowy certyfikat w przypadku rozwiązań wdrożonych jako dowodu.

### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Do podpisania rozwiązania do pakietu Office przy użyciu certyfikatu

1. Na **projektu** menu, kliknij przycisk _SolutionName_**właściwości**.

2. Kliknij przycisk **podpisywanie** kartę.

3. Wybierz **Podpisz manifesty ClickOnce**.

4. Znajdź certyfikat, klikając **wybierać Store** lub **wybierz z pliku** i przejdź do certyfikatu.

5. Aby zweryfikować, że używany jest poprawny certyfikat, kliknij przycisk **więcej szczegółów** do wyświetlania informacji o certyfikacie.

## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
- [Udzielanie zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md)
- [Strona podpisywania, Projektant projektu](../ide/reference/signing-page-project-designer.md)
