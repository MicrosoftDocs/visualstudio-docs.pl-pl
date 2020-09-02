---
title: 'IDiaEnumFrameData:: frameByRVA | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByRVA method
ms.assetid: 4b8dec05-e76c-4cc4-9644-2369d583849f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 825f72eec5b56fef70019b64d6e599b7c4712ee2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146520"
---
# <a name="idiaenumframedataframebyrva"></a>IDiaEnumFrameData::frameByRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zwraca ramkę według względnego adresu wirtualnego (RVA).  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT frameByRVA(   
   DWORD           relativeVirtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 relativeVirtualAddress  
 podczas Adres RVA ramki zainteresowania.  
  
 ramowe  
 określoną Zwraca obiekt [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) reprezentujący ramkę, która zawiera podany adres.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli żadne dane ramki nie pasują do podanego adresu. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
