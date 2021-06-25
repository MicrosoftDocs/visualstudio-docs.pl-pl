---
title: Bitflags używane przez określone polecenia | Microsoft Docs
description: Dowiedz się więcej o bitflagach używanych przez interfejs API wtyczki kontroli kodu źródłowego zorganizowanych według funkcji, która ich używa.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: be5915d96b574336d7091239275a2aaef456a7f3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899370"
---
# <a name="bitflags-used-by-specific-commands"></a>Bitflags używane przez określone polecenia
Zachowanie wielu funkcji w interfejsie API wtyczki kontroli kodu źródłowego można zmodyfikować, ustawiając co najmniej jeden bit w pojedynczej wartości. Te wartości są nazywane bitflags. Różne bitflags używane przez interfejs API wtyczki kontroli kodu źródłowego są szczegółowo opisane tutaj, pogrupowane według funkcji, która z nich korzysta.

## <a name="checked-out-flag"></a>Flaga wyewidencjonowania
 Tę flagę można ustawić dla [SccAdd](../extensibility/sccadd-function.md) lub [SccCheckin](../extensibility/scccheckin-function.md).

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Zachowaj wyewidencjonowanie pliku.|

## <a name="add-flags"></a>Dodawanie flag
 Te flagi są używane przez [SccAdd](../extensibility/sccadd-function.md).

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|Wtyczka kontroli źródła ma automatycznie wykrywać, czy plik jest plikiem tekstowym, czy binarnym.|
|`SCC_FILETYPE_TEXT`|0x01|Typ pliku to tekst.|
|`SCC_FILETYPE_BINARY`|0x04|Typ pliku jest binarny. **Uwaga:** `SCC_FILETYPE_TEXT` Flagi `SCC_FILETYPE_BINARY` i wzajemnie się wykluczają.   Ustaw dokładnie jedną lub żadną z nich.|
|`SCC_ADD_STORELATEST`|0x02|Przechowuj tylko najnowszą wersję (bez różnic).|

## <a name="diff-flags"></a>Flagi różnic
 [SccDiff używa](../extensibility/sccdiff-function.md) tych flag do definiowania zakresu operacji różnicowej. Flagi `SCC_DIFF_QD_xxx` wzajemnie się wykluczają. Jeśli którykolwiek z nich jest określony, nie należy podawać żadnej wizualnej opinii. W przypadku "szybkiej różnicy" (QD) wtyczka nie określa różnic między plikami, tylko wtedy, gdy jest inny. Jeśli żadna z tych flag nie zostanie określona, zostanie wykonana "różnica wizualna". szczegółowe różnice w plikach są obliczane i wyświetlane. Jeśli żądany QD nie jest obsługiwany, wtyczka przechodzi do następnego najlepszego. Jeśli na przykład idee żądają sumy kontrolnej, a wtyczka jej nie obsługuje, wtyczka przeprowadza sprawdzanie pełnej zawartości (nadal znacznie szybciej niż wyświetlanie wizualizacji).

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Ignoruj różnice w przypadku.|
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignoruj różnice odstępów. **Uwaga:**  Flagi `SCC_DIFF_IGNORECASE` `SCC_DIFF_IGNORESPACE` i są opcjonalnymi flagami bitflags.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|Funkcja QD przez porównanie całej zawartości pliku.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD by checksum (QD według sumy kontrolnej).|
|`SCC_DIFF_QD_TIME`|0x0040|Funkcja QD według daty/sygnatury czasowej pliku.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|Jest to maska używana do sprawdzania wszystkich bitów QD. Nie należy go przekazywane do funkcji; Trzy bity QD bitflags wzajemnie się wykluczają. Funkcja QD zawsze oznacza brak wyświetlania interfejsu użytkownika.|

## <a name="populatelist-flag"></a>Flaga PopulateList
 Ta flaga jest używana przez [SccPopulateList](../extensibility/sccpopulatelist-function.md) w `fOptions` parametrze .

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|W idee są przekazujące katalogi, a nie pliki.|

## <a name="populatedirlist-flags"></a>Flagi PopulateDirList
 Te flagi są używane przez [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) w `fOptions` parametrze .

|Wartość opcji|Wartość|Opis|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Sprawdź tylko jeden poziom katalogów dla katalogów (jest to ustawienie domyślne).|
|SCC_PDL_RECURSIVE|0x0001|Rekursywnie sprawdź wszystkie katalogi w każdym danym katalogu.|
|SCC_PDL_INCLUDEFILES|0x0002|Uwzględnij nazwy plików w procesie badania.|

## <a name="openproject-flags"></a>Flagi OpenProject
 Te flagi są używane przez [SccOpenProject](../extensibility/sccopenproject-function.md) w `dwFlags` parametrze .

|Wartość opcji|Wartość|Opis|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|Jeśli projekt nie istnieje w kontroli źródła, utwórz go. Jeśli ta flaga nie jest ustawiona, monituj użytkownika o utworzenie projektu (chyba `SCC_OP_SILENTOPEN` że określono flagę).|
|SCC_OP_SILENTOPEN|0x00000002L|Nie monituj użytkownika o utworzenie projektu; po prostu zwróć `SCC_E_UNKNOWNPROJECT` .|

## <a name="get-flags"></a>Pobierz flagi
 Te flagi są używane przez [SccGet](../extensibility/sccget-function.md) i [SccCheckout](../extensibility/scccheckout-function.md).

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|Ide przekazujące katalogi, a nie pliki: pobierz wszystkie pliki w tych katalogach.|
|`SCC_GET_RECURSIVE`|0x00000002L|Ide przekazujące katalogi: pobierz te katalogi i wszystkie ich podkatalogi.|

## <a name="noption-values"></a>Wartości nOption
 Te flagi są używane przez [SccSetOption](../extensibility/sccsetoption-function.md) w `nOption` parametrze .

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Ustaw stan kolejki zdarzeń.|
|`SCC_OPT_USERDATA`|0x00000002L|Określ dane użytkownika dla `SCC_OPT_NAMECHANGEPFN` .|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|Ide może obsługiwać anulowanie.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Ustaw wywołanie zwrotne dla zmian nazw.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Wyłącz wyewidencjonowanie interfejsu użytkownika wtyczki kontroli źródła i nie ustawiaj katalogu roboczego.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Dodaj z systemu kontroli źródła, aby określić katalog roboczy. Spróbuj udostępnić w skojarzonym projekcie, jeśli jest to bezpośredni element potomny.|

## <a name="dwval-bitflags"></a>dwVal bitflags
 Te flagi są używane przez [SccSetOption](../extensibility/sccsetoption-function.md) w `dwVal` parametrze .

|Flaga|Wartość|Opis|Używane przez `nOption` wartość|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|Wstrzymuje działanie kolejki zdarzeń.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|Włącza rejestrowanie kolejki zdarzeń.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|(Ustawienie domyślne) Nie ma trybu anulowania; Wtyczka musi być dostarczana w razie potrzeby.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|Ide obsługuje anulowanie.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|(Ustawienie domyślne) Ok, aby wyewidencjić z interfejsu użytkownika wtyczki; ustawiono katalog roboczy.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|Brak wyewidencjonowania interfejsu użytkownika wtyczki, brak katalogu roboczego.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
