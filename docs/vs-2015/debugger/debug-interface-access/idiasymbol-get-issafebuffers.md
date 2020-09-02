---
title: 'IDiaSymbol:: get_isSafeBuffers | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isSafeBuffers method
ms.assetid: f29e373d-e7bb-4181-ab9f-bf708d401d83
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 046744fda09f272ca80c2760e880dce23d45ae36
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65673760"
---
# <a name="idiasymbolget_issafebuffers"></a>IDiaSymbol::get_isSafeBuffers
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera flagę, która określa, czy jest używana dyrektywa preprocesora dla bezpiecznego bufora. Użyj, gdy [Wyliczenie SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) jest ustawione na `SymTagFunction` .  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_isSafeBuffers(   
   BOOL* pRetVal)  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 określoną Zwraca `TRUE` czy wskaźnik używa dyrektywy preprocesora dla bezpiecznego bufora; w przeciwnym razie zwraca `FALSE` .  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dia2. h  
  
 Biblioteka: diaguids. lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [strict_gs_check](https://msdn.microsoft.com/library/decfec81-c916-42e0-a07f-8cc26df6a7ce)
