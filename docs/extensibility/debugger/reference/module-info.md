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
ms.openlocfilehash: 0e3a11e368b6260d00f3f6ed0b19d94aa26bd31a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683613"
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
 dwValidFields A kombinacja flag z [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) wyliczenia, która określa pola, które są wypełnione.

 m_bstrName nazwy modułu.

 m_bstrUrl URL modułu.

 m_bstrVersion wersji modułu.

 m_bstrDebugMessage opcjonalną wiadomość, informacje o module, na przykład "nie można załadować symboli."

 m_addrLoadAddress adresem ładowania modułu.

 m_addrPreferredLoadAddress adres preferowanego ładowania modułu.

 m_dwSize rozmiar modułu.

 m_dwLoadOrder kolejność ładowania modułu.

 m_TimeStamp czas ostatniej modyfikacji pliku symboli.

 m_bstrUrlSymbolLocation lokalizację pliku symboli (na przykład ".\\") określona w module. Używane jako lokalizację początkową można znaleźć symboli dla modułu.

 m_dwModuleFlags A kombinacja flag z [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) wyliczenie opisujące modułu.

## <a name="remarks"></a>Uwagi
 Ta struktura jest przekazywany do [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) metody, gdzie jest wypełnione.

 Ta struktura odnosi się do każdego modułu, na liście **modułów** okna.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)