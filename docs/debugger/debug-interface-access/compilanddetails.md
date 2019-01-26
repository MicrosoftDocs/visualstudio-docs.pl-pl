---
title: Compilanddetails — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 56ed4b317dc9259458ddb9f984c5d086595d7846
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033924"
---
# <a name="compilanddetails"></a>CompilandDetails
Compiland — informacje jest podzielony między symboli z `SymTagCompiland` tag (szczegóły niski) i `SymTagCompilandDetails` tag (wysoki poziom szczegółów). `SymTagCompilandDetails` wymaga dodatkowych symbole. Jednak zawiera mnóstwo informacji o compiland —, która nie jest dostępna z `SymTagCompiland` symboli.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli przedstawiono właściwości, które są prawidłowe dla tego typu symbolu.  
  
|Właściwość|Typ danych|Opis|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Numer kompilacji zaplecza kompilatora.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Serwer zaplecza główny numer wersji kompilatora.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Serwer zaplecza pomocniczy numer wersji kompilatora.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Nazwa kompilatora wytworzonego to compiland — (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` Jeśli Edytuj i Kontynuuj zostały włączone w kompilacji.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Numer kompilacji fronton kompilatora.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Fronton główny numer wersji kompilatora.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Fronton pomocniczy numer wersji kompilatora.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Jeśli ta compiland — zawiera informacje o debugowaniu (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Jeśli ta compiland — zawiera kod zarządzany (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Jeśli compiland — został skompilowany przy użyciu [/GS (Sprawdzanie zabezpieczeń bufora)](/cpp/build/reference/gs-buffer-security-check) przełącznika kompilatora (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` Jeśli compiland — została przekonwertowana z kodu wspólny język pośredni (CIL) do kodu macierzystego.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Jeśli typy zdefiniowane przez użytkownika (UDT) mają zostać wyrównane do niektórych określona granica pamięci (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` Jeśli compiland — został skompilowany przy użyciu [/hotpatch (Utwórz obraz Hotpatchable)](/cpp/build/reference/hotpatch-create-hotpatchable-image) przełącznika kompilatora (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` Jeśli compiland — został skompilowany przy użyciu [opcję/LTCG (Generowanie kodu Link-time)](/cpp/build/reference/ltcg-link-time-code-generation) przełącznika kompilatora (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|Wartość TRUE, jeśli compiland — to moduł Microsoft Intermediate Language (MSIL) (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Język kodu źródłowego.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Compiland — symbol.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identyfikator symbol leksykalne nadrzędnej.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Platformy, na którym został skompilowany compiland — (jeden z [cv_cpu_type_e — wyliczenie](../../debugger/debug-interface-access/cv-cpu-type-e.md) wartości).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Identyfikator indeksu: symbolu.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Zwraca `SymTagCompilandDetails` (jeden z [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wartości).|  
  
## <a name="remarks"></a>Uwagi  
 Kompilatory często jest opracowywane w formularzu, znane jako kompilatora dwuprzebiegową; w niektórych wersjach kompilatora każdego przebiegu odbywa się przez inny program. Te są nazywane kompilatory frontonu i zaplecza, odpowiednio, dlatego właściwości symbolu numerów wersji zaplecza i frontonu.  
  
## <a name="see-also"></a>Zobacz też  
 [Compiland —](../../debugger/debug-interface-access/compiland.md)   
 [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)