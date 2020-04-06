---
title: IDebugComPlusSymbolProvider | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 482ea1b2fb2eb7ddad46bd99694e4599e9fd9bbe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733476"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
Reprezentuje dostawcę symboli COM+ z metodami specyficznymi dla kodu zarządzanego.

## <a name="syntax"></a>Składnia

```
IDebugComPlusSymbolProvider : IDebugSymbolProvider
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Chociaż nie istnieje separacja między interfejsami, które są przydatne dla oceniającego wyrażenie (EE) i tych, które są przeznaczone do użycia przez aparat debugowania (DE), następujące metody będą prawdopodobnie interesować de deweloperów tylko: AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols i UpdateSymbols.

## <a name="methods"></a>Metody
 Oprócz metod na interfejsie [IDebugSymbolProvider,](../../../extensibility/debugger/reference/idebugsymbolprovider.md) ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Określa, czy symbole debugowania są ładowane dla określonego modułu, biorąc pod uwagę identyfikator domeny aplikacji.|
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Tworzy typ z określonego typu pierwotnego.|
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Mapuje pozycję dokumentu w określonym module do tablicy adresów debugowania.|
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Pobiera informacje o typie o określonej tablicy, biorąc pod uwagę jego adres debugowania.|
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Pobiera nazwę zestawu, biorąc pod uwagę jego moduł i domenę aplikacji.|
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Pobiera klasy z określonym atrybutem, które są implementowane w danym języku programowania.|
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Pobiera klasy z określonym atrybutem w danym module.|
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Pobiera punkt wejścia aplikacji.|
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Pobiera adres w ramach funkcji, która reprezentuje danego odsunięcia wiersza.|
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Pobiera układ zmiennych lokalnych dla zestawu metod.|
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Zwraca nazwę skojarzoną z określonym tokenem, biorąc pod uwagę jego obiekt metadanych.|
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Pobiera symbole debugowania z atrybutem nadrzędnym dla określonego modułu.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Pobiera czytnik symboli, który ma być używany przez kod niezarządzany.|
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Pobiera do typu symbolu, biorąc pod uwagę jego adres debugowania.|
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Określa, czy funkcja pod określonym adresem debugowania jest usuwana.|
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Określa, czy funkcja pod określonym adresem debugowania jest uważana za przestarzałą.|
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Określa, czy kod pod określonym adresem debugera jest ukryty.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Ładuje określone symbole debugowania w pamięci.|
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Ładuje symbole debugowania, biorąc pod uwagę strumień danych.|
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Zastępuje bieżące symbole debugowania symbolami w określonym strumieniu danych.|
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Zwalnia symbole debugowania dla określonego modułu z pamięci.|
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Aktualizuje symbole debugowania w pamięci z tymi określonym strumieniem danych.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Sh.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
