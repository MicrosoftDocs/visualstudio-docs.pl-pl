---
title: Idiasession::put_loadaddress — | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1be0bfd6d5a635dcff632e25421922697b3f0de6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54794315"
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ustawia adres obciążenia dla pliku wykonywalnego, który odpowiada symboli w tym magazynie symboli.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
