---
title: 'IVariantChangeType:: ChangeType | Microsoft Docs'
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
ms.openlocfilehash: 406d5d8486b3016f0105b7bd8bf231db0e1e9613
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571779"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Przyjmuje wartość wariantu i tworzy nowy wariant o określonym typie.  
  
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
 [in. out] Wariant zawierający wartość reprezentowaną przez `pvarSrc`, ale z typem określonym przez `vtNew`.  
  
 `pvarSrc`  
 podczas Wartość wariantu do zmiany na nowy typ.  
  
 `lcid`  
 podczas Kontekst ustawień regionalnych, który ma być używany podczas konwertowania argumentów na lub z ciągów.  
  
 `vtNew`  
 podczas Określa typ `pvarDst`, który ma zostać przekształcony.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Argumenty `pvarDst` i `pvarSrc` mogą być równe, w takim przypadku oryginalna wartość jest zastępowana. Ta metoda przekazuje `pvarDst` do funkcji `VariantClear`, w związku z czym `pvarDst` powinna zostać zainicjowana do prawidłowej wartości.  
  
## <a name="see-also"></a>Zobacz także  
 [IVariantChangeType, interfejs](../../winscript/reference/ivariantchangetype-interface.md)