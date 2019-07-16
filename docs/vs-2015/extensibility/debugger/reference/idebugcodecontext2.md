---
title: IDebugCodeContext2 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e06fd709b2d076b6fa8de7f104e907eb1b35a42
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68190955"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs reprezentuje pozycję początkową instrukcji kodu. Dla większości architektury w czasie wykonywania, kontekst kodu można traktować jako adres w usłudze stream wykonywania programu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania implementuje ten interfejs, aby powiązać pozycja instrukcję kodu położenie dokumentu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 W wielu interfejsach zwracają ten interfejs najczęściej, [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Jest również używany często [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) interfejsu także, jak informacje rozwiązania punktu przerwania.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 Oprócz metod na [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interfejsu, ten interfejs implementuje następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Pobiera kontekst dokumentu, który odnosi się do kontekstu aktywnego kodu.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Pobiera informacje o języku dla tego kontekstu kodu.|  
  
## <a name="remarks"></a>Uwagi  
 Główną różnicą między `IDebugCodeContext2` interfejsu i [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interfejsu jest fakt, że `IDebugCodeContext2` zawsze jest wyrównany do instrukcji. Oznacza to, że `IDebugCodeContext2` zawsze wskazuje początek instrukcji, natomiast `IDebugMemoryContext2` mogą wskazywać na dowolny bajt pamięci w architekturze czasu wykonywania. `IDebugCodeContext2` jest zwiększany, zgodnie z instrukcjami opisanymi, a nie według rozmiaru magazynu podstawowego (zazwyczaj bajtów).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)   
 [Dalej](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
