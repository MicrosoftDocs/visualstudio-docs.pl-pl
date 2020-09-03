---
title: CONST_GUID_ARRAY | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CONST_GUID_ARRAY
helpviewer_keywords:
- CONST_GUID_ARRAY structure
ms.assetid: bd55e7d8-372c-4c3e-9eed-28f6b415a5db
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 43715ca8fa8174b2b8b9509a93e98cf15ad4611c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198862"
---
# <a name="const_guid_array"></a>CONST_GUID_ARRAY
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Struktura, która przechowuje listę `GUID` s.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
typedef struct tagCONST_GUID_ARRAY {  
   DWORD       dwCount;  
   CONST GUID* Members;  
} CONST_GUID_ARRAY;  
```  
  
```csharp  
public struct CONST_GUID_ARRAY {  
   public uint   dwCount;  
   public Guid[] Members;  
}  
```  
  
## <a name="members"></a>Elementy członkowskie  
 dwCount  
 Liczba elementów `GUID` w `Members` tablicy.  
  
 Elementy członkowskie  
 Tablica wartości `GUID` s.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest przekazana do metody [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) i jest zwracana z metod [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) i [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md) .  
  
 Właściciel wystąpienia tej struktury jest odpowiedzialny za zwalnianie wszelkich przyznanych pamięci.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)   
 [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
