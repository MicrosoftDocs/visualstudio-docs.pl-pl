---
title: Struktura DebugStackFrameDescriptor | Microsoft Docs
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
ms.openlocfilehash: 910e08ec6d9982354eb71b50d5e916917808f140
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576551"
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
 Obiekt ramki stosu.  
  
 `dwMin`  
 Reprezentacja z dolnym zakresem adresów fizycznych skojarzonych z tą ramką stosu.  
  
 `dwLim`  
 Reprezentacja z górnym zakresem adresów fizycznych skojarzonych z tą ramką stosu.  
  
 `fFinal`  
 Flaga wskazująca, że ramka jest przetwarzana.  
  
 `punkFinal`  
 Jeśli ten parametr nie jest `NULL`, bieżące scalenie modułu wyliczającego powinno zostać zatrzymane i należy uruchomić nowy. Obiekt wskazuje, jak rozpocząć nowe Wyliczenie.  
  
## <a name="remarks"></a>Uwagi  
 Menedżer debugowania procesów używa tej struktury do sortowania ramek stosu z wielu aparatów skryptów. Według Konwencji, stosy rosną. W związku z tym w przypadku architektury, w których stosy rosną, adresy powinny być parach-uzupełnione.  
  
## <a name="see-also"></a>Zobacz także  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)