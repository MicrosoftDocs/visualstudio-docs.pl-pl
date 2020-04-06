---
title: Bitflags używane przez określone polecenia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffa1fd8bf025d665977e87dc8b88da724ade5a8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740015"
---
# <a name="bitflags-used-by-specific-commands"></a>Bitflags używane przez określone polecenia
Zachowanie wielu funkcji w interfejsie API wtyczki kontroli źródła można zmodyfikować, ustawiając jeden lub więcej bitów w jednej wartości. Wartości te są znane jako bitflags. Różne bitflags używane przez interfejs API wtyczki kontroli źródła są szczegółowe tutaj, pogrupowane według funkcji, która ich używa.

## <a name="checked-out-flag"></a>Wyewidencjonowana flaga
 Tę flagę można ustawić dla [SccAdd](../extensibility/sccadd-function.md) lub [SccCheckin](../extensibility/scccheckin-function.md).

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Zachowaj plik wyewidencjonowany.|

## <a name="add-flags"></a>Dodawanie flag
 Flagi te są używane przez [SccAdd](../extensibility/sccadd-function.md).

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|Oczekuje się, że wtyczka formantu źródła automatycznie wykryje, czy plik jest tekstem czy plikiem binarnym.|
|`SCC_FILETYPE_TEXT`|0x01|Typ pliku to tekst.|
|`SCC_FILETYPE_BINARY`|0x04|Typ pliku jest binarny. **Uwaga:** `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` i flagi wzajemnie się wykluczają.   Ustaw dokładnie jeden lub żaden.|
|`SCC_ADD_STORELATEST`|0x02|Przechowuj tylko najnowszą wersję (bez delt).|

## <a name="diff-flags"></a>Flagi różnicowe
 [SccDiff](../extensibility/sccdiff-function.md) używa tych flag do definiowania zakresu operacji diff. Flagi `SCC_DIFF_QD_xxx` wzajemnie się wykluczają. Jeśli którykolwiek z nich jest określony, a następnie nie wizualne sprzężenie zwrotne ma być podane. W "quick diff" (QD) wtyczka nie określa, jak plik jest inny, tylko jeśli jest inny. Jeśli żadna z tych flag nie jest określona, "wizualny diff" jest wykonywana; szczegółowe różnice plików są obliczane i wyświetlane. Jeśli żądana QD nie jest obsługiwana, wtyczka przechodzi do następnego najlepszego. Na przykład jeśli IDE żąda sumy kontrolnej, a dodatek nie obsługuje go, wtyczka sprawdza pełną zawartość (nadal znacznie szybciej niż na wyświetlaczu wizualnym).

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Ignoruj różnice przypadków.|
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignoruj różnice odstępów. **Uwaga:**  Flagi `SCC_DIFF_IGNORECASE` `SCC_DIFF_IGNORESPACE` i są opcjonalne bitflags.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD, porównując całą zawartość pliku.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD przez sumę kontrolną.|
|`SCC_DIFF_QD_TIME`|0x0040|QD według daty/sygnatury czasowej pliku.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|Jest to maska służąca do sprawdzania wszystkich bitflagów QD. Nie należy go przepuszczać do funkcji; trzy bitflagi QD wzajemnie się wykluczają. QD zawsze oznacza brak wyświetlania interfejsu użytkownika.|

## <a name="populatelist-flag"></a>Flaga listy wypełnień
 Ta flaga jest używana przez [SccPopulateList](../extensibility/sccpopulatelist-function.md) w parametrze. `fOptions`

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|IDE przekazuje katalogi, a nie pliki.|

## <a name="populatedirlist-flags"></a>Flagi Listy WypełnićDirList
 Flagi te są używane przez [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) w parametrze. `fOptions`

|Wartość opcji|Wartość|Opis|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Sprawdź tylko jeden poziom katalogów dla katalogów (jest to wartość domyślna).|
|SCC_PDL_RECURSIVE|0x0001|Rekursyjnie zbadać wszystkie katalogi w każdym danym katalogu.|
|SCC_PDL_INCLUDEFILES|0x0002|Dołącz nazwy plików w procesie badania.|

## <a name="openproject-flags"></a>Flagi OpenProject
 Flagi te są używane przez [SccOpenProject](../extensibility/sccopenproject-function.md) w parametrze. `dwFlags`

|Wartość opcji|Wartość|Opis|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|Jeśli projekt nie istnieje w kontroli źródła, utwórz go. Jeśli ta flaga nie jest ustawiona, `SCC_OP_SILENTOPEN` monituj użytkownika o utworzenie projektu (chyba że określono flagę).|
|SCC_OP_SILENTOPEN|0x00000002L|Nie monituj użytkownika o utworzenie projektu; po `SCC_E_UNKNOWNPROJECT`prostu wróć .|

## <a name="get-flags"></a>Pobierz flagi
 Flagi te są używane przez [SccGet](../extensibility/sccget-function.md) i [SccCheckout](../extensibility/scccheckout-function.md).

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|IDE przekazuje katalogi, a nie pliki: Pobierz wszystkie pliki w tych katalogach.|
|`SCC_GET_RECURSIVE`|0x00000002L|IDE przekazuje katalogi: Pobierz te katalogi i wszystkie ich podkatalogi.|

## <a name="noption-values"></a>nOption wartości
 Flagi te są używane przez [SccSetOption](../extensibility/sccsetoption-function.md) w parametrze. `nOption`

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Ustaw stan kolejki zdarzeń.|
|`SCC_OPT_USERDATA`|0x00000002L|Określ dane `SCC_OPT_NAMECHANGEPFN`użytkownika dla .|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|IDE może obsłużyć cancel.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Ustaw wywołanie zwrotne dla zmian nazwy.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Wyłącz wyewidencjonowanie wyewidencjonowania wtyczek interfejsu użytkownika wtyczek sterowania źródłem i nie ustawiaj katalogu roboczego.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Dodaj z systemu kontroli źródła, aby określić katalog roboczy. Spróbuj udostępnić w skojarzonym projekcie, jeśli jest bezpośrednim elementem podrzędnym.|

## <a name="dwval-bitflags"></a>dwVal bitflags
 Flagi te są używane przez [SccSetOption](../extensibility/sccsetoption-function.md) w parametrze. `dwVal`

|Flaga|Wartość|Opis|Używane `nOption` przez wartość|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|Zawiesza aktywność kolejki zdarzeń.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|Umożliwia rejestrowanie kolejki zdarzeń.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|(Domyślnie) Nie ma trybu anulowania; w razie potrzeby musi dostarczyć wtyczkę.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|Dojścia IDE anuluj.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|(Domyślnie) OK, aby wyewidencjonować z interfejsu użytkownika wtyczki; katalog roboczy jest ustawiony.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|Brak wyewidencjonowania interfejsu użytkownika wtyczki, brak działającego katalogu.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
