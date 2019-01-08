---
title: IJsDebugProperty::GetMembers, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProperty.GetMembers
apilocation:
- jscript9diag.dll
ms.assetid: a32b5372-d9cb-4b9a-9bc2-81b5e1df365c
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 351862f488aceb5fd3e9176cc4676e70b197d803
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087030"
---
# <a name="ijsdebugpropertygetmembers-method"></a>IJsDebugProperty::GetMembers — Metoda
Pobiera elementy członkowskie tego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetMembers(  
   JS_PROPERTY_MEMBERS members,  
   IJsEnumDebugProperty **ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `members`  
 [in] Flagi określające, co obejmuje informacje o członkach.  
  
 `ppEnum`  
 [out] Elementy członkowskie obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [IJsDebugProperty, interfejs](../../winscript/reference/ijsdebugproperty-interface.md)