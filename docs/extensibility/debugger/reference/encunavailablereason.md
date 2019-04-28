---
title: EncUnavailableReason | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea1bbf8fe96abbf1e7bd9a92396d0dcfa4306445
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62924596"
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

#### <a name="parameters"></a>Parametry
Brak ENCUN_NONE powód Dlaczego Edytuj i Kontynuuj nie jest dostępny.

ENCUN_INTEROP Edytuj i Kontynuuj nie jest dostępna podczas wywołania międzyoperacyjnego.

ENCUN_SQLCLR Edytuj i Kontynuuj nie jest dostępna podczas wywołania procedury SQL, która używa środowiska uruchomieniowego języka wspólnego (CLR).

ENCUN_MINIDUMP Edytuj i Kontynuuj nie jest dostępna podczas przetwarzania minizrzutu.

ENCUN_EMBEDDED Edytuj i Kontynuuj nie jest dostępna, podczas przetwarzania osadzony kod.

ENCUN_ATTACH Edytuj i Kontynuuj nie jest dostępna, ponieważ sesja została podłączona do, nie uruchomione przez debugera.

ENCUN_WIN64 Edytuj i Kontynuuj nie jest dostępna podczas przetwarzania kodu Windows 64-bitowego.

## <a name="remarks"></a>Uwagi
To wyliczenie jest do użytku wewnętrznego tylko przez [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]. [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) i [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) zaimplementowanego przez dostawcę numery portów należy zawsze zwracają `E_NOTIMPL`.

## <a name="requirements"></a>Wymagania
Header: msdbg.idl

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
