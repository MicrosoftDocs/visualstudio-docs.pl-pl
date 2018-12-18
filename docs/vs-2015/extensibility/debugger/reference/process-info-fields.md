---
title: PROCESS_INFO_FIELDS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d4349a4a2ad55c53886ab281652ff990aa608682
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807741"
---
# <a name="processinfofields"></a>PROCESS_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określić, jakiego rodzaju informacje należy pobrać dla procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
typedef DWORD PROCESS_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 PIF_FILE_NAME  
 Inicjowanie bądź użyj `bstrFileName` pole [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struktury.  
  
 PIF_BASE_NAME  
 Inicjowanie bądź użyj `bstrBaseName` pole `PROCESS_INFO` struktury.  
  
 PIF_TITLE  
 Inicjowanie bądź użyj `bstrTitle` pole `PROCESS_INFO` struktury.  
  
 PIF_PROCESS_ID  
 Inicjowanie bądź użyj `ProcessId` pole `PROCESS_INFO` struktury.  
  
 PIF_SESSION_ID  
 Inicjowanie bądź użyj `dwSessionId` pole `PROCESS_INFO` struktury.  
  
 PIF_ATTACHED_SESSION_NAME  
 Inicjowanie bądź użyj `bstrAttachedSessionName` pole `PROCESS_INFO` struktury.  
  
 PIF_CREATION_TIME  
 Inicjowanie bądź użyj `CreationTime` pole `PROCESS_INFO` struktury.  
  
 PIF_FLAGS  
 Inicjowanie bądź użyj `Flags` pole `PROCESS_INFO` struktury.  
  
 PIF_ALL  
 Wypełnia wszystkie pola.  
  
## <a name="remarks"></a>Uwagi  
 Przekazany do [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) metodę, aby wskazać, które pola [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struktury, które mają zostać zainicjowane.  
  
 Używany również w `Fields` pole `PROCESS_INFO` struktury, aby wskazać, które pola są używane i prawidłowy.  
  
 Te flagi mogą być łączone przy użyciu bitowego operatora `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)

