---
title: Zabezpieczanie wdrożenia
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 852e66bb4e29e732093cdac6b44c6791ad9b772d
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671083"
---
# <a name="secure-deployment"></a>Zabezpieczanie wdrożenia
  Podczas tworzenia rozwiązań pakietu Office, komputer deweloperski jest aktualizowany automatycznie uruchamianie kodu w projekcie do uruchomienia. Jednak podczas wdrażania rozwiązania, należy podać dowód, na którym można oprzeć decyzji o zaufaniu rozwiązania przy użyciu certyfikatu podpisywania lub używając [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] klucz monitu zaufania. Aby uzyskać więcej informacji, zobacz [udzielenia zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Przypadku dostosowań na poziomie dokumentu w przypadku wdrożenia dokument do lokalizacji sieciowej, należy również dodać lokalizacji tego dokumentu do listy zaufanych lokalizacji w Centrum zaufania w aplikacji pakietu Office. Aby uzyskać więcej informacji na temat sposobu ustawiania uprawnień do dokumentu na komputerach użytkowników końcowych, zobacz [udzielenia zaufania do dokumentów](../vsto/granting-trust-to-documents.md).  
  
## <a name="prevent-office-solutions-from-running-code"></a>Uniemożliwienie rozwiązań pakietu Office kodu  
 Administratorzy mogą używać rejestru, aby zapobiec wszystkich rozwiązań pakietu Office na komputerze z systemem. Gdy rozwiązań pakietu Office, który zawiera rozszerzenia kodu zarządzanego jest otwarty, Visual Studio Tools for Office runtime kontroli czy wpisu o nazwie `Disabled` istnieje w jednej z następujących kluczy rejestru na komputerze:  
  
- **HKEY_CURRENT_USER\Software\Microsoft\VSTO**  
  
- **Folderze**  
  
  Aby uniemożliwić uruchamianie kodu rozwiązań pakietu Office, należy utworzyć `Disabled` wpis w co najmniej jeden z tych kluczy rejestru i określ jedną z następujących typów danych i wartości dla `Disabled`:  
  
- REG_SZ lub REG_EXPAND_SZ, który jest ustawiony na dowolny ciąg, innego niż "0" (zero).  
  
- REG_DWORD, który jest ustawiony na wartość inną niż 0 (zero).  
  
  Aby włączyć rozwiązań pakietu Office uruchomić kod, ustaw obie `Disabled` wpisy na 0 (zero), lub Usuń wpisy rejestru.  
  
## <a name="see-also"></a>Zobacz także  
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Przygotowywanie komputerów pozwala uruchamiać lub hostować rozwiązań pakietu Office](https://msdn.microsoft.com/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)  
  
  