---
title: Zabezpieczanie wdrożenia
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1000504ad83706bd028af4bd668da7483e478b7a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56604928"
---
# <a name="secure-deployment"></a>Zabezpieczanie wdrożenia
  Podczas tworzenia rozwiązań pakietu Office, komputer deweloperski jest aktualizowany automatycznie uruchamianie kodu w projekcie do uruchomienia. Jednak podczas wdrażania rozwiązania, należy podać dowód, na którym można oprzeć decyzji o zaufaniu rozwiązania przy użyciu certyfikatu podpisywania lub używając [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] klucz monitu zaufania. Aby uzyskać więcej informacji, zobacz [udzielenia zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Przypadku dostosowań na poziomie dokumentu w przypadku wdrożenia dokument do lokalizacji sieciowej, należy również dodać lokalizacji tego dokumentu do listy zaufanych lokalizacji w Centrum zaufania w aplikacji pakietu Office. Aby uzyskać więcej informacji na temat sposobu ustawiania uprawnień do dokumentu na komputerach użytkowników końcowych, zobacz [udzielenia zaufania do dokumentów](../vsto/granting-trust-to-documents.md).

## <a name="prevent-office-solutions-from-running-code"></a>Uniemożliwienie rozwiązań pakietu Office kodu
 Administratorzy mogą używać rejestru, aby zapobiec wszystkich rozwiązań pakietu Office na komputerze z systemem. Gdy rozwiązań pakietu Office, który zawiera rozszerzenia kodu zarządzanego jest otwarty, Visual Studio Tools for Office runtime kontroli czy wpisu o nazwie `Disabled` istnieje w jednej z następujących kluczy rejestru na komputerze:

- **HKEY_CURRENT_USER\Software\Microsoft\VSTO**

- **HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO**

  Aby uniemożliwić uruchamianie kodu rozwiązań pakietu Office, należy utworzyć `Disabled` wpis w co najmniej jeden z tych kluczy rejestru i określ jedną z następujących typów danych i wartości dla `Disabled`:

- REG_SZ lub REG_EXPAND_SZ, który jest ustawiony na dowolny ciąg, innego niż "0" (zero).

- REG_DWORD, który jest ustawiony na wartość inną niż 0 (zero).

  Aby włączyć rozwiązań pakietu Office uruchomić kod, ustaw obie `Disabled` wpisy na 0 (zero), lub Usuń wpisy rejestru.

## <a name="see-also"></a>Zobacz także
- [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)
- [Przygotowywanie komputerów pozwala uruchamiać lub hostować rozwiązań pakietu Office](https://msdn.microsoft.com/be1b173f-7261-4d74-aa4e-94ccd43db8d8)
- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
