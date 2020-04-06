---
title: MODULE_INFO | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59ab4d0bb2a7aaa4b08f616ea0a99be85b521bb0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714316"
---
# <a name="module_info"></a>MODULE_INFO
Opisuje określony moduł (biblioteka DLL, EXE lub zespół).

## <a name="syntax"></a>Składnia

```cpp
typedef struct tagMODULE_INFO { 
   MODULE_INFO_FIELDS dwValidFields;
   BSTR               m_bstrName;
   BSTR               m_bstrUrl;
   BSTR               m_bstrVersion;
   BSTR               m_bstrDebugMessage;
   UINT64             m_addrLoadAddress;
   UINT64             m_addrPreferredLoadAddress;
   DWORD              m_dwSize;
   DWORD              m_dwLoadOrder;
   FILETIME           m_TimeStamp;
   BSTR               m_bstrUrlSymbolLocation;
   MODULE_FLAGS       m_dwModuleFlags;
} MODULE_INFO;
```

```csharp
public struct MODULE_INFO { 
   public uint     dwValidFields;
   public string   m_bstrName;
   public string   m_bstrUrl;
   public string   m_bstrVersion;
   public string   m_bstrDebugMessage;
   public ulong    m_addrLoadAddress;
   public ulong    m_addrPreferredLoadAddress;
   public uint     m_dwSize;
   public uint     m_dwLoadOrder;
   public FILETIME m_TimeStamp;
   public string   m_bstrUrlSymbolLocation;
   public uint     m_dwModuleFlags;
};
```

## <a name="members"></a>Elementy członkowskie
 `dwValidFields`\
 Kombinacja flag z wyliczenia [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) określająca, które pola są wypełniane.

 `m_bstrName`\
 Nazwa modułu.

 `m_bstrUrl`\
 Adres URL modułu.

 `m_bstrVersion`\
 Wersja modułu.

 `m_bstrDebugMessage`\
 Opcjonalny komunikat o module, na przykład "Nie można załadować symboli".

 `m_addrLoadAddress`\
 Adres obciążenia modułu.

 `m_addrPreferredLoadAddress`\
 Preferowany adres obciążenia modułu.

 `m_dwSize`\
 Rozmiar modułu.

 `m_dwLoadOrder`\
 Kolejność ładowania modułu.

 `m_TimeStamp`\
 Czas ostatniej modyfikacji pliku symbolu.

 `m_bstrUrlSymbolLocation`\
 Lokalizacja pliku symbolu (na przykład\\". ") określona w module. Służy jako miejsce początkowe do znajdowania symboli modułu.

 `m_dwModuleFlags`\
 Kombinacja flag z wyliczenia [MODULE_FLAGS,](../../../extensibility/debugger/reference/module-flags.md) który opisuje moduł.

## <a name="remarks"></a>Uwagi
 Ta struktura jest przekazywana do [Metody GetInfo,](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) gdzie jest wypełniona.

 Ta struktura odpowiada każdemu modułowi wymienionemu w oknie **Moduły.**

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
