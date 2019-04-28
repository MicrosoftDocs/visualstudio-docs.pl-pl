---
title: IDebugAsyncOperation::QueryIsComplete | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.QueryIsComplete
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::QueryIsComplete
ms.assetid: fcf6e229-4d40-46d9-ab81-d3561bc8e084
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de686f146fded1e4b53914a1de706025f6680ab6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822009"
---
# <a name="idebugasyncoperationqueryiscomplete"></a>IDebugAsyncOperation::QueryIsComplete
Określa, jeśli operacja debugowania została zakończona.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT QueryIsComplete();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Operacja została zakończona.|  
|`S_FALSE`|Operacja nie została zakończona.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda określa, jeśli operacja debugowania została zakończona.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugAsyncOperation, interfejs](../../winscript/reference/idebugasyncoperation-interface.md)