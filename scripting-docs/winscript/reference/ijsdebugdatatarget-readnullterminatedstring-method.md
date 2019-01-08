---
title: IJsDebugDataTarget::ReadNullTerminatedString, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadNullTerminatedString
apilocation:
- jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a681dcedf873f0cb96f47b14278f47271cd43ec8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093330"
---
# <a name="ijsdebugdatatargetreadnullterminatedstring-method"></a>IJsDebugDataTarget::ReadNullTerminatedString — Metoda
Odczytuje określoną liczbę znaków z obiektu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [in] Adres do odczytu.  
  
 `characterSize`  
 [in] rozmiar każdego znaku w ciągu  
  
 `maxCharacters`  
 [in] Maksymalna liczba znaków do odczytania. wartość elementu maxCharacters nie powinna być wygórowana. Każdy wniosek o więcej niż 128MB pamięci zakończy się niepowodzeniem.  Jeśli ten ciąg jest większy niż wartość elementu maxCharacters, ciąg wyniku zostanie obcięty po wartość elementu maxCharacters.  
  
 `pString`  
 [out] Odczyt BSTR z celu.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Zwraca wartość S_FALSE, jeśli obcięte.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [IJsDebugDataTarget, interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)