---
title: 'IDiaEnumSectionContribs:: Item | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Item method
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 06a82fbb52ccdf0f9fb9fda50a74f2cfb30e7648
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190007"
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera udziały sekcji za pomocą indeksu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Item (   
   DWORD                index,  
   IDiaSectionContrib** section  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 index  
 podczas Indeks obiektu [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) do pobrania. Indeks znajduje się w zakresie od 0 do `count` -1, gdzie `count` jest zwracany przez metodę [IDiaEnumSectionContribs:: get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md) .  
  
 section  
 określoną Zwraca obiekt [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) reprezentujący żądany udział sekcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaEnumSectionContribs:: get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
