---
title: EncUnavailableReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 384d71d6f88e8cd792585bb097594fa7b1e38c64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953750"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` Przedstawia powody, które **Edytuj i Kontynuuj** są niedostępne.

## <a name="syntax"></a>Składnia

```cpp
enum tagEncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
typedef enum tagEncUnavailableReason EncUnavailableReason;
```

```csharp
public enum EncUnavailableReason {
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
Brak określonych powodów, dla których Edycja i kontynuacja nie są dostępne.

`ENCUN_INTEROP`\
W trakcie wywołania międzyoperacyjnego nie jest dostępne edytowanie i kontynuowanie.

`ENCUN_SQLCLR`\
Funkcja Edytuj i Kontynuuj nie jest dostępna podczas wywołania procedury SQL, które używa środowiska uruchomieniowego języka wspólnego (CLR).

`ENCUN_MINIDUMP`\
Edytuj i Kontynuuj nie jest dostępny podczas przetwarzania mini-dump.

`ENCUN_EMBEDDED`\
Edytuj i Kontynuuj nie jest dostępny podczas przetwarzania kodu osadzonego.

`ENCUN_ATTACH`\
Polecenie Edytuj i Kontynuuj nie jest dostępne, ponieważ sesja została dołączona do programu, debuger.

`ENCUN_WIN64`\
Edytuj i Kontynuuj nie jest dostępny podczas przetwarzania 64-bitowego kodu systemu Windows.

## <a name="remarks"></a>Uwagi
To wyliczenie jest przeznaczone do użytku wewnętrznego tylko przez program [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] . Metody [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) i [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) , zgodnie z implementacją przez niestandardowego dostawcę portu, powinny zawsze być zwracane `E_NOTIMPL` .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. idl

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
