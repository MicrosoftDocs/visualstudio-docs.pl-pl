---
title: IDebugDocumentHelper::GetScriptBlockInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.GetScriptBlockInfo
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::GetScriptBlockInfo
ms.assetid: 332d7540-bbbe-4747-95ec-e47384d4f4e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1984cdc19beb883dd7ee82f58497b11a8d781b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62549718"
---
# <a name="idebugdocumenthelpergetscriptblockinfo"></a>IDebugDocumentHelper::GetScriptBlockInfo
Pobiera zakres znaków i aparat skryptów odpowiadający blok skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetScriptBlockInfo(  
   DWORD_PTR        dwSourceContext,  
   IActiveScript**  ppasd,  
   ULONG*           piCharPos,  
   ULONG*           pcChars  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwSourceContext`  
 [in] Kontekst źródła dla bloku skryptu.  
  
 `ppasd`  
 [out] Aparat skryptów dla tego bloku skryptu.  
  
 `piCharPos`  
 [out] Lokalizacja początku bloku skryptu.  
  
 `cChars`  
 [out] Liczba znaków w bloku skryptu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda pobiera zakres znaków i aparat skryptów odpowiadający blok skryptu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentHelper, interfejs](../../winscript/reference/idebugdocumenthelper-interface.md)