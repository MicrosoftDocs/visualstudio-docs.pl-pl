---
title: Struktura DebugStackFrameDescriptor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugStackFrameDescriptor
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugStackFrameDescriptor structure
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fddae48178ec6c56ce647f5c4f3a1bff3d81a980
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955197"
---
# <a name="debugstackframedescriptor-structure"></a>Struktura DebugStackFrameDescriptor
Wylicza ramki stosu i scala dane wyjściowe z kilku modułów wyliczających w tym samym wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `pdsf`  
 Obiekt w ramce stosu.  
  
 `dwMin`  
 Reprezentacja zależnych od maszyny niższy zakres adresów fizycznych skojarzonych z tą ramką stosu.  
  
 `dwLim`  
 Reprezentacja zależnych od maszyny Górny zakres adresów fizycznych skojarzonych z tą ramką stosu.  
  
 `fFinal`  
 Flaga wskazująca, że ramki jest przetwarzany.  
  
 `punkFinal`  
 Jeśli ten parametr nie jest `NULL`, powinna zostać przerwana w bieżącym modułu wyliczającego, scalanie i nowe hasło, które mają być uruchamiane. Obiekt wskazuje, jak uruchomić nowe wyliczenie.  
  
## <a name="remarks"></a>Uwagi  
 Menedżer debugowania procesów używa tej struktury, aby posortować ramek stosu z wielu aparatów skryptów. Zgodnie z Konwencją stosów rosnąć w dół. W związku z tym w architekturach, w którym stosy rozwój, adresy powinna być uzupełniony parami.  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)