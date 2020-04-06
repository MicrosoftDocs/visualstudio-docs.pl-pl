---
title: IDebugSymbolProviderDirect | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd1201007b27d3c7c51b5b0d862b36ba0549429b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718905"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Reprezentuje dostawcę symboli, który ma bezpośredni dostęp do metadanych i interfejsów symboli podstawowych.

## <a name="syntax"></a>Składnia

```
IDebugSymbolProviderDirect: IUnknown
```

## <a name="methods"></a>Metody
 Ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Pobiera identyfikator domeny aplikacji podany adres debugowania.|
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Pobiera informacje o modułach w grupie symboli.|
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Pobiera informacje o grupie symboli, której członkiem jest dostawca symboli.|
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Pobiera informacje o imporcie metadanych.|
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Pobiera informacje o metodzie pod określonym adresem debugowania.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Pobiera czytnik symboli dla kodu niezarządzanego.|

## <a name="remarks"></a>Uwagi
 Ten interfejs może być używany zamiast większości innych interfejsów dostawcy symboli. Zapewnia bezpośredni dostęp do metadanych i `CorSym` interfejsów.

## <a name="requirements"></a>Wymagania
 Nagłówek: Sh.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
