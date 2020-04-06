---
title: EncNiedostępneReason | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28863549ab3eac96322530bc85c52697f20448c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737167"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!`Reprezentuje przyczyny, dla których **edycja i kontynuowanie** są niedostępne.

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
Nie ma konkretnego powodu, dla którego edycja i kontynuowanie nie są dostępne.

`ENCUN_INTEROP`\
Funkcja Edycja i Kontynuuj nie jest dostępna podczas połączenia InterOp.

`ENCUN_SQLCLR`\
Edycja i kontynuuj nie jest dostępna podczas wywołania procedury SQL, która używa środowiska wykonawczego języka wspólnego (CLR).

`ENCUN_MINIDUMP`\
Funkcja Edycja i Kontynuuj nie jest dostępna podczas przetwarzania mini-zrzutu.

`ENCUN_EMBEDDED`\
Edycja i kontynuuj nie jest dostępna podczas przetwarzania kodu osadzonego.

`ENCUN_ATTACH`\
Funkcja Edycja i Kontynuuj nie jest dostępna, ponieważ sesja została dołączona do debugera, nie została uruchomiona przez debuger.

`ENCUN_WIN64`\
Program Edit and Continue nie jest dostępny podczas przetwarzania 64-bitowego kodu systemu Windows.

## <a name="remarks"></a>Uwagi
To wyliczenie jest przeznaczone [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]do użytku wewnętrznego tylko przez . [Metody GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) i [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) zaimplementowane przez `E_NOTIMPL`niestandardowego dostawcę portu powinny zawsze zwracać .

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.idl

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
