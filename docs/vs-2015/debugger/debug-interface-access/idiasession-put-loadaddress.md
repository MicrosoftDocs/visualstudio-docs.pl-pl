---
title: IDiaSession::p ut_loadAddress | Microsoft Docs
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
ms.openlocfilehash: f697384874726904960fc5ba04733c3acfe1cd06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64778223"
---
# <a name="idiasessionput_loadaddress"></a>IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ustawia adres ładowania pliku wykonywalnego, który odnosi się do symboli w tym magazynie symboli.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `NewVal`  
 podczas Adres ładowania pliku wykonywalnego.  
  
## <a name="remarks"></a>Uwagi  
 Właściwości adresu wirtualnego symbolu (VA) są obliczane przy użyciu wartości tej metody. Adresy wirtualne nie są obliczane, chyba że ta właściwość ma wartość różną od zera.  
  
> [!NOTE]
> Należy wywołać tę metodę, gdy zostanie pobrany obiekt [IDiaSession](../../debugger/debug-interface-access/idiasession.md) i przed rozpoczęciem korzystania z obiektu, jeśli konieczne jest użycie dowolnych właściwości wirtualnych w symbolach.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
