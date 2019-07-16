---
title: SEEK_START | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 45e664b153c4d643d8fbe8f1cefb207e0a76e18e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204877"
---
# <a name="seekstart"></a>SEEK_START
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa położenie, z którym ma zostać rozpoczęte wyszukiwanie w strumieniu dezasemblacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
typedef DWORD SEEK_START;  
```  
  
```csharp  
public enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 SEEK_START_BEGIN  
 Rozpoczyna się wyszukiwanie od początku bieżącego dokumentu.  
  
 SEEK_START_END  
 Rozpoczyna się wyszukiwanie na koniec bieżącego dokumentu.  
  
 SEEK_START_CURRENT  
 Rozpoczyna się wyszukiwanie w bieżącym położeniu bieżącego dokumentu.  
  
 SEEK_START_CODECONTEXT  
 Rozpoczyna się wyszukiwanie w kontekście danego kodu bieżącego dokumentu.  
  
 SEEK_START_CODELOCID  
 Rozpoczyna się wyszukiwanie na identyfikator lokalizacji danego kodu. Identyfikatory lokalizacji kodu są pobierane przez wywołanie metody [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md).  
  
## <a name="remarks"></a>Uwagi  
 Przekazywany jako argument do [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Wyszukiwanie](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)   
 [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
