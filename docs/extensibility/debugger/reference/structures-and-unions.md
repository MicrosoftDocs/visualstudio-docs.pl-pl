---
title: Struktury i związki | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e0ef171d24b3744657a2cb05338b2b124a6331c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62864677"
---
# <a name="structures-and-unions"></a>Struktury i związki
Poniżej przedstawiono struktur i Unii w Visual Studio SDK debugowania.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Określa identyfikator procesu, który może mieć identyfikator systemu lub identyfikator GUID.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) opisuje warunki, na których zostanie uruchomiony punkt przerwania.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) opisuje rozwiązanie punktu przerwania błędu, takie jak lokalizacja, program i wątku.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Określa typ struktury, używane do opisywania lokalizację punktu przerwania.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) definiuje składników, które opisują lokalizację punktu przerwania pod adresem w kodzie.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) wskazuje lokalizację, w punkcie przerwania, który jest powiązany bezpośrednio z adresu w debugowanego programu.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) opisuje lokalizacji punktu przerwania w wierszu w pliku kodu źródłowego.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) opisuje przesunięcia lokalizacji punktu przerwania w funkcji w kodzie.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) używana do ustawiania punktów przerwania kodu na podstawie ciągu, który użytkownik może wprowadzić z poziomu środowiska IDE.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) używana do ustawiania punktów przerwania danych, które są oparte na ciąg, który użytkownik może wprowadzić z poziomu środowiska IDE.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) opisuje rozwiązanie punktu przerwania w określonej lokalizacji.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) opisuje liczbę i warunki, na których punkt przerwania zostanie wyzwolone po został wcześniej przekazany.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) zawiera informacje wymagane do zaimplementowania punktu przerwania.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) zawiera informacje wymagane do zaimplementowania punktu przerwania (taka sama jak [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struktura ale zawiera identyfikator GUID, ograniczenia i śledzenia informacje na temat dostawcy).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) opisuje lokalizacji punktu przerwania w kodzie.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) przedstawia wynik powiązania punktu przerwania danych.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) opisano informacje powiązany punkt przerwania dla punktu przerwania w kodzie lub punktu przerwania danych.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) określa strukturę Rozpoznawanie lokalizacji punktu przerwania.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) opisuje tablicę ciągów.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) określa informacje o typie pola pobierana z metadanych.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) opisuje wywołanie funkcji lub metody.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) opisuje komputera, na którym uruchomiony jest debugera.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) opisuje listę identyfikatorów GUID.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) opisuje kontekst pamięci lub kontekst kodu.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) opisuje adres debugowanego programu.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) reprezentuje jeden z wielu różnych rodzajów adresów.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) określa podglądu niestandardowego lub Wizualizator typów.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) opisuje właściwość debugowania, który z kolei opisuje obiekt hierarchiczny charakter, który ma nazwę, typ i wartość.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) opisuje odwołania.

- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) opisuje dezasemblacji środowiska IDE w celu wyświetlenia.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) opisuje błąd wyjątku lub czasu wykonywania zgłoszony przez debugowanego programu.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) opisuje zmienną lokalną, parametr lub innego pola.

- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) opisuje ramki stosu.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) opisuje tablicę unikatowych identyfikatorów dla silniki debugowania dostępnych.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) używane do ustawiania informacji JustMyCode dla modułu.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) opisuje określonego komputera.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) opisuje elementu w tablicy w tablicy.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) opisuje adresu pola klasy lub struktury.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) opisuje adresu lokalnej zmiennej w zakresie (zazwyczaj funkcja lub metoda).

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) opisuje adres metody klasy.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) opisuje parametr metody lub funkcji.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) opisuje wartość zwracana z metody lub funkcji.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) opisuje typ pola pobierana z metadanych.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) opisuje konkretnego modułu (DLL, EXE lub zestawu).

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) opisuje informacje o stanie dotyczące ścieżki wyszukiwania symboli, które zostały przeszukiwane.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) opisuje adresu natywnego.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) opisuje typ pola z symboli PDB.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) opisuje stan punktu przerwania, który jest gotowy do powiązania do lokalizacji kodu.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) w tym artykule opisano proces.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) opisuje listę [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) obiekty reprezentujące węzły programu.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) opisano procesy uruchomione na maszynie.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) wskazuje lokalizację, wierszy i kolumn w podanym tekście.

- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) opisano właściwości obiektu wątku.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) opisuje typ pola.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) opisuje adresu fizycznego.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) opisuje adres który będzie względne `this` wskaźnika (`Me` w języku Visual Basic).

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h sh.h i ee.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Dokumentacja interfejsu API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)