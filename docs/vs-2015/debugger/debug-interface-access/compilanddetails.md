---
title: Compilanddetails — | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 34349bf096d8bb98ae4b3de7c7a922b8d28bc4f8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703001"
---
# <a name="compilanddetails"></a>CompilandDetails
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Jeśli compiland — został skompilowany przy użyciu [/GS (Sprawdzanie zabezpieczeń bufora)](https://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e) przełącznika kompilatora (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` Jeśli compiland — została przekonwertowana z kodu wspólny język pośredni (CIL) do kodu macierzystego.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Jeśli typy zdefiniowane przez użytkownika (UDT) mają zostać wyrównane do niektórych określona granica pamięci (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` Jeśli compiland — został skompilowany przy użyciu [/hotpatch (Utwórz obraz Hotpatchable)](https://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798) przełącznika kompilatora (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` Jeśli compiland — został skompilowany przy użyciu [opcję/LTCG (Generowanie kodu Link-time)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) przełącznika kompilatora (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
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
