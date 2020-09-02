---
title: 'IDiaSectionContrib:: get_compiland | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_compiland method
ms.assetid: c0496f6f-f8f2-435f-8674-6c32db6c5934
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7ed5b181a9e0346cab5225d5f9024f070124186a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62576590"
---
# <a name="idiasectioncontribget_compiland"></a>IDiaSectionContrib::get_compiland
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera odwołanie do symbolu jednostka kompilacji, który należy do tej sekcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_compiland (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 określoną Zwraca obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) reprezentujący jednostka kompilacji, który współtworzył tę sekcję.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
