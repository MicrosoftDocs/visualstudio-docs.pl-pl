---
title: IDebugSymbolProviderDirect | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 64cab3dde38f3008a097e89b17b2d61921332ed6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53965317"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Reprezentuje dostawcę symbol, który ma bezpośredni dostęp do metadanych i podstawowych interfejsów symboli.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugSymbolProviderDirect: IUnknown  
```  
  
## <a name="methods"></a>Metody  
 Ten interfejs implementuje następujących metod:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Pobiera identyfikator domeny aplikacji, mając adres debugowania.|  
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Pobiera informacje o modułach w grupie symboli.|  
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Pobiera informacje o grupie symbol dostawca symboli jest elementem członkowskim.|  
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Pobiera informacje o Importowanie metadanych.|  
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Pobiera informacje o metodzie pod adresem określonym debugowania.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Pobiera czytnik symbolu dla niezarządzanego kodu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs można używać zamiast większość inne interfejsy dostawcy symboli. Zapewnia bezpośredni dostęp do metadanych i `CorSym` interfejsów.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: SH.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll