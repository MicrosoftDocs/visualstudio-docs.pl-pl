---
title: CompilandDetails | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da102a8968bc3e29091f6b4b58ee6ef78c6c3fb3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462254"
---
# <a name="compilanddetails"></a>CompilandDetails
Informacje jednostka kompilacji są dzielone między symbolami ze `SymTagCompiland` znacznikiem (Low detail) i `SymTagCompilandDetails` tagiem (High detail). `SymTagCompilandDetails` zawiera mnóstwo informacji o jednostka kompilacji, które nie są dostępne z `SymTagCompiland` symbolem.

## <a name="properties"></a>Właściwości
 W poniższej tabeli przedstawiono właściwości, które są prawidłowe dla tego typu symbolu.

|Właściwość|Typ danych|Opis|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Numer kompilacji zaplecza kompilatora.|
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Główny numer wersji kompilatora.|
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Wewnętrzny numer wersji kompilatora.|
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Nazwa kompilatora, który wygenerował ten jednostka kompilacji (tylko w DIA SDK V 8.0 lub nowszym).|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` Jeśli funkcja Edytuj i Kontynuuj została włączona podczas kompilacji.|
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Numer kompilacji frontonu kompilatora.|
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Główny numer wersji kompilatora.|
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Wewnętrzny numer wersji kompilatora.|
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Jeśli ten jednostka kompilacji zawiera informacje debugowania (tylko w DIA SDK V 8.0 lub nowszym).|
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Jeśli ten jednostka kompilacji zawiera kod zarządzany (tylko w DIA SDK v 8.0 lub nowszym).|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Jeśli jednostka kompilacji został skompilowany za pomocą przełącznika kompilatora [/GS (buffer Security Check)](/cpp/build/reference/gs-buffer-security-check) (tylko w DIA SDK v 8.0 lub nowszym).|
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` Jeśli jednostka kompilacji został przekonwertowany ze wspólnego kodu języka pośredniego (CIL) na kod natywny.|
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Jeśli typy zdefiniowane przez użytkownika (UDT) zostały wyrównane do określonej granicy pamięci (tylko w DIA SDK V 8.0 lub nowszym).|
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` Jeśli jednostka kompilacji został skompilowany za pomocą przełącznika kompilatora [/hotpatch (Utwórz obraz możliwy do poprawiania)](/cpp/build/reference/hotpatch-create-hotpatchable-image) (tylko w DIA SDK v 8.0 lub nowszym).|
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` Jeśli jednostka kompilacji zostały skompilowane przy użyciu przełącznika kompilatora [/LTCG (generowanie kodu w czasie konsolidacji)](/cpp/build/reference/ltcg-link-time-code-generation) (tylko w DIA SDK v 8.0 lub nowszym).|
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|TRUE, jeśli jednostka kompilacji jest modułem języka pośredniego (MSIL) firmy Microsoft (tylko w DIA SDK v 8.0 lub nowszym).|
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Język kodu źródłowego.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol dla jednostka kompilacji.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identyfikator leksykalnego symbolicznego symbolu.|
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Platforma, na której została skompilowana jednostka kompilacji (jedna z wartości [wyliczenia CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) ).|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Identyfikator indeksu symbolu.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Zwraca `SymTagCompilandDetails` (jedną z wartości [wyliczenia SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) ).|

## <a name="remarks"></a>Uwagi
 Kompilatory często mają postać znaną jako kompilator dwuprzebiegowy; w niektórych wersjach kompilatora każdy przebieg jest obsługiwany przez osobny program. Są one znane odpowiednio jako kompilatory frontonu i zaplecza, dlatego Właściwości symboli dla numerów wersji zaplecza i frontonu.

## <a name="see-also"></a>Zobacz też
- [Jednostka kompilacji](../../debugger/debug-interface-access/compiland.md)
- [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)