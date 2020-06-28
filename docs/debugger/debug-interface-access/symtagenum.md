---
title: SymTagEnum — | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 29bbb4eed485d3ff354757ab8c83a60b92f566aa
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461050"
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
`SymTagNull`Wskazuje, że symbol nie ma typu.

`SymTagExe`Wskazuje, że symbol jest plikiem exe. Istnieje tylko jeden `SymTagExe` symbol dla magazynu symboli. Pełni rolę zakresu globalnego i nie ma leksykalnego elementu nadrzędnego.

`SymTagCompiland`Wskazuje symbol jednostka kompilacji dla każdego składnika jednostka kompilacji magazynu symboli. W przypadku aplikacji natywnych `SymTagCompiland` symbole odpowiadają plikom obiektów podłączonym do obrazu. W przypadku niektórych rodzajów obrazów języka pośredniego firmy Microsoft (MSIL) istnieje jeden jednostka kompilacji na klasę.

`SymTagCompilandDetails`Wskazuje, że symbol zawiera rozszerzone atrybuty jednostka kompilacji. Pobranie tych właściwości może wymagać załadowania symboli jednostka kompilacji.

`SymTagCompilandEnv`Wskazuje, że symbol jest ciągiem środowiska zdefiniowanym dla jednostka kompilacji.

`SymTagFunction`Wskazuje, że symbol jest funkcją.

`SymTagBlock`Wskazuje, że symbol jest zagnieżdżonym blokiem.

`SymTagData`Wskazuje, że symbol to dane.

`SymTagAnnotation`Wskazuje, że symbol jest przeznaczony dla adnotacji kodu. Elementy podrzędne tego symbolu są stałymi ciągami danych ( `SymTagData` , `LocIsConstant` , `DataIsConstant` ). Większość klientów ignoruje ten symbol.

`SymTagLabel`Wskazuje, że symbol jest etykietą.

`SymTagPublicSymbol`Wskazuje, że symbol jest symbolem publicznym. W przypadku aplikacji natywnych ten symbol jest zewnętrznym symbolem COFF podczas łączenia obrazu.

`SymTagUDT`Wskazuje, że symbol jest typem zdefiniowanym przez użytkownika (strukturą, klasą lub Unią).

`SymTagEnum`Wskazuje, że symbol jest wyliczeniem.

`SymTagFunctionType`Wskazuje, że symbol jest typem sygnatury funkcji.

`SymTagPointerType`Wskazuje, że symbol jest typem wskaźnika.

`SymTagArrayType`Wskazuje, że symbol jest typem tablicy.

`SymTagBaseType`Wskazuje, że symbol jest typem podstawowym.

`SymTagTypedef`Wskazuje, że symbol jest `typedef` , czyli alias dla innego typu.

`SymTagBaseClass`Wskazuje, że symbol jest klasą bazową typu zdefiniowanego przez użytkownika.

`SymTagFriend`Wskazuje, że symbol jest znajomością typu zdefiniowanego przez użytkownika.

`SymTagFunctionArgType`Wskazuje, że symbol jest argumentem funkcji.

`SymTagFuncDebugStart`Wskazuje, że symbol jest lokalizacją końcową kodu prologu funkcji.

`SymTagFuncDebugEnd`Wskazuje, że symbol jest początkową lokalizacją kodu epilogu funkcji.

`SymTagUsingNamespace`Wskazuje, że symbol jest nazwą przestrzeni nazw, aktywną w bieżącym zakresie.

`SymTagVTableShape`Wskazuje, że symbol jest opisem tabeli wirtualnej.

`SymTagVTable`Wskazuje, że symbol jest wskaźnikiem tabeli wirtualnej.

`SymTagCustom`Wskazuje, że symbol jest symbolem niestandardowym i nie jest interpretowany przez DIA.

`SymTagThunk`Wskazuje, że symbol jest thunk używany do udostępniania danych między 16 i 32 bitowym kodem.

`SymTagCustomType`Wskazuje, że symbol jest niestandardowym symbolem kompilatora.

`SymTagManagedType`Wskazuje, że symbol jest w metadanych.

`SymTagDimension`Wskazuje, że symbol jest tablicą wielowymiarową Pascal.

`SymTagCallSite`Wskazuje, że symbol reprezentuje witrynę wywołania.

`SymTagInlineSite`Wskazuje, że symbol reprezentuje lokację wbudowaną.

`SymTagBaseInterface`Wskazuje, że symbol jest interfejsem podstawowym.

`SymTagVectorType`Wskazuje, że symbol jest typem wektora.

`SymTagMatrixType`Wskazuje, że symbol jest typem macierzy.

`SymTagHLSLType`Wskazuje, że symbol jest typem języka cieniowania wysokiego poziomu.

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

## <a name="see-also"></a>Zobacz też
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
