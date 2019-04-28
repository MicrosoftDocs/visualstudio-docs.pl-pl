---
title: IJsEnumDebugProperty::Next, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsEnumDebugProperty.Next
apilocation:
- jscript9diag.dll
ms.assetid: 9fad1893-483a-440c-88c1-469494212300
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ec6a1dded8c24de06a5746261a19b6609a97ada
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977542"
---
# <a name="ijsenumdebugpropertynext-method"></a>IJsEnumDebugProperty::Next — Metoda
Odczytuje właściwości tego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Next(  
   ULONG count,  
   IJsDebugProperty **ppDebugProperty,  
   ULONG *pActualCount  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `count`  
 [in] Liczba znaków do odczytania.  
  
 `ppDebugProperty`  
 [out] Obiekt reprezentujący przeglądarkę właściwości.  
  
 `pActualCount`  
 [out] Rzeczywista liczba właściwości obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [IJsEnumDebugProperty, interfejs](../../winscript/reference/ijsenumdebugproperty-interface.md)