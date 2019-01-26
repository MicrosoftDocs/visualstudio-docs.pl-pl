---
title: Idiasession::put_loadaddress — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 488ae20ae4e38905b722f833a52676eea6ce0e81
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035773"
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
Ustawia adres obciążenia dla pliku wykonywalnego, który odpowiada symboli w tym magazynie symboli.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `NewVal`  
 [in] Ładowanie adresów dla pliku wykonywalnego.  
  
## <a name="remarks"></a>Uwagi  
 Symbol adresów wirtualnych (oceny luk w zabezpieczeniach) właściwości są obliczane przy użyciu wartości przez tę metodę. Wirtualne adresy nie są obliczane, jeśli ta właściwość ma wartość różna od zera.  
  
> [!NOTE]
>  Musisz wywołać tę metodę, gdy otrzymasz [idiasession —](../../debugger/debug-interface-access/idiasession.md) obiektu i przed rozpoczęciem korzystania z obiektu, jeśli musisz użyć dowolnej właściwości wirtualnego symboli.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)