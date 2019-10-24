---
title: SymTagEnum — | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 806fe878468baa06b52a15879ceaff1b376461e9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738516"
---
# <a name="symtagenum"></a>SymTagEnum
Określa typ symbolu.

## <a name="syntax"></a>Składnia

```C++
enum SymTagEnum {
    SymTagNull,
    SymTagExe,
    SymTagCompiland,
    SymTagCompilandDetails,
    SymTagCompilandEnv,
    SymTagFunction,
    SymTagBlock,
    SymTagData,
    SymTagAnnotation,
    SymTagLabel,
    SymTagPublicSymbol,
    SymTagUDT,
    SymTagEnum,
    SymTagFunctionType,
    SymTagPointerType,
    SymTagArrayType,
    SymTagBaseType,
    SymTagTypedef,
    SymTagBaseClass,
    SymTagFriend,
    SymTagFunctionArgType,
    SymTagFuncDebugStart,
    SymTagFuncDebugEnd,
    SymTagUsingNamespace,
    SymTagVTableShape,
    SymTagVTable,
    SymTagCustom,
    SymTagThunk,
    SymTagCustomType,
    SymTagManagedType,
    SymTagDimension,
    SymTagCallSite,
    SymTagInlineSite,
    SymTagBaseInterface,
    SymTagVectorType,
    SymTagMatrixType,
    SymTagHLSLType
};
```

## <a name="elements"></a>Elementy
`SymTagNull` wskazuje, że symbol nie ma typu.

`SymTagExe` wskazuje, że symbol jest plikiem exe. Istnieje tylko jeden `SymTagExe` symbol dla magazynu symboli. Pełni rolę zakresu globalnego i nie ma leksykalnego elementu nadrzędnego.

`SymTagCompiland` wskazuje symbol jednostka kompilacji dla każdego składnika jednostka kompilacji magazynu symboli. W przypadku aplikacji natywnych symbole `SymTagCompiland` odpowiadają plikom obiektów połączonym z obrazem. W przypadku niektórych rodzajów obrazów języka pośredniego firmy Microsoft (MSIL) istnieje jeden jednostka kompilacji na klasę.

`SymTagCompilandDetails` wskazuje, że symbol zawiera rozszerzone atrybuty jednostka kompilacji. Pobranie tych właściwości może wymagać załadowania symboli jednostka kompilacji.

`SymTagCompilandEnv` wskazuje, że symbol jest ciągiem środowiska zdefiniowanym dla jednostka kompilacji.

`SymTagFunction` wskazuje, że symbol jest funkcją.

`SymTagBlock` wskazuje, że symbol jest zagnieżdżonym blokiem.

`SymTagData` wskazuje, że symbol to dane.

`SymTagAnnotation` wskazuje, że symbol jest przeznaczony dla adnotacji kodu. Elementy podrzędne tego symbolu są stałymi ciągami danych (`SymTagData`, `LocIsConstant`, `DataIsConstant`). Większość klientów ignoruje ten symbol.

`SymTagLabel` wskazuje, że symbol jest etykietą.

`SymTagPublicSymbol` wskazuje, że symbol jest symbolem publicznym. W przypadku aplikacji natywnych ten symbol jest zewnętrznym symbolem COFF podczas łączenia obrazu.

`SymTagUDT` wskazuje, że symbol jest typem zdefiniowanym przez użytkownika (strukturą, klasą lub Unią).

`SymTagEnum` wskazuje, że symbol jest wyliczeniem.

`SymTagFunctionType` wskazuje, że symbol jest typem sygnatury funkcji.

`SymTagPointerType` wskazuje, że symbol jest typem wskaźnika.

`SymTagArrayType` wskazuje, że symbol jest typem tablicy.

`SymTagBaseType` wskazuje, że symbol jest typem podstawowym.

`SymTagTypedef` wskazuje, że symbol jest `typedef`, czyli alias dla innego typu.

`SymTagBaseClass` wskazuje, że symbol jest klasą bazową typu zdefiniowanego przez użytkownika.

`SymTagFriend` wskazuje, że symbol jest znajomością typu zdefiniowanego przez użytkownika.

`SymTagFunctionArgType` wskazuje, że symbol jest argumentem funkcji.

`SymTagFuncDebugStart` wskazuje, że symbol jest lokalizacją końcową kodu prologu funkcji.

`SymTagFuncDebugEnd` wskazuje, że symbol jest początkową lokalizacją kodu epilogu funkcji.

`SymTagUsingNamespace` wskazuje, że symbol jest nazwą przestrzeni nazw, aktywną w bieżącym zakresie.

`SymTagVTableShape` wskazuje, że symbol jest opisem tabeli wirtualnej.

`SymTagVTable` wskazuje, że symbol jest wskaźnikiem tabeli wirtualnej.

`SymTagCustom` wskazuje, że symbol jest symbolem niestandardowym i nie jest interpretowany przez DIA.

`SymTagThunk` wskazuje, że symbol jest thunk używany do udostępniania danych między 16 i 32 bitowym kodem.

`SymTagCustomType` wskazuje, że symbol jest niestandardowym symbolem kompilatora.

`SymTagManagedType` wskazuje, że symbol jest w metadanych.

`SymTagDimension` wskazuje, że symbol jest tablicą wielowymiarową Pascal.

`SymTagCallSite` wskazuje, że symbol reprezentuje witrynę wywołania.

`SymTagInlineSite` wskazuje, że symbol reprezentuje lokację wbudowaną.

`SymTagBaseInterface` wskazuje, że symbol jest interfejsem podstawowym.

`SymTagVectorType` wskazuje, że symbol jest typem wektora.

`SymTagMatrixType` wskazuje, że symbol jest typem macierzy.

`SymTagHLSLType` wskazuje, że symbol jest typem języka cieniowania wysokiego poziomu.

## <a name="remarks"></a>Uwagi
Wszystkie symbole w pliku debugowania mają tag identyfikujący, który określa typ symbolu.

Wartości w tym wyliczeniu są zwracane przez wywołanie metody [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) .

Wartości w tym wyliczeniu są przesyłane do następujących metod w celu ograniczenia zakresu wyszukiwania do określonego typu symbolu:

- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)

- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)

- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)

- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)

- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)

- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst. h

## <a name="see-also"></a>Zobacz także
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)
- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)
- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)
- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)
- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
