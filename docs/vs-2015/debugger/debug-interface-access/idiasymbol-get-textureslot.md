---
title: 'IDiaSymbol:: get_textureSlot | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 166a1a3a-2e10-4baa-ace1-9104b56185ce
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4890790db10ca1956a3e1f0163cb8bbc8c9df214
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154209"
---
# <a name="idiasymbolget_textureslot"></a>IDiaSymbol::get_textureSlot
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera gniazdo tekstury.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT get_textureSlot(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 określoną Wskaźnik do `DWORD` , który zawiera gniazdo tekstury.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
