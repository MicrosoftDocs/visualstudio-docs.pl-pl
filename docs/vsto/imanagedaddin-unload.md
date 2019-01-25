---
title: IManagedAddin::Unload
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 68ef36185c193263db386a1e1f80877c0327440c
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874344"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Wywoływana tuż przed zarządzanych dodatku narzędzi VSTO dla programów nie jest załadowany.  
  
## <a name="syntax"></a>Składnia  
  
```csharp
HRESULT Unload();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość HRESULT, która wskazuje, czy metoda została ukończona pomyślnie.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie jest wywoływana przez bieżącej wersji pakietu Microsoft Office. Ta metoda jest zarezerwowana do użytku w przyszłości.  
  
## <a name="see-also"></a>Zobacz także  
 [Imanagedaddin — interfejs](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Load](../vsto/imanagedaddin-load.md)  
