---
title: Flagi bitowe używane przez określone polecenia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 47dd3b1c75ab7ff206714509a82449d744a02952
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333526"
---
# <a name="bitflags-used-by-specific-commands"></a>Flagi bitowe używane przez określone polecenia
Zachowanie wiele funkcji w interfejsie API wtyczki kontroli źródła można zmodyfikować, ustawiając jeden lub więcej bitów w postaci pojedynczej wartości. Te wartości są określane jako flag bitowych. Różne flagi bitowe używane przez interfejs API wtyczki kontroli źródła są szczegółowo opisane w tym miejscu, pogrupowane według funkcji, która korzysta z nich.

## <a name="checked-out-flag"></a>Wyewidencjonowano flagi
 Tę flagę można ustawić dla dowolnego [SccAdd](../extensibility/sccadd-function.md) lub [SccCheckin](../extensibility/scccheckin-function.md).

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Zachowaj plik wyewidencjonowany.|

## <a name="add-flags"></a>Dodawanie flag
 Te flagi są używane przez [SccAdd](../extensibility/sccadd-function.md).

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|Wtyczka do kontroli źródła oczekuje się, aby automatycznie wykrywać, czy plik jest tekstowe lub binarne.|
|`SCC_FILETYPE_TEXT`|0x01|Typ pliku jest tekst.|
|`SCC_FILETYPE_BINARY`|0x04|Typ pliku jest plikiem binarnym. **Uwaga:** `SCC_FILETYPE_TEXT` i `SCC_FILETYPE_BINARY` flagi są wzajemnie się wykluczają. Ustaw dokładnie jeden lub żadnego z tych celów.|
|`SCC_ADD_STORELATEST`|0x02|Store tylko najnowszą wersję (nie różnic).|

## <a name="diff-flags"></a>Flagi różnic
 [SccDiff](../extensibility/sccdiff-function.md) używa tych flag do definiowania zakresu operacji diff. `SCC_DIFF_QD_xxx` Flagi są wzajemnie się wykluczają. Jeśli jeden z nich jest określona, nie wizualną opinię jest podawana. W "szybkie diff" (głębokość kolejki), wtyczka nie określa, jak ten plik ma różne, tylko wtedy, gdy jest inny. Jeśli żadna z tych flag jest określony, odbywa się "visual diff"; szczegółowy plik różnice są obliczane i wyświetlane. Jeśli żądana głębokość kolejki nie jest obsługiwany, wtyczki przechodzi do następnego najlepsze. Na przykład jeśli IDE żądań sumy kontrolnej oraz wtyczki nie obsługuje tej wtyczki ma pełny spis treści sprawdź (nadal znacznie szybciej niż wyświetlacza wizualnego).

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Ignoruj różnice wielkości liter.|
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignoruj różnice odstępu. **Uwaga:**  `SCC_DIFF_IGNORECASE` i `SCC_DIFF_IGNORESPACE` flagi są opcjonalne flag bitowych.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|Głębokość kolejki przez porównywanie zawartości całego pliku.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|Głębokość kolejki według sumy kontrolnej.|
|`SCC_DIFF_QD_TIME`|0x0040|Głębokość kolejki przez sygnaturę daty i godziny pliku.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|Jest to maskę użytych do sprawdzenia wszystkie flagi bitowe głębokość kolejki. Nie powinny być przekazywane do funkcji; trzy flagi bitowe głębokość kolejki wzajemnie się wykluczają. Głębokość kolejki zawsze oznacza nie wyświetlania interfejsu użytkownika.|

## <a name="populatelist-flag"></a>Flaga PopulateList
 Ta flaga jest używana przez [SccPopulateList](../extensibility/sccpopulatelist-function.md) w `fOptions` parametru.

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|Środowisko IDE jest przekazanie katalogi, nie pliki.|

## <a name="populatedirlist-flags"></a>Flagi PopulateDirList
 Te flagi są używane przez [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) w `fOptions` parametru.

|Wartość opcji|Wartość|Opis|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Sprawdź tylko jeden poziom katalogów dla katalogów (jest to wartość domyślna).|
|SCC_PDL_RECURSIVE|0x0001|Rekursywnie sprawdzić wszystkie katalogi w ramach każdego danego katalogu.|
|SCC_PDL_INCLUDEFILES|0x0002|Nazwy załączonych plików w procesie badania.|

## <a name="openproject-flags"></a>Flagi OpenProject
 Te flagi są używane przez [SccOpenProject](../extensibility/sccopenproject-function.md) w `dwFlags` parametru.

|Wartość opcji|Wartość|Opis|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|Jeśli projekt nie istnieje w kontroli źródła, należy go utworzyć. Jeśli ta flaga nie jest ustawiona, Monituj użytkownika dla projektu, aby utworzyć (chyba że `SCC_OP_SILENTOPEN` określono flagę).|
|SCC_OP_SILENTOPEN|0x00000002L|Nie monituj użytkownika, aby utworzyć projekt; Zwróć `SCC_E_UNKNOWNPROJECT`.|

## <a name="get-flags"></a>Pobierz flagi
 Te flagi są używane przez [SccGet](../extensibility/sccget-function.md) i [SccCheckout](../extensibility/scccheckout-function.md).

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|Środowisko IDE jest przekazanie katalogi, nie pliki: Pobierz wszystkie pliki w katalogach.|
|`SCC_GET_RECURSIVE`|0x00000002L|Środowisko IDE jest przekazanie katalogi: Skorzystaj z tych katalogów i wszystkich jego podkatalogów.|

## <a name="noption-values"></a>wartości nOption
 Te flagi są używane przez [SccSetOption](../extensibility/sccsetoption-function.md) w `nOption` parametru.

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Ustaw stan kolejki zdarzeń.|
|`SCC_OPT_USERDATA`|0x00000002L|Określ dane użytkowników dla `SCC_OPT_NAMECHANGEPFN`.|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|IDE może obsługiwać anulowania.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Ustaw wywołanie zwrotne dla zmiany nazwy.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Wyłącz wyewidencjonowanie interfejsu użytkownika dodatku plug-in kontroli źródła i nie należy ustawiać katalogu roboczego.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Dodaj z systemu kontroli źródła, aby określić katalog roboczy. Spróbuj udostępnić do skojarzonego projektu, jeśli jest bezpośredni obiekt podrzędny.|

## <a name="dwval-bitflags"></a>Flagi bitowe dwVal
 Te flagi są używane przez [SccSetOption](../extensibility/sccsetoption-function.md) w `dwVal` parametru.

|Flaga|Wartość|Opis|Używane przez `nOption` wartość|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|Wstrzymuje działanie kolejki zdarzeń.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|Umożliwia rejestrowanie kolejki zdarzeń.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|(Ustawienie domyślne) Trybem nie Anuluj; dodatek typu plug-in, musisz podać w razie potrzeby.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|IDE obsługuje anulowanie.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|(Ustawienie domyślne) OK, aby zapoznaj się z poziomu interfejsu użytkownika dodatku typu plug-in; katalog roboczy jest ustawiony.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|Nie wtyczki wyewidencjonowania interfejsu użytkownika, nie katalogu roboczego.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>Zobacz także
- [Wtyczek kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)