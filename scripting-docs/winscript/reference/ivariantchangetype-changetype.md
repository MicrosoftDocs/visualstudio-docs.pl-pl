---
title: IVariantChangeType::ChangeType | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 0a02b8a3991ff6d20370cd4a2ea4cd87aa9a1226
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086583"
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