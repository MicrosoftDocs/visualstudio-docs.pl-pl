---
title: Idiasymbol::get_scoped — | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_scoped method
ms.assetid: 588163f7-958e-4072-bf66-db5c5f07d3cb
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2b958580eefb56eeb4b5341d7c484bb1f04e25ca
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "64787486"
---
# <a name="idiasymbolgetscoped"></a>IDiaSymbol::get_scoped
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera flagę określającą, czy typ danych zdefiniowany przez użytkownika pojawia się w zakresie leksykalnym nieglobalnej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_scoped (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca `TRUE` Jeśli typ danych zdefiniowany przez użytkownika, który pojawia się w nieglobalnych zakresie leksykalnym; w przeciwnym razie zwraca `FALSE`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.  
  
> [!NOTE]
> Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
