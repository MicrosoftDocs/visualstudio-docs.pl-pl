---
title: CANSTOP_REASON | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 277164ea3dfcdabbe24622bb5148ebd75d54f8c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62561855"
---
# <a name="canstop_reason"></a>CANSTOP_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Służy do określenia, czy program może zatrzymać wykonywanie po osiągnięciu określonego punktu w wykonaniu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
typedef DWORD CANSTOP_REASON;  
```  
  
```csharp  
public enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 CANSTOP_ENTRYPOINT  
 Określa punkt wejścia danego programu.  
  
 CANSTOP_STEPIN  
 Określa przechodzenie do funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Przeszedł jako argument do metody [Getpowód](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) , aby potwierdzić z menedżerem debugowania sesji (SDM), jeśli nie można go zatrzymać po osiągnięciu punktu wejścia programu lub po przejściu do funkcji lub metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
