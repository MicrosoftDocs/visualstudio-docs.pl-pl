---
title: IDebugProgramPublisher2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4a7547639fb2f7f3068dd7f738b0c0d10ea926f0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916687"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Ten interfejs umożliwia aparat debugowania (DE) lub dostawców port niestandardowy, można zarejestrować programy do debugowania.

## <a name="syntax"></a>Składnia

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
Program Visual Studio implementuje ten interfejs, aby zarejestrować debugowane aby stały się widoczne dla debugowania wielu procesom programy.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Wywołania modelu COM `CoCreateInstance` funkcją `CLSID_ProgramPublisher` uzyskać tego interfejsu (Zobacz przykład). DE lub dostawcy niestandardowego portu ten interfejs jest używana do zarejestrowania węzły programu, które reprezentują debugowane programy.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
Ten interfejs implementuje następujących metod:

|Metoda|Opis|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Udostępnia węzła programu DEs i sesja debugowania manager (SDM).|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Usuwa węzła program nie jest już dostępna.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Udostępnia program DEs i SDM.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Usuwa program, więc nie jest już dostępna.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Ustawia flagę wskazującą, czy jest obecny debuger.|

## <a name="remarks"></a>Uwagi
Ten interfejs udostępnia programy oraz węzły programu (czyli "" spowoduje ich opublikowanie) do użycia przez DEs i Menedżer debugowania sesji (SDM). Dostęp do opublikowanych programów i węzły programu, należy użyć [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interfejsu. To jest jedynym sposobem, w których program Visual Studio jest w stanie rozpoznać jest debugowany program.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Przykład
Ten przykład przedstawia sposób tworzenia wystąpienia wydawca programu i zarejestruj węzeł program. To jest pobierana z tego samouczka [publikowanie węzła programu](https://msdn.microsoft.com/library/d0100e02-4e2b-4e72-9e90-f7bc11777bae).

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
