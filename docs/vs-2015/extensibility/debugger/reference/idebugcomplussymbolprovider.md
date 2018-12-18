---
title: IDebugComPlusSymbolProvider | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 036d545b6bc8f2b59b76fdbc777680d0307f6972
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721984"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Reprezentuje dostawcę symbol modelu COM +, za pomocą metod, które są specyficzne dla kodu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Mimo że istnieje bez separacji między interfejsy, które są przydatne do ewaluatora wyrażeń (EE), które są przeznaczone do użycia przez aparat debugowania (DE), następujące metody prawdopodobnie będzie interesują tylko deweloperów DE: AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols i UpdateSymbols.  
  
## <a name="methods"></a>Metody  
 Oprócz metod na [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) interfejsu, ten interfejs implementuje następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Określa, jeśli dla określonego modułu podany identyfikator domeny aplikacji, czy załadowano symbole debugowania.|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Tworzy typ z określonego typu pierwotnego.|  
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Mapuje położenie dokumentu, w określonym module na tablicę adresów debugowania.|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Pobiera typ informacji o określonej tablicy, na podstawie jego adresu debugowania.|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Pobiera nazwę zestawu, biorąc pod uwagę jego domeny moduł i aplikacji.|  
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Pobiera klasy przy użyciu określonego atrybutu, które są implementowane w danym języku programowania.|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Pobiera klasy przy użyciu określonego atrybutu w danym module.|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Pobiera punkt wejścia aplikacji.|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Pobiera adres w ramach funkcji, która reprezentuje przesunięcie w danym wierszu.|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Pobiera układ zmienne lokalne, aby uzyskać zestaw metod.|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Zwraca nazwę skojarzone z tokenem określony, biorąc pod uwagę jej obiektu metadanych.|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Pobiera symbole debugowania z atrybutem nadrzędnym podanego dla określonego modułu.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Pobiera czytnika symboli, który będzie używany przez kod niezarządzany.|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Pobiera typ symbolu, podany adres debugowania.|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Określa, w przypadku funkcji pod adresem określonym debugowania zostaną usunięte.|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Określa, czy funkcja pod adresem określonym debugowania jest uznawane za przestarzałe.|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Określa, jeśli kod pod adresem określonym debugera jest ukryta.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Ładuje symbole debugowania określony w pamięci.|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Obciążenie debugowania symbole danego strumienia danych.|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Zamienia bieżące symbole debugowania znajdującymi się na strumieniu określone dane.|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Zwalnia symbole debugowania dla określonego modułu z pamięci.|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Aktualizuje symbole debugowania w pamięci z tymi strumienia określone dane.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

