---
title: IDebugExpressionContext::GetLanguageInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext.GetLanguageInfo
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::GetLanguageInfo
ms.assetid: 35e25662-0b2a-4c3f-bce4-f01726bc04a8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed5546f07a81d9c2825f3dbdc4f2bb28887948f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946293"
---
# <a name="idebugexpressioncontextgetlanguageinfo"></a>IDebugExpressionContext::GetLanguageInfo
Zwraca nazwę i identyfikator GUID dla języka, który jest właścicielem tego kontekstu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetLanguageInfo(  
   BSTR*  pbstrLanguageName,  
   GUID*  pLanguageID  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrLanguageName`  
 [out] Nazwa języka.  
  
 `pLanguageID`  
 [out] Unikatowy identyfikator dla tego języka.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca nazwę i identyfikator GUID dla języka, który jest właścicielem tego kontekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExpressionContext, interfejs](../../winscript/reference/idebugexpressioncontext-interface.md)