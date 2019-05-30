---
title: EncUnavailableReason | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7db94a181d87791edb242d69b461f90c42a5e080
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318154"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` Reprezentuje przyczyny, **Edytuj i Kontynuuj** nie jest dostępna.

## <a name="syntax"></a>Składnia

```cpp
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

## <a name="fields"></a>Pola
`ENCUN_NONE`\
Nie określonych powód, dlaczego Edytuj i Kontynuuj nie jest dostępny.

`ENCUN_INTEROP`\
Edytuj i Kontynuuj nie jest dostępna podczas wywołania międzyoperacyjnego.

`ENCUN_SQLCLR`\
Edytuj i Kontynuuj nie jest dostępna podczas wywołania procedury SQL, która używa środowiska uruchomieniowego języka wspólnego (CLR).

`ENCUN_MINIDUMP`\
Edytuj i Kontynuuj nie jest dostępna podczas przetwarzania minizrzutu.

`ENCUN_EMBEDDED`\
Edytuj i Kontynuuj nie jest dostępna, podczas przetwarzania osadzony kod.

`ENCUN_ATTACH`\
Edytuj i Kontynuuj nie jest dostępna, ponieważ sesja została podłączona do, nie jest uruchamiane przez debuger.

`ENCUN_WIN64`\
Edytuj i Kontynuuj nie jest dostępna podczas przetwarzania kodu Windows 64-bitowego.

## <a name="remarks"></a>Uwagi
To wyliczenie jest do użytku wewnętrznego tylko przez [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]. [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) i [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) zaimplementowanego przez dostawcę numery portów należy zawsze zwracają `E_NOTIMPL`.

## <a name="requirements"></a>Wymagania
Header: msdbg.idl

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
