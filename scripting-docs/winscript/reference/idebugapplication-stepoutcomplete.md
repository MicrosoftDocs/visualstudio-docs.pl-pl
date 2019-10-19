---
title: 'IDebugApplication:: StepOutComplete | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.StepOutComplete
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::StepOutComplete
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f50d7e8a8936e52f4177450e7d163c4cfeaa55df
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571038"
---
# <a name="idebugapplicationstepoutcomplete"></a>IDebugApplication::StepOutComplete
Powiadamia Menedżera debugowania procesów, że aparat języka w trybie pojedynczego kroku ma zwrócić do obiektu wywołującego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT StepOutComplete();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Aparaty języka wywołują tę metodę w trybie pojedynczego kroku tuż przed zwróceniem ich do obiektu wywołującego. Menedżer debugowania procesów używa tej możliwości do powiadomienia wszystkich innych aparatów skryptów, które powinny być w pierwszej kolejności zerwane. Ta technika polega na tym, jak są implementowane tryby etapów wielu języków.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugApplication, interfejs](../../winscript/reference/idebugapplication-interface.md)