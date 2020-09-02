---
title: IDebugComPlusSymbolProvider | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b70701aa9c4b339749554601e2a565c17697c6a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186516"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Reprezentuje dostawcę symboli modelu COM+ z metodami specyficznymi dla kodu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Chociaż nie ma rozdzielania między interfejsami, które są przydatne dla ewaluatora wyrażeń (EE) i tych, które są przeznaczone do użycia przez aparat debugowania (DE), następujące metody prawdopodobnie będą interesować tylko: AreSymbolsLoaded, GetAddressesInModuleFromPosition, getentrypoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols, UpdateSymbols  
  
## <a name="methods"></a>Metody  
 Oprócz metod interfejsu [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) , ten interfejs implementuje następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Określa, czy symbole debugowania są ładowane dla określonego modułu o identyfikatorze domeny aplikacji.|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Tworzy typ z określonego typu pierwotnego.|  
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Mapuje pozycję dokumentu w określonym module na tablicę adresów debugowania.|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Pobiera informacje o typie dla określonej tablicy z uwzględnieniem jego adresu debugowania.|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Pobiera nazwę zestawu, w którym zamieszczono jego moduł i domenę aplikacji.|  
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Pobiera klasy z określonym atrybutem, które są implementowane w danym języku programowania.|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Pobiera klasy z określonym atrybutem w danym module.|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Pobiera punkt wejścia aplikacji.|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Pobiera adres w ramach funkcji, która reprezentuje podane przesunięcie wiersza.|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Pobiera układ zmiennych lokalnych dla zestawu metod.|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Zwraca nazwę skojarzoną z określonym tokenem, w której znajduje się obiekt metadanych.|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Pobiera symbole debugowania z podanym atrybutem nadrzędnym dla określonego modułu.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Pobiera czytnik symboli, który ma być używany przez kod niezarządzany.|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Pobiera do typu symbolu z uwzględnieniem jego adresu debugowania.|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Określa, czy funkcja pod określonym adresem debugowania jest usuwana.|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Określa, czy funkcja pod określonym adresem debugowania jest uważana za przestarzałą.|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Określa, czy kod pod określonym adresem debugera jest ukryty.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Ładuje określone symbole debugowania w pamięci.|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Ładuje symbole debugowania danego strumienia danych.|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Zamienia bieżące symbole debugowania na te w określonym strumieniu danych.|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Zwalnia symbole debugowania dla określonego modułu z pamięci.|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Aktualizuje symbole debugowania w pamięci za pomocą tych określonego strumienia danych.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
