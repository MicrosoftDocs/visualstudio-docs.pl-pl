---
title: 'Instrukcje: podpisywanie rozwiązań pakietu Office'
description: Dowiedz się, w jaki sposób można udzielić zaufania do rozwiązania Microsoft Office przy użyciu certyfikatu jako dowodu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3135962c8476fdb6970fc137e689c638299f8f81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927642"
---
# <a name="how-to-sign-office-solutions"></a>Instrukcje: podpisywanie rozwiązań pakietu Office
  Po podpisaniu rozwiązania można udzielić zaufania do rozwiązania przy użyciu certyfikatu jako dowodu. Możesz użyć tego samego certyfikatu dla wielu rozwiązań, a wszystkie rozwiązania będą zaufane bez dodatkowych aktualizacji zasad zabezpieczeń.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 W przypadku ręcznego edytowania manifestów aplikacji i wdrażania przy użyciu Narzędzie tworzenia i edycji manifestów (*mage.exe* i *mageui.exe*) należy je zarejestrować przed użyciem. Aby uzyskać więcej informacji, zobacz [jak: ponowne podpisywanie aplikacji i manifestów wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="sign-by-using-a-certificate"></a>Logowanie przy użyciu certyfikatu
 Certyfikat to plik zawierający unikatowy klucz i tożsamość wydawcy rozwiązania. Można zakupić certyfikaty z urzędu certyfikacji lub utworzyć własny certyfikat oraz podpisać go za pomocą urzędu certyfikacji.

 Program Visual Studio podpisuje rozwiązania pakietu Office z certyfikatem tymczasowym w celu włączenia debugowania. Certyfikatu tymczasowego nie należy używać w ramach wdrożonych rozwiązań jako dowodu.

### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Aby podpisać rozwiązanie pakietu Office przy użyciu certyfikatu

1. W menu **projekt** kliknij pozycję właściwości _rozwiązania_.

2. Kliknij kartę **podpisywanie** .

3. Wybierz pozycję **Podpisz manifesty ClickOnce**.

4. Znajdź certyfikat, klikając **pozycję Wybierz z magazynu** lub **wybierając pozycję z pliku** i przechodząc do certyfikatu.

5. Aby sprawdzić, czy jest używany prawidłowy certyfikat, kliknij pozycję **więcej szczegółów** , aby wyświetlić informacje o certyfikacie.

## <a name="see-also"></a>Zobacz też

- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
- [Udzielanie zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md)
- [Strona podpisywania, Projektant projektu](../ide/reference/signing-page-project-designer.md)
