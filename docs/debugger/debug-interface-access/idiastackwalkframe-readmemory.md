---
title: Idiastackwalkframe::readmemory — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97b1f58f31484084bff502d9ad6a019089ecfec8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992528"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Odczytuje pamięć z obrazu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT readMemory (   
   MemoryTypeEnum type,  
   ULONGLONG va,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 [in] Jedną z [memorytypeenum — wyliczenie](../../debugger/debug-interface-access/memorytypeenum.md) wartości wyliczenia, które określa rodzaj pamięci, aby uzyskać dostęp.  
  
 `va`  
 [in] Wirtualny adres lokalizacji obrazu ma rozpocząć się odczyt.  
  
 `cbData`  
 [in] Rozmiar buforu danych, w bajtach.  
  
 `pcbData`  
 [out] Zwraca liczbę bajtów zwróconych. Jeśli `data` jest `NULL`, następnie `pcbData` zawiera całkowitą liczbę bajtów dostępnych danych.  
  
 `data`  
 [out] Buforu, który jest wypełniona danymi z określonej lokalizacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)