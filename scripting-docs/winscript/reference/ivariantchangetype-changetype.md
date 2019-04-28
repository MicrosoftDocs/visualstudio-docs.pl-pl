---
title: IVariantChangeType::ChangeType | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IVariantChangeType.ChangeType
apilocation:
- scrobj.dll
helpviewer_keywords:
- IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81ed0a8502e9b0cfc53725621d477d34ee5010ea
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945637"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Pobiera wartość wariantu i tworzy nowy wariant z określonym typem.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pvarDst`  
 [out w] Wariant będzie zawierać wynik, reprezentowane przez `pvarSrc`, ale z typu określonego przez `vtNew`.  
  
 `pvarSrc`  
 [in] Wartość wariantu, aby zmienić do nowego typu.  
  
 `lcid`  
 [in] Ustawienia regionalne kontekstu do użycia podczas konwertowania argumenty do lub z ciągami.  
  
 `vtNew`  
 [in] Określa typ `pvarDst` stać się.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 `pvarDst` i `pvarSrc` argumenty mogą być równe, w którym to przypadku jest zastępowany oryginalną wartość. Ta metoda przekazuje `pvarDst` do `VariantClear` funkcji, a w konsekwencji `pvarDst` powinna być inicjowana na prawidłową wartość.  
  
## <a name="see-also"></a>Zobacz też  
 [IVariantChangeType, interfejs](../../winscript/reference/ivariantchangetype-interface.md)