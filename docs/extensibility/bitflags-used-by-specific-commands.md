---
title: Bitflags używane przez określone polecenia | Microsoft Docs
description: Dowiedz się więcej o bitflags używanym przez interfejs API kontroli źródła, zorganizowane przez funkcję, która z nich korzysta.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6e018631e24cf7e678072b6b54183fd3c619dc4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890334"
---
# <a name="bitflags-used-by-specific-commands"></a>Bitflags używane przez określone polecenia
Zachowanie wielu funkcji w interfejsie API dodatku plug-in kontroli źródła może być modyfikowane przez ustawienie jednej lub kilku bitów w jednej wartości. Te wartości są znane jako bitflags. Różne bitflags używane przez interfejs API dodatku plug-in kontroli źródła są szczegółowo pogrupowane według funkcji, która z nich korzysta.

## <a name="checked-out-flag"></a>Flaga wyewidencjonowania
 Tę flagę można ustawić dla [SccAdd](../extensibility/sccadd-function.md) lub [SccCheckin](../extensibility/scccheckin-function.md).

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Pozostaw wyewidencjonowany plik.|

## <a name="add-flags"></a>Dodaj flagi
 Te flagi są używane przez [SccAdd](../extensibility/sccadd-function.md).

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|Wtyczka do kontroli źródła jest w stanie automatycznie wykryć, czy plik jest plikiem tekstowym czy binarnym.|
|`SCC_FILETYPE_TEXT`|0x01|Typ pliku to Text.|
|`SCC_FILETYPE_BINARY`|0x04|Typ pliku jest binarny. **Uwaga:** `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY`flagi i wykluczają się wzajemnie.   Ustaw dokładnie jeden lub nie.|
|`SCC_ADD_STORELATEST`|0x02|Tylko Najnowsza wersja magazynu (bez różnic).|

## <a name="diff-flags"></a>Flagi diff
 [SccDiff](../extensibility/sccdiff-function.md) używa tych flag do definiowania zakresu operacji diff. `SCC_DIFF_QD_xxx`Flagi wykluczają się wzajemnie. Jeśli jedna z nich jest określona, nie ma potrzeby wyświetlania opinii. W "szybkiej Diffie" (głębokość kolejki) wtyczka nie określa, w jaki sposób plik jest inny, tylko wtedy, gdy jest inny. Jeśli żadna z tych flag nie jest określona, zostanie wykonany "różnica wizualna". szczegółowe różnice plików są obliczane i wyświetlane. Jeśli żądana głębokość kolejki nie jest obsługiwana, wtyczka jest przenoszona do następnego najlepszego. Na przykład, jeśli IDE żąda sumy kontrolnej, a wtyczka nie obsługuje tego, wtyczka wykonuje sprawdzanie pełne zawartości (nadal znacznie szybciej niż w przypadku wyświetlania wizualnego).

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Ignoruj różnice wielkości liter.|
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignoruj różnice między znakami. **Uwaga:**  `SCC_DIFF_IGNORECASE` Flagi i `SCC_DIFF_IGNORESPACE` są opcjonalne bitflags.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|Głębokość kolejki przez porównanie całej zawartości pliku.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|Głębokość kolejki przez sumę kontrolną.|
|`SCC_DIFF_QD_TIME`|0x0040|Głębokość kolejki według sygnatury daty/godziny pliku.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|To jest maska służąca do sprawdzania wszystkich głębokość kolejki bitflags. Nie należy go przekazywać do funkcji; trzy głębokość kolejki bitflags wzajemnie się wykluczają. Głębokość kolejki zawsze oznacza brak wyświetlania interfejsu użytkownika.|

## <a name="populatelist-flag"></a>Flaga PopulateList
 Ta flaga jest używana przez [SccPopulateList](../extensibility/sccpopulatelist-function.md) w `fOptions` parametrze.

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001|IDE przekazuje katalogi, a nie pliki.|

## <a name="populatedirlist-flags"></a>Flagi PopulateDirList
 Te flagi są używane przez [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) w `fOptions` parametrze.

|Wartość opcji|Wartość|Opis|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Przejrzyj tylko jeden poziom katalogów dla katalogów (jest to ustawienie domyślne).|
|SCC_PDL_RECURSIVE|0x0001|Rekursywnie bada wszystkie katalogi w poszczególnych katalogach.|
|SCC_PDL_INCLUDEFILES|0x0002|Uwzględnij nazwy plików w procesie badania.|

## <a name="openproject-flags"></a>Flagi OpenProject
 Te flagi są używane przez [SccOpenProject](../extensibility/sccopenproject-function.md) w `dwFlags` parametrze.

|Wartość opcji|Wartość|Opis|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001|Jeśli projekt nie istnieje w kontroli źródła, utwórz go. Jeśli ta flaga nie jest ustawiona, Monituj użytkownika o utworzenie projektu (chyba że `SCC_OP_SILENTOPEN` flaga jest określona).|
|SCC_OP_SILENTOPEN|0x00000002L|Nie Monituj użytkownika o utworzenie projektu; po prostu zwracaj `SCC_E_UNKNOWNPROJECT` .|

## <a name="get-flags"></a>Pobierz flagi
 Te flagi są używane przez [SccGet](../extensibility/sccget-function.md) i [SccCheckout](../extensibility/scccheckout-function.md).

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001|IDE przekazuje katalogi, a nie pliki: Pobiera wszystkie pliki z tych katalogów.|
|`SCC_GET_RECURSIVE`|0x00000002L|IDE przekazuje katalogi: Pobierz te katalogi i wszystkie podkatalogi.|

## <a name="noption-values"></a>nOption wartości
 Te flagi są używane przez [SccSetOption](../extensibility/sccsetoption-function.md) w `nOption` parametrze.

|Flaga|Wartość|Opis|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001|Ustawianie stanu kolejki zdarzeń.|
|`SCC_OPT_USERDATA`|0x00000002L|Określ dane użytkownika `SCC_OPT_NAMECHANGEPFN` .|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|IDE może obsłużyć anulowanie.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Ustawianie wywołania zwrotnego dla zmian nazw.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Wyłącz wyewidencjonowywanie interfejsu użytkownika wtyczki kontroli źródła i nie ustawiaj katalogu roboczego.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Dodaj z systemu kontroli źródła, aby określić katalog roboczy. Spróbuj udostępnić do skojarzonego projektu, jeśli jest to bezpośredni element podrzędny.|

## <a name="dwval-bitflags"></a>dwVal bitflags
 Te flagi są używane przez [SccSetOption](../extensibility/sccsetoption-function.md) w `dwVal` parametrze.

|Flaga|Wartość|Opis|Używane przez `nOption` wartość|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00|Wstrzymuje działanie kolejki zdarzeń.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|Włącza rejestrowanie kolejki zdarzeń.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|Wartooć Nie ma trybu anulowania; wtyczka musi dostarczyć w razie potrzeby.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|Wartooć OK, aby wyewidencjonować z wtyczki interfejsu użytkownika; Katalog roboczy jest ustawiony.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|Brak wyewidencjonowania interfejsu użytkownika wtyczki, brak katalogu roboczego.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
