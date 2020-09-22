---
title: Bezpieczne wdrożenie
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
ms.openlocfilehash: c838eddea5b3118c28fb33411a8c58a19d7b4a2d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810957"
---
# <a name="secure-deployment"></a>Bezpieczne wdrożenie
  Podczas tworzenia rozwiązania pakietu Office komputer deweloperski zostanie automatycznie zaktualizowany, aby umożliwić uruchomienie kodu w projekcie. Jednak podczas wdrażania rozwiązania należy podać dowody, na których należy oprzeć decyzję zaufania, podpisywanie rozwiązania za pomocą certyfikatu lub przy użyciu [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] klucza monitu zaufania. Aby uzyskać więcej informacji, zobacz [udzielanie zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 W przypadku dostosowań na poziomie dokumentu, jeśli dokument jest wdrażany w lokalizacji sieciowej, należy również dodać lokalizację dokumentu do listy zaufanych lokalizacji w centrum zaufania aplikacji pakietu Office. Aby uzyskać więcej informacji na temat sposobu ustawiania uprawnień do dokumentów na komputerach użytkowników końcowych, zobacz [Grant Trust to Documents](../vsto/granting-trust-to-documents.md).

## <a name="prevent-office-solutions-from-running-code"></a>Zapobiegaj uruchamianiu kodu w rozwiązaniach pakietu Office
 Administratorzy mogą używać rejestru, aby zapobiec uruchamianiu wszystkich rozwiązań pakietu Office na komputerze. Gdy zostanie otwarte rozwiązanie pakietu Office, które ma rozszerzenia kodu zarządzanego, Visual Studio Tools dla środowiska uruchomieniowego pakietu Office sprawdza, czy wpis o nazwie `Disabled` istnieje w ramach jednego z następujących kluczy rejestru na komputerze:

- **HKEY_CURRENT_USER \Software\Microsoft\VSTO**

- **HKEY_LOCAL_MACHINE \Software\Microsoft\VSTO**

  Aby zapobiec uruchamianiu kodu przez rozwiązania pakietu Office, należy utworzyć `Disabled` wpis w ramach jednego lub obu tych kluczy rejestru i określić jeden z następujących typów danych i wartości dla `Disabled` :

- REG_SZ lub REG_EXPAND_SZ, które są ustawione na dowolny ciąg inny niż "0" (zero).

- REG_DWORD, która jest ustawiona na dowolną wartość inną niż 0 (zero).

  Aby włączyć obsługę kodu dla rozwiązań pakietu Office, ustaw oba `Disabled` wpisy na 0 (zero) lub Usuń wpisy rejestru.

## <a name="see-also"></a>Zobacz też
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
- [Przygotowywanie komputerów do uruchamiania lub hostowania rozwiązań pakietu Office](/previous-versions/bb772092(v=vs.110))
- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)