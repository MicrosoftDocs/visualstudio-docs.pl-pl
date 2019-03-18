---
title: IDebugApplication::StepOutComplete | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 04f8ecfb835199afa0a60f3fde3c8fbdc8812240
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58153139"
---
# <a name="idebugapplicationstepoutcomplete"></a>IDebugApplication::StepOutComplete
Powiadamia Menedżer debugowania procesów, że aparat języka, w trybie pojedynczego kroku zostanie powrócić do obiektu wywołującego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT StepOutComplete();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Aparaty języka wywołać tę metodę w trybie pojedynczego kroku przed powrócą do wywołującego ich. Menedżer debugowania procesów używa tej możliwości, aby powiadomić wszystkich innych aparatów skryptów, które dzielą powinny one przy okazji pierwszego. Ta technika jest jak między językami kroku tryby są implementowane.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugApplication, interfejs](../../winscript/reference/idebugapplication-interface.md)