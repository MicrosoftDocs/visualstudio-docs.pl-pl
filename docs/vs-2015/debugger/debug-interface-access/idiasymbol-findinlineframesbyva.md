---
title: 'IDiaSymbol:: findInlineFramesByVA | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 54295d3e-bbb6-4c10-ab9d-adcfc22b1f71
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 45ba0d02c58bf40fb45ea79616c58bbc9037671c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149883"
---
# <a name="idiasymbolfindinlineframesbyva"></a>IDiaSymbol::findInlineFramesByVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera wyliczenie, które pozwala klientowi na iterację we wszystkich wbudowanych ramkach w określonym adresie wirtualnym (VA).  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT findInlineFramesByVA (   
   ULONGLONG         va,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `va`  
 podczas Określa adres jako VA.  
  
 `ppResult`  
 określoną Zawiera `IDiaEnumSymbols` obiekt zawierający listę pobieranych ramek.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum —, Wyliczenie](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
