---
title: BP_ERROR_TYPE | Dokumentacja firmy Microsoft
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
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 61ec31973d1de69b9b276456465b31c429d77469
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725846"
---
# <a name="bperrortype"></a>BP_ERROR_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa typ błąd punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
typedef DWORD BP_ERROR_TYPE;  
```  
  
```csharp  
public enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 BPET_NONE  
 Określa nie błąd punktu przerwania.  
  
 BPET_TYPE_WARNING  
 Określa błąd stylu ostrzeżenie punktu przerwania.  
  
 BPET_TYPE_ERROR  
 Określa błąd punktu przerwania stylu błędu.  
  
 BPET_SEV_HIGH  
 Określa błąd punktu przerwania o wysokiej ważności.  
  
 BPET_SEV_GENERAL  
 Określa o średniej ważności, punkt przerwania.  
  
 BPET_SEV_LOW  
 Określa o niskiej ważności, punkt przerwania.  
  
 BPET_TYPE_MASK  
 Określa błąd punktu przerwania stylu maski.  
  
 BPET_SEV_MASK  
 Określa błąd punktu przerwania ważność maska stylu.  
  
 BPET_GENERAL_WARNING  
 Określa błąd punktu przerwania ogólne ostrzeżenie stylu.  
  
 BPET_GENERAL_ERROR  
 Określa błąd punktu przerwania stylu w przypadku błędu ogólnego.  
  
 BPET_ALL  
 Określa wszystkie typy błąd punktu przerwania.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości mogą być łączone przy użyciu bitowego operatora `OR` i jest używana do `dwType` członkiem [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struktury. Przekazany jako parametr do [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) metody.  
  
 Typ błędu punktu przerwania składa się z typu i ważności. Oznacza, że typ błąd punktu przerwania nigdy nie tylko typem (na przykład `BPET_TYPE_ERROR`,) lub ważność (na przykład `BPET_SEV_GENERAL`) przez siebie. `BPET_GENERAL_WARNING` i `BPET_GENERAL_ERROR` zapewnia wstępnie zdefiniowane wartości dla punktów przerwania ogólne, ostrzeżeń i błędów.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)

