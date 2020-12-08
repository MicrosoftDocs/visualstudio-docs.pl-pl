---
title: Struktury i związki | Microsoft Docs
description: Ten artykuł zawiera linki do dokumentacji dotyczącej struktur i Unii w zestawie SDK debugowania programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1f477b46083b5abd5b8e93593cc728b660b58d9
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845768"
---
# <a name="structures-and-unions"></a>Struktury i związki
Poniżej przedstawiono struktury i związki w zestawie SDK debugowania programu Visual Studio.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Określa identyfikator procesu, który może być IDENTYFIKATORem systemowym lub GUID.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Opisuje warunki, w których zostanie uruchomiony punkt przerwania.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Opisuje rozwiązanie punktu przerwania błędu, w tym lokalizacji, programu i wątku.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Określa typ struktury używany do opisywania lokalizacji punktu przerwania.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) Definiuje składniki opisujące lokalizację punktu przerwania pod adresem w kodzie.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) Opisuje lokalizację punktu przerwania, który jest powiązany bezpośrednio z adresem w debugowanym programie.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Opisuje lokalizację punktu przerwania w wierszu w pliku źródłowym kodu.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) Opisuje lokalizację przesunięcia punktu przerwania w funkcji w kodzie.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) Służy do ustawiania punktów przerwania kodu na podstawie ciągu, który użytkownik może wprowadzić z IDE.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) Służy do ustawiania punktów przerwania danych opartych na ciągu, który użytkownik może wprowadzić z IDE.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) Opisuje rozdzielczość punktu przerwania w określonej lokalizacji.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Opisuje liczbę i warunki, w których punkt przerwania zostanie wyzwolony po jego wcześniejszym przekazaniu.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Zawiera informacje wymagane do zaimplementowania punktu przerwania.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Zawiera informacje wymagane do zaimplementowania punktu przerwania (takiego jak struktura [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) , ale zawiera identyfikator GUID dostawcy, informacje o ograniczeniu i punkt śledzenia).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) Opisuje lokalizację punktu przerwania kodu.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) Opisuje wynik powiązania punktu przerwania danych.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Opisuje powiązane informacje o punkcie przerwania dla punktu przerwania kodu lub punktu przerwania danych.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Określa strukturę lokalizacji rozpoznawania punktów przerwania.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) Opisuje tablicę ciągów.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Określa informacje o typie pola pobieranym z metadanych.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) Opisuje wywołanie funkcji lub metody.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) Opisuje komputer, na którym jest uruchomiony debuger.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) Opisuje listę identyfikatorów GUID.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Opisuje kontekst pamięci lub kontekst kodu.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Opisuje adres w debugowanym programie.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Reprezentuje jedną z wielu różnych rodzajów adresów.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Identyfikuje niestandardowy Podgląd lub wizualizator typu.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Opisuje właściwość debugowania, która z kolei opisuje obiekt o rodzaju hierarchicznej, który ma nazwę, typ i wartość.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Opisuje odwołanie.

- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Opisuje demontaż do środowiska IDE na potrzeby wyświetlania.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Opisuje wyjątek lub błąd czasu wykonywania zgłoszony przez debugowany program.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Opisuje zmienną lokalną, parametr lub inne pole.

- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Opisuje ramkę stosu.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) Opisuje tablicę unikatowych identyfikatorów dla dostępnych aparatów debugowania.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) Służy do ustawiania JustMyCode informacji dla modułu.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) Opisuje konkretną maszynę.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) Opisuje element tablicy w tablicy.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Opisuje adres pola klasy lub struktury.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) Opisuje adres zmiennej lokalnej w zakresie (zazwyczaj jest to funkcja lub metoda).

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) Opisuje adres metody klasy.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Opisuje parametr metody lub funkcji.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) Opisuje wartość zwracaną z metody lub funkcji.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Opisuje typ pola pobrane z metadanych.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Opisuje określony moduł (DLL, EXE lub Assembly).

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) Opisuje informacje o stanie dotyczące przeszukanych ścieżek wyszukiwania symboli.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) Opisuje adres macierzysty.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) Opisuje typ pola pochodzący z symbolu PDB.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) Opisuje stan punktu przerwania, który jest gotowy do powiązania z lokalizacją w kodzie.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Opisuje proces.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) Opisuje listę obiektów [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) reprezentujących węzły programu.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Zawiera opis procesów uruchomionych na komputerze.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Opisuje lokalizację wiersza i kolumny w danym tekście.

- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) Opisuje właściwości wątku.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Opisuje typ pola.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Opisuje adres fizyczny.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) Opisuje adres względem `this` wskaźnika ( `Me` w Visual Basic).

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h, sh. h lub EE. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Dokumentacja interfejsu API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
