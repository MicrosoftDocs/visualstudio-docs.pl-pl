---
title: 'IDiaStackWalkFrame:: ReadMemory — | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97a868973d2a514150b8d728e685523e918f88f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150163"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Odczytuje pamięć z obrazu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 podczas Jedna z wartości wyliczenia [memorytypeenum —](../../debugger/debug-interface-access/memorytypeenum.md) , która określa rodzaj pamięci do uzyskania dostępu.  
  
 `va`  
 podczas Lokalizacja adresu wirtualnego w obrazie do rozpoczęcia odczytywania.  
  
 `cbData`  
 podczas Rozmiar buforu danych w bajtach.  
  
 `pcbData`  
 określoną Zwraca liczbę zwracanych bajtów. Jeśli `data` jest `NULL` , `pcbData` zawiera łączną liczbę dostępnych bajtów danych.  
  
 `data`  
 określoną Bufor, który ma zostać wypełniony danymi z określonej lokalizacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
