---
title: EncUnavailableReason | Dokumentacja firmy Microsoft
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
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5ec7c652fd2a35aa927cb5c634fea3cdf9b19ee3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784016"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

`This is for internal use only!` Reprezentuje przyczyny, **Edytuj i Kontynuuj** nie jest dostępna.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```csharp  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 ENCUN_NONE  
 Nie określonych powód, dlaczego Edytuj i Kontynuuj nie jest dostępny.  
  
 ENCUN_INTEROP  
 Edytuj i Kontynuuj nie jest dostępna podczas wywołania międzyoperacyjnego.  
  
 ENCUN_SQLCLR  
 Edytuj i Kontynuuj nie jest dostępna podczas wywołania procedury SQL, która używa środowiska uruchomieniowego języka wspólnego (CLR).  
  
 ENCUN_MINIDUMP  
 Edytuj i Kontynuuj nie jest dostępna podczas przetwarzania minizrzutu.  
  
 ENCUN_EMBEDDED  
 Edytuj i Kontynuuj nie jest dostępna, podczas przetwarzania osadzony kod.  
  
 ENCUN_ATTACH  
 Edytuj i Kontynuuj nie jest dostępna, ponieważ sesja została podłączona do, nie jest uruchamiane przez debuger.  
  
 ENCUN_WIN64  
 Edytuj i Kontynuuj nie jest dostępna podczas przetwarzania kodu Windows 64-bitowego.  
  
## <a name="remarks"></a>Uwagi  
 To wyliczenie jest do użytku wewnętrznego tylko przez [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) i [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) zaimplementowanego przez dostawcę numery portów należy zawsze zwracają `E_NOTIMPL`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.idl  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)

