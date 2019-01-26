---
title: PROGRAM_NODE_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- PROGRAM_NODE_ARRAY
helpviewer_keywords:
- PROGRAM_NODE_ARRAY structure
ms.assetid: 8eeea600-eda5-4b7c-868a-0b86d177b0a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ebdb40634deea9c1a2362e6027ea6d6ae5117ff
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54934026"
---
# <a name="programnodearray"></a>PROGRAM_NODE_ARRAY
Zawiera tablicę obiektów, które opisują interesujące programy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct tagPROGRAM_NODE_ARRAY {  
   DWORD                dwCount;  
   IDebugProgramNode2** Members;  
} PROGRAM_NODE_ARRAY;  
```  
  
```csharp  
public struct tagPROGRAM_NODE_ARRAY {  
   public uint                 dwCount;  
   public IDebugProgramNode2[] Members;  
}  
```  
  
## <a name="members"></a>Elementy członkowskie  
 dwCount  
 Liczba obiektów w `Members` tablicy.  
  
 Elementy członkowskie  
 Tablica [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) obiekty opisujące programy wymagane.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest częścią [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) strukturę, która z kolei jest wypełniane przez wywołanie [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktur i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)