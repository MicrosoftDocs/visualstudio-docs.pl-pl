---
title: Interfejsy (debugowanie zestaw SDK dostępu do interfejsu) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5eaf63ac57610e9ebde6703f0b5c15bf9607fdde
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774945"
---
# <a name="interfaces-debug-interface-access-sdk"></a>Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Metody są wymieniane alfabetycznie w ramach każdego interfejsu w tabeli treści i na stronie interfejsu w Vtable kolejności.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
 Zapewnia kontrolę nad jak DIA SDK oblicza względne i wirtualnego wirtualne adresy obiektów debugowania.  
  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
 Inicjuje dostęp do źródła symboli debugowania.  
  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)  
 Zapewnia dostęp do rekordów w strumieniu danych debugowania.  
  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)  
 Wylicza różnych strumieni debugowania zawartych w źródle danych.  
  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
 Wylicza różnych elementów danych ramek, znajdujących się w źródle danych.  
  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
 Wyliczanie różnych źródeł wprowadzonego znajdujących się w źródle danych.  
  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
 Wylicza różne numery wierszy zawartych w źródle danych.  
  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
 Wylicza różnych wkładów sekcji zawarte w źródle danych.  
  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
 Wylicza różnych segmentów znajdujących się w źródle danych.  
  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
 Wylicza różnych plików źródłowych znajdujących się w źródle danych.  
  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)  
 Wylicza różnych dostępnych ramek stosu.  
  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
 Wylicza różnych symboli znajdujących się w źródle danych.  
  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)  
 Wylicza przy użyciu adresu różnych symboli znajdujących się w źródle danych.  
  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)  
 Wylicza różnych tabel znajdujących się w źródle danych.  
  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
 Przedstawia szczegóły ramki stosu.  
  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)  
 Przedstawia szczegółowe informacje o podstawowej przesunięcia lokalizacji i pamięci, modułu lub obrazu.  
  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
 Uzyskuje dostęp do kodu źródłowego programu są przechowywane w źródle danych DIA.  
  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
 Uzyskuje dostęp do informacji w tym artykule opisano proces mapowanie bloku bajtów tekst obrazu na numer wiersza pliku źródłowego.  
  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
 Odbiera wywołania zwrotne z symboli DIA lokalizowanie procedury, umożliwiając w ten sposób interfejs użytkownika może raportować postęp lokalizacji.  
  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
 Odbiera wywołania zwrotne z symboli DIA lokalizowanie procedury, dzięki czemu ograniczenia nakładane na temat procesu lokalizowania.  
  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)  
 Pozwala na trwałe właściwości zestawu właściwości DIA odczytu.  
  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
 Umożliwia aplikacji klienta podać plik wykonywalny określony przez położenie pliku w bajtach.  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
 Umożliwia aplikacji klienckiej umożliwiają określanie wartości bajtów plik wykonywalny określony przez względny adres wirtualny.  
  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
 Pobiera dane opisujące wkład sekcji, czyli ciągłego bloku pamięci pochodzącego z danego obrazu compiland —.  
  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
 Mapuje dane z numer sekcji na segmenty przestrzeni adresowej.  
  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
 Udostępnia kontekst zapytania dla symboli debugowania.  
  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
 Reprezentuje plik źródłowy.  
  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)  
 Udostępnia właściwości ramki stosu.  
  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)  
 Udostępnia metody stosu zapoznaj się z przy użyciu pliku PDB.  
  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
 Utrzymuje kontekst stosu między wywołań [idiaframedata::EXECUTE —](../../debugger/debug-interface-access/idiaframedata-execute.md) metody.  
  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)  
 Ułatwia zalet stosu przy użyciu pliku bazy danych (PDB) programu debugowania.  
  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
 Opisuje właściwości instancji symbolu.  
  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
 Wylicza DIA tabeli źródła danych.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)  
 W tym artykule opisano, wyliczenia i struktury używane przez różne interfejsy DIA SDK.  
  
 [Stałe (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)  
 W tym artykule opisano dostępne w DIA SDK stałe.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)
