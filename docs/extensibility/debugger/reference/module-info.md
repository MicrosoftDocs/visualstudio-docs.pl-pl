---
title: MODULE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58531e64c88c89a92b5eee7f2eac7067cf42775f
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458005"
---
# <a name="moduleinfo"></a>MODULE_INFO
W tym artykule opisano konkretnego modułu (DLL, EXE lub zestawu).

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
 Kombinacja flag z [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) wyliczenia, która określa pola, które są wypełnione.

 `m_bstrName`\
 Nazwa modułu.

 `m_bstrUrl`\
 Adres URL modułu.

 `m_bstrVersion`\
 Wersja modułu.

 `m_bstrDebugMessage`\
 Opcjonalną wiadomość, informacje o module, na przykład "nie można załadować symboli."

 `m_addrLoadAddress`\
 Adresem ładowania modułu.

 `m_addrPreferredLoadAddress`\
 Adres preferowanego ładowania modułu.

 `m_dwSize`\
 Rozmiar modułu.

 `m_dwLoadOrder`\
 Kolejność ładowania modułu.

 `m_TimeStamp`\
 Czas ostatniej modyfikacji pliku symboli.

 `m_bstrUrlSymbolLocation`\
 Lokalizacja pliku symboli (na przykład ".\\") określona w module. Używane jako lokalizację początkową można znaleźć symboli dla modułu.

 `m_dwModuleFlags`\
 Kombinacja flag z [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) wyliczenie opisujące modułu.

## <a name="remarks"></a>Uwagi
 Ta struktura jest przekazywany do [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) metody, gdzie jest wypełnione.

 Ta struktura odnosi się do każdego modułu, na liście **modułów** okna.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
