---
title: PENDING_BP_STATE_FLAGS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PENDING_BP_STATE_FLAGS
helpviewer_keywords:
- PENDING_BP_STATE_FLAGS enumeration
ms.assetid: 85522449-3fd8-4da5-b0fe-a43160e0c33b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e2e2fe8e529b3f4ed8457ce4552ff4d61dd00036
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783158"
---
# <a name="pendingbpstateflags"></a>PENDING_BP_STATE_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa flagi stan oczekujący punkt przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_PENDING_BP_STATE_FLAGS {   
   PBPSF_NONE        = 0x0000,  
   PBPSF_VIRTUALIZED = 0x0001  
};  
typedef DWORD PENDING_BP_STATE_FLAGS;  
```  
  
```csharp  
public enum enum_PENDING_BP_STATE_FLAGS {   
   PBPSF_NONE        = 0x0000,  
   PBPSF_VIRTUALIZED = 0x0001  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 PBPSF_NONE  
 Symbol zastępczy.  
  
 PBPSF_VIRTUALIZED  
 Określa zwirtualizowanych oczekujących punktów przerwania, który ma zostać powiązany za każdym razem, gdy nowy kod jest ładowany.  
  
## <a name="remarks"></a>Uwagi  
 Używany do `flags` członkiem [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) struktury.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)

