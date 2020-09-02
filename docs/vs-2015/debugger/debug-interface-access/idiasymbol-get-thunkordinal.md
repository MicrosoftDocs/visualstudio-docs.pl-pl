---
title: 'IDiaSymbol:: get_thunkOrdinal | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 540eb49b215d06127a47df1defc436a0a307aa6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64784288"
---
# <a name="idiasymbolget_thunkordinal"></a>IDiaSymbol::get_thunkOrdinal
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera typ thunk funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 określoną Zwraca wartość z wyliczenia [THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md) , która określa typ THUNK funkcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Ta właściwość jest prawidłowa tylko wtedy, gdy symbol jako wartość [wyliczenia SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) `SymTagThunk` .  
  
 "Thunk" to fragment kodu, który konwertuje między 32-bitową przestrzenią adresową (znaną również jako płaska przestrzeń adresów) i 16-bitową przestrzenią adresową (znaną jako segmentowy obszar adresów).  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [THUNK_ORDINAL, Wyliczenie](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
