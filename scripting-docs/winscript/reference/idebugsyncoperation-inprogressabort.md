---
title: IDebugSyncOperation::InProgressAbort | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.InProgressAbort
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::InProgressAbort
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cab8bae7f131d24c1a2c7272dc8d1178e12bf0e6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095527"
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
Anuluje operację w toku na inny wątek.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_NOTIMPL`|Nie można anulować operacji.|  
|`E_ABORT`|Nie można ukończyć operacji.|  
  
## <a name="remarks"></a>Uwagi  
 Menedżer debugowania procesów wywołuje tę metodę w z wewnątrz wątku debugera, aby anulować operację, która jest w toku w innym wątku.  
  
 Jeśli `InProgressAbort` metody nie można ukończyć operacji, zwraca `E_ABORT` tak szybko, jak to możliwe. Ta metoda może zwrócić `E_NOTIMPL` Jeśli nie można anulować operacji.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugSyncOperation, interfejs](../../winscript/reference/idebugsyncoperation-interface.md)