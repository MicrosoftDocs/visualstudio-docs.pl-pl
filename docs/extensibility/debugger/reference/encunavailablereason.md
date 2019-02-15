---
title: EncUnavailableReason | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 7ccc05c58eafe6f8902b3f8ac09b90dc771a3009
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315693"
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
To wyliczenie jest do użytku wewnętrznego tylko przez [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]. [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) i [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) zaimplementowanego przez dostawcę numery portów należy zawsze zwracają `E_NOTIMPL`.

## <a name="requirements"></a>Wymagania
Header: msdbg.idl

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
[Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)

