---
title: IDebugSyncOperation::InProgressAbort | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: a794ea70d6d2fe937afb311e6961d53f22bd7ac2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004833"
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