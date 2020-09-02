---
title: 'IDiaFrameData:: Execute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4042cf58ee34b5f49df601b94e1110f03e0b6f5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197552"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wykonuje odwinięcia stosu i zwraca wyniki w interfejsie przeszukiwania stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `frame`  
 podczas Obiekt [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) , który przechowuje stan rejestrów ramek.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono możliwe wartości zwracane dla tej metody.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|E_DIA_INPROLOG|Nie można wykonać ramki stosu w kodzie prologu.|  
|E_DIA_SYNTAX|Napotkano błąd analizy w programie ramowym.|  
|E_DIA_FRAME_ACCESS|Nie można uzyskać dostępu do rejestrów lub pamięci.|  
|E_DIA_VALUE|Wystąpił błąd podczas obliczania wartości (na przykład dzielenia przez zero).|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana podczas debugowania w celu odwinięcia stosu. Obiekt [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) jest implementowany przez aplikację kliencką w celu otrzymywania aktualizacji rejestrów i dostarczania metod używanych przez `execute` metodę.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
