---
title: Struktura JS_NATIVE_FRAME | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_NATIVE_FRAME
apilocation:
- jscript9diag.dll
ms.assetid: 5afa2ee1-b3e2-47cb-b304-84f96e6fbb14
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0b624229a96cfc2a2d2044a926f45fa91a1c76c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571764"
---
# <a name="js_native_frame-structure"></a>Struktura JS_NATIVE_FRAME
Reprezentuje ramkę stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef struct {  
    UINT64 InstructionOffset;    UINT64 ReturnOffset;    UINT64 FrameOffset;    UINT64 StackOffset;  
} JS_NATIVE_FRAME;  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `InstructionOffset`  
 Wskaźnik instrukcji.  
  
 `ReturnOffset`  
 Adres zwrotny.  
  
 `FrameOffset`  
 Wskaźnik ramki.  
  
 `StackOffset`  
 Wskaźnik stosu.  
  
## <a name="remarks"></a>Uwagi  
 Struktura `JS_NATIVE_FRAME` jest używana przez `IJsStackFrameEnumerator`.  
  
## <a name="see-also"></a>Zobacz także  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)