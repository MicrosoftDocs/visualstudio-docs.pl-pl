---
title: IDebugSymbolProviderDirect | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d546cae810d40a850bb3dd2758f2f659eecdd18e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915679"
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
 Nagłówek: Sh.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll