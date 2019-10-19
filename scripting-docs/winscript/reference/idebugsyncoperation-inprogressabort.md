---
title: 'IDebugSyncOperation:: InProgressAbort | Microsoft Docs'
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
ms.openlocfilehash: 40974c738c071e52648297ac90a0ab89d9681435
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576666"
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
Anuluje operację w toku w innym wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_NOTIMPL`|Nie można anulować operacji.|  
|`E_ABORT`|Nie można ukończyć operacji.|  
  
## <a name="remarks"></a>Uwagi  
 Menedżer debugowania procesów wywołuje tę metodę z wątku debugera, aby anulować operację, która jest w toku w innym wątku.  
  
 Jeśli metoda `InProgressAbort` nie może ukończyć operacji, zwraca `E_ABORT` tak szybko, jak to możliwe. Ta metoda może zwracać `E_NOTIMPL`, jeśli operacja nie może zostać anulowana.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugSyncOperation, interfejs](../../winscript/reference/idebugsyncoperation-interface.md)