---
title: 'IDiaSymbol:: get_targetVirtualAddress | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetVirtualAddress method
ms.assetid: a0a5ce72-95f8-443e-bb4b-8c21194faad0
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 911295730548e905e55a61fa16fc3adc792a1bbb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64793149"
---
# <a name="idiasymbolget_targetvirtualaddress"></a>IDiaSymbol::get_targetVirtualAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera adres wirtualny (VA) elementu docelowego thunk.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_targetVirtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 określoną Zwraca liczbę VA elementu docelowego thunk.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Ta właściwość jest prawidłowa tylko wtedy, gdy symbol jako wartość [wyliczenia SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) `SymTagThunk` .  
  
 "Thunk" to fragment kodu, który konwertuje między 32-bitową przestrzenią adresową (znaną również jako płaska przestrzeń adresów) i 16-bitową przestrzenią adresową (znaną jako segmentowy obszar adresów).  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
