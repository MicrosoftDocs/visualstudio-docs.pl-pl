---
description: Opisuje wyjątek lub błąd czasu wykonywania zgłoszony przez debugowany program.
title: EXCEPTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa78aeea8a3c20aa5b7f5d17cf444bd4184903d5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150903"
---
# <a name="exception_info"></a>EXCEPTION_INFO
Opisuje wyjątek lub błąd czasu wykonywania zgłoszony przez debugowany program.

## <a name="syntax"></a>Składnia

```cpp
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
`pProgram`\
Obiekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , który reprezentuje program, w którym wystąpił wyjątek.

`bstrProgramName`\
Nazwa programu, w którym wystąpił wyjątek.

`bstrExceptionName`\
Nazwa wyjątku.

`dwCode`\
Kod identyfikacyjny dotyczący wyjątku lub błędu czasu wykonywania.

`dwState`\
Wartość z wyliczenia [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) , która definiuje stan wyjątku.

`guidType`\
Identyfikator języka GUID (lub) `guidLang` `guidEng` .

## <a name="remarks"></a>Uwagi
Ta struktura jest przenoszona jako parametr do metody [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) i [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) . Ta struktura jest również przenoszona do metody [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) , która ma zostać wypełniona.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
- [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)
