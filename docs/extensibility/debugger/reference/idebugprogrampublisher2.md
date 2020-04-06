---
title: Program IDebugPublisher2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b17f5bab02e49951eb1647af95641af807c44863
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721528"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Ten interfejs umożliwia aparat debugowania (DE) lub dostawców portów niestandardowych do rejestrowania programów do debugowania.

## <a name="syntax"></a>Składnia

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
Visual Studio implementuje ten interfejs do rejestrowania programów są debugowane w celu ich widoczne do debugowania w wielu procesach.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Wywołaj `CoCreateInstance` funkcję COM, `CLSID_ProgramPublisher` aby uzyskać ten interfejs (zobacz przykład). DE lub dostawca portu niestandardowego używa tego interfejsu do rejestrowania węzłów programu, które reprezentują programy są debugowane.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
Ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Udostępnia węzeł programu dla DEs i menedżera debugowania sesji (SDM).|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Usuwa węzeł programu, tak aby nie był już dostępny.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Udostępnia program des i SDM.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Usuwa program, dzięki czemu nie jest już dostępny.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Ustawia flagę wskazującą, że debuger jest obecny.|

## <a name="remarks"></a>Uwagi
Ten interfejs udostępnia programy i węzły programów (czyli "publikuje" je) do użytku przez DEs i menedżera debugowania sesji (SDM). Aby uzyskać dostęp do opublikowanych programów i węzłów programu, użyj interfejsu [IDebugProgramProvider2.](../../../extensibility/debugger/reference/idebugprogramprovider2.md) Jest to jedyny sposób Visual Studio można rozpoznać, że program jest debugowany.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Przykład
W tym przykładzie pokazano, jak utworzyć wystąpienie wydawcy programu i zarejestrować węzeł programu. Jest to zaczerpnięte z samouczka, [Publikowanie węzła programu](https://msdn.microsoft.com/library/d0100e02-4e2b-4e72-9e90-f7bc11777bae).

```cpp
// This is how m_srpProgramPublisher is defined in the class definition:
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.

void CProgram::Start(IDebugEngine2 * pEngine)
{
    m_spEngine = pEngine;

    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);
        return;
    }

    // Register ourselves with the program publisher. Note that
    // CProgram implements the IDebgProgramNode2 interface, hence
    // the static cast on "this".
    hr = m_srpProgramPublisher->PublishProgramNode(
        static_cast<IDebugProgramNode2*>(this));
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);
        m_srpProgramPublisher.Release();
        return;
    }

    ATLTRACE("Added program node.\n");
}
```

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
