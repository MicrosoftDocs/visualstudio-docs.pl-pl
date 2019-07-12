---
title: Idiasymbol::get_thunkordinal — | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "64784288"
---
# <a name="idiasymbolgetthunkordinal"></a>IDiaSymbol::get_thunkOrdinal
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
 [out] Zwraca wartość z zakresu od [thunk_ordinal — wyliczenie](../../debugger/debug-interface-access/thunk-ordinal.md) wyliczenie, który określa typ thunk funkcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.  
  
> [!NOTE]
> Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Ta właściwość jest prawidłowa tylko wtedy, gdy symbol jako [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wartość `SymTagThunk`.  
  
 "thunk" jest fragmentem kodu, który wykonuje konwersję między pamięci 32-bitowej przestrzeni adresowej (znany także jako płaska przestrzeń adresowa) i 16-bitowej przestrzeni adresowej (znanych jako przestrzeń adresową segmenty).  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Thunk_ordinal — wyliczenie](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
