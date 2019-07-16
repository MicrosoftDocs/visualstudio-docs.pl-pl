---
title: Symtagenum — | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1578d88265769414f68964e28d3426ffcc62f9e8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193521"
---
# <a name="symtagenum"></a>SymTagEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Określa typ symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum SymTagEnum {   
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
 `SymTagNull`  
 Wskazuje, że symbol nie ma typu.  
  
 `SymTagExe`  
 Wskazuje, czy symbol jest plik .exe. Jest tylko jedna `SymTagExe` symboli na magazynie symboli. On służy jako zasięg globalny i nie ma elementu nadrzędnego leksykalne.  
  
 `SymTagCompiland`  
 Wskazuje compiland — symbol dla każdego składnika compiland — w magazynie symboli. W przypadku aplikacji natywnych `SymTagCompiland` symbole odnoszą się do plików obiektu podłączonymi do obrazu. Dla niektórych typów obrazów firmy Microsoft Intermediate Language (MSIL) jest jednym compiland — na klasy.  
  
 `SymTagCompilandDetails`  
 Wskazuje, że symbol zawiera rozszerzonych atrybutów compiland —. Pobieranie właściwości te mogą wymagać ładowanie symboli compiland —.  
  
 `SymTagCompilandEnv`  
 Wskazuje, czy symbol jest ciągiem środowiska zdefiniowane dla compiland —.  
  
 `SymTagFunction`  
 Wskazuje, czy symbol jest funkcją.  
  
 `SymTagBlock`  
 Wskazuje, czy symbol jest zagnieżdżony blok.  
  
 `SymTagData`  
 Wskazuje, czy symbol jest danych.  
  
 `SymTagAnnotation`  
 Wskazuje, czy symbol jest dla adnotacji kodu. Elementy podrzędne tego symbolu są dane o stałych ciągów (`SymTagData`, `LocIsConstant`, `DataIsConstant`). Większość klientów Zignoruj ten symbol.  
  
 `SymTagLabel`  
 Wskazuje, czy symbol jest etykietę.  
  
 `SymTagPublicSymbol`  
 Wskazuje, czy symbol jest symboli publicznych. Dla natywnych aplikacji ten symbol jest symbol zewnętrzny COFF podczas łączenia obrazu.  
  
 `SymTagUDT`  
 Wskazuje, czy symbol jest typem zdefiniowanym przez użytkownika (struktury, klasy lub Unii).  
  
 `SymTagEnum`  
 Wskazuje, czy symbol jest wyliczenie.  
  
 `SymTagFunctionType`  
 Wskazuje, czy symbol jest typem podpisu funkcji.  
  
 `SymTagPointerType`  
 Wskazuje, czy symbol jest typem wskaźnika.  
  
 `SymTagArrayType`  
 Wskazuje, czy symbol jest typem tablicy.  
  
 `SymTagBaseType`  
 Wskazuje, czy symbol jest typem podstawowym.  
  
 `SymTagTypedef`  
 Wskazuje, czy symbol jest `typedef`, oznacza to, że alias dla innego typu.  
  
 `SymTagBaseClass`  
 Wskazuje, czy symbol jest klasą bazową dla typu zdefiniowanego przez użytkownika.  
  
 `SymTagFriend`  
 Wskazuje, że symbol jest znajomego typ zdefiniowany przez użytkownika.  
  
 `SymTagFunctionArgType`  
 Wskazuje, czy symbol jest argumentu funkcji.  
  
 `SymTagFuncDebugStart`  
 Wskazuje, czy symbol jest lokalizacji końcowej kodu prologu funkcji.  
  
 `SymTagFuncDebugEnd`  
 Wskazuje, czy symbol jest lokalizacja początku kod epilogu funkcji.  
  
 `SymTagUsingNamespace`  
 Wskazuje, czy symbol jest nazwą obszaru nazw, aktywne w bieżącym zakresie.  
  
 `SymTagVTableShape`  
 Wskazuje, czy symbol jest opis tabeli wirtualnej.  
  
 `SymTagVTable`  
 Wskazuje, czy symbol jest wskaźnikiem typu tabeli wirtualnej.  
  
 `SymTagCustom`  
 Wskazuje, czy symbol jest niestandardowego symbolu i nie będzie interpretowany przez DIA.  
  
 `SymTagThunk`  
 Wskazuje, czy symbol jest sekcją thunk używany do udostępniania danych między 16 i 32-bitowego.  
  
 `SymTagCustomType`  
 Wskazuje, że symbol jest symbol kompilatora niestandardowych.  
  
 `SymTagManagedType`  
 Wskazuje, czy symbol jest w metadanych.  
  
 `SymTagDimension`  
 Wskazuje, czy symbol jest FORTRAN tablicy wielowymiarowej.  
  
 `SymTagCallSite`  
 Wskazuje, że symbol reprezentuje wywołania.  
  
 `SymTagInlineSite`  
 Wskazuje, że symbol reprezentuje lokacji wbudowanego.  
  
 `SymTagBaseInterface`  
 Wskazuje, czy symbol jest interfejs podstawowy.  
  
 `SymTagVectorType`  
 Wskazuje, czy symbol jest typem wektora.  
  
 `SymTagMatrixType`  
 Wskazuje, czy symbol jest typem macierzy.  
  
 `SymTagHLSLType`  
 Wskazuje, czy symbol jest typem wysoki poziom programu do cieniowania języka.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie symbole w pliku debugowania ma identyfikujące tag, który określa typ symbolu.  
  
 Wartości w tym wyliczeniu są zwracane przez wywołanie [idiasymbol::get_symtag —](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) metody.  
  
 Wartości w tym wyliczeniu są przekazywane do poniższych metod, aby ograniczyć zakres wyszukiwania do typu określonego symbolu:  
  
- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Idiasession::findsymbolbyaddr —](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [Idiasession::findsymbolbyrva —](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)   
 [Idiasession::findsymbolbyrvaex —](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [Idiasession::findsymbolbytoken —](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [Idiasession::findsymbolbyva —](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [Idiasession::findsymbolbyvaex —](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [Idiasession::findchildren —](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
