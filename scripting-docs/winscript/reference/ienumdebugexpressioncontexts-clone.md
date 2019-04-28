---
title: IEnumDebugExpressionContexts::Clone | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExpressionContexts.Clone
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugExpressionContexts::Clone
ms.assetid: c8070ae1-120c-4b5d-bd3d-ae8fca6f9277
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0579ec43d46698f4ba1ba40a9bc7610263cc996
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963536"
---
# <a name="ienumdebugexpressioncontextsclone"></a>IEnumDebugExpressionContexts::Clone
Tworzy moduł wyliczający, który zawiera ten sam stan jako bieżący modułu wyliczającego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Clone(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppedec`  
 [out] Zwraca `IEnumDebugExpressionContexts` interfejsu klonu modułu wyliczającego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda tworzy moduł wyliczający, który zawiera ten sam stan jako bieżący modułu wyliczającego.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugExpressionContexts, interfejs](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)