---
title: EXCEPTION_INFO | Dokumentacja firmy Microsoft
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
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8a6feebb3be6f6f6f50a7d1a2ed3ff8525dacf6c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786889"
---
# <a name="exceptioninfo"></a>EXCEPTION_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

W tym artykule opisano, wystąpi wyjątek lub błąd czasu wykonywania zgłoszony przez debugowanego programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```csharp  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 pProgram  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekt, który reprezentuje program, w którym wyjątek wystąpił.  
  
 bstrProgramName  
 Nazwa programu, w którym wyjątek wystąpił.  
  
 bstrExceptionName  
 Nazwa wyjątku.  
  
 dwCode  
 Kod identyfikacyjny dla błędu lub wyjątku czasu wykonywania.  
  
 dwState  
 Wartość z zakresu od [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) wyliczenie, które definiuje stan wyjątku.  
  
 guidType  
 Identyfikator GUID języka, każdy `guidLang` lub `guidEng`.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest przekazywany jako parametr do [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) i [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) metody. Ta struktura jest również przekazywany do [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) metodę, aby wypełnić.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktur i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)

