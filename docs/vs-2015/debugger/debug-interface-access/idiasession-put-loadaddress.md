---
title: Idiasession::put_loadaddress — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: daf1e7748a95ae0ad2d7fce3592e0a6948077f45
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761999"
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



