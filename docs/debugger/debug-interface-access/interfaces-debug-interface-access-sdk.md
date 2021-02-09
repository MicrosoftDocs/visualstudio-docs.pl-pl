---
title: Interfejsy (zestaw SDK dostępu do interfejsu debugowania) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 234bfa31c79fa2c9ef60afd29d655cfc6e585aed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853262"
---
# <a name="interfaces-debug-interface-access-sdk"></a>Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)
Metody są wyświetlane alfabetycznie w każdym interfejsie w spisie treści i na stronie interfejsu w kolejności tablic wirtualnych.

## <a name="in-this-section"></a>W tej sekcji

[IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)

Zapewnia kontrolę nad sposobem, w jaki DIA SDK oblicza wirtualne i względne adresy wirtualne dla obiektów debugowania.

[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)

Inicjuje dostęp do źródła symboli debugowania.

[IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)

Zapewnia dostęp do rekordów w strumieniu danych debugowania.

[IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)

Wylicza różne strumienie debugowania zawarte w źródle danych.

[IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

Wylicza różne elementy danych ramek zawarte w źródle danych.

[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

Wyliczyć różne wstrzyknięte źródła zawarte w źródle danych.

[IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

Wylicza różne numery wierszy zawarte w źródle danych.

[IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

Wylicza różne wkłady sekcji zawarte w źródle danych.

[IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

Wylicza różne segmenty zawarte w źródle danych.

[IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

Wylicza różne pliki źródłowe zawarte w źródle danych.

[IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)

Wylicza różne dostępne ramki stosu.

[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

Wylicza różne symbole zawarte w źródle danych.

[IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)

Wylicza według adresów różnych symboli zawartych w źródle danych.

[IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)

Wylicza różne tabele zawarte w źródle danych.

[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)

Uwidacznia szczegóły ramki stosu.

[IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)

Opisuje szczegóły lokalizacji podstawowej i przesunięcia pamięci modułu lub obrazu.

[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)

Uzyskuje dostęp do kodu źródłowego programu przechowywanego w źródle danych DIA.

[IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)

Uzyskuje dostęp do informacji opisujących proces mapowania z bloku bajtów tekstu obrazu do numeru wiersza pliku źródłowego.

[IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)

Odbiera wywołania zwrotne z DIA symbol lokalizowania procedury, dzięki czemu interfejs użytkownika może raportować postęp próby lokalizacji.

[IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)

Odbiera wywołania zwrotne z DIA symbol lokalizacji procedury, co pozwala na nakładanie ograniczeń w procesie lokalizowania.

[IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)

Umożliwia odczytywanie trwałych właściwości zestawu właściwości DIA.

[IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)

Umożliwia aplikacji klienckiej dostarczanie bajtów pliku wykonywalnego określonego przez położenie pliku.

[IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)

Umożliwia aplikacji klienckiej dostarczanie bajtów pliku wykonywalnego określonego przez względny adres wirtualny.

[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)

Pobiera dane opisujące udział sekcji, czyli ciągły blok pamięci, który tworzy obraz przez jednostka kompilacji.

[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)

Mapuje dane z sekcji Number na segmenty przestrzeni adresowej.

[IDiaSession](../../debugger/debug-interface-access/idiasession.md)

Zawiera kontekst zapytania dla symboli debugowania.

[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)

Reprezentuje plik źródłowy.

[IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)

Uwidacznia właściwości ramki stosu.

[IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)

Zapewnia metody do przeszukiwania stosu przy użyciu pliku PDB.

[IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)

Utrzymuje kontekst stosu między wywołaniami metody [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) .

[IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)

Ułatwia przechodzenie stosu przy użyciu pliku bazy danych debugowania programu (PDB).

[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)

Opisuje właściwości wystąpienia symbolu.

[IDiaTable](../../debugger/debug-interface-access/idiatable.md)

Wylicza tabelę źródła danych DIA.

## <a name="related-sections"></a>Sekcje pokrewne
[Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)

Opisuje wyliczenia i struktury używane przez różne interfejsy DIA SDK.

[Stałe (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)

Opisuje stałe dostępne w DIA SDK.

## <a name="see-also"></a>Zobacz też

- [Odwołanie](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)