---
title: PDB_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad4b6a06a2a145daa85d780f4d23dfac9bebf7a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205112"
---
# <a name="pdb_type"></a>PDB_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta struktura określa informacje o typie pola pobieranym z symbolu PDB.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
typedef struct _tagTYPE_PDB {  
   ULONG32 ulAppDomainID;  
   GUID    guidModule;  
   DWORD   symid;  
} PDB_TYPE;  
```  
  
```csharp  
public struct PDB_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public uint symid;  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 ulAppDomainID  
 Identyfikator aplikacji, z której pochodzi symbol. Służy do jednoznacznego identyfikowania wystąpienia aplikacji.  
  
 guidModule  
 Identyfikator GUID modułu zawierającego to pole.  
  
 symid  
 Identyfikator symbolu, który odnosi się do tego pola.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest wyświetlana jako część Unii w strukturze [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) , gdy `dwKind` pole `TYPE_INFO` struktury jest ustawione na `TYPE_KIND_PDB` (wartość z wyliczenia [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
