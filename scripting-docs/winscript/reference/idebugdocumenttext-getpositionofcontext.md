---
title: IDebugDocumentText::GetPositionOfContext | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetPositionOfContext
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetPositionOfContext
ms.assetid: 90fec730-c3fb-45fb-92ef-05ecc90dca38
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6058502c076dd4f75dbbb44fdb161b889a965fec
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58145125"
---
# <a name="idebugdocumenttextgetpositionofcontext"></a>IDebugDocumentText::GetPositionOfContext
Zwraca zakres pozycji znaku odpowiadający kontekstu dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetPositionOfContext(  
   IDebugDocumentContext*  psc,  
   ULONG*                  pcCharacterPosition,  
   ULONG*                  cNumChars  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `psc`  
 [in] Obiekt kontekstu dokumentu.  
  
 `pcCharacterPosition`  
 [out] Lokalizacja z zakresu znaków pozycja początkowa.  
  
 `cNumChars`  
 [out] Liczba znaków w zakresie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Kontekstu dokumentu, pod warunkiem do tej metody musi być skojarzony z tym dokumentem.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentText, interfejs](../../winscript/reference/idebugdocumenttext-interface.md)