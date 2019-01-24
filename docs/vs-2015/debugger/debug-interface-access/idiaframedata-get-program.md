---
title: IDiaFrameData::get_program | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d87f5c7fda25a901d44b9f511b9a92eb4471f845
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54761347"
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera ciąg program, który jest używany do obliczania rejestru ustawić przed wywołaniem do bieżącej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca ciąg program.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ciąg program jest sekwencją makra jest interpretowany w celu ustanowienia prologu. Na przykład użyć ramkę stosu typowe parametry programu `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`. Format jest Polski odwrotnej notacji, gdy operatory postępuj zgodnie z argumentów. `T0` reprezentuje zmienną tymczasową na stosie. W tym przykładzie wykonuje następujące czynności:  
  
1. Przenieś zawartość rejestru `ebp` do `T0`.  
  
2. Dodaj `4` wartość `T0` do utworzenia adresu, pobrać wartości z tego adresu i przechowywana wartość rejestru `eip`.  
  
3. Pobiera wartość z adresem przechowywanym w `T0` i zapisać wartości rejestru `ebp`.  
  
4. Dodaj `8` wartość `T0` i zapisać wartości rejestru `esp`.  
  
   Pamiętaj, że ciąg program zależy od procesora CPU i konwencji wywoływania, skonfiguruj dla funkcji, reprezentowane przez bieżącą ramkę stosu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
