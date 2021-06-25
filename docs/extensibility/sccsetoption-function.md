---
description: Ta funkcja ustawia opcje, które kontrolują zachowanie wtyczki kontroli źródła.
title: Funkcja SccSetOption | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 18e33cbb8dbee9b332456826ed33e46e4d2e76de
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904103"
---
# <a name="sccsetoption-function"></a>SccSetOption, funkcja
Ta funkcja ustawia opcje, które kontrolują zachowanie wtyczki kontroli źródła.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccSetOption(
   LPVOID pvContext,
   LONG   nOption,
   LONG   dwVal
);
```

#### <a name="parameters"></a>Parametry
 pvContext

[in] Struktura kontekstu wtyczki kontroli źródła.

 nOption (nOption)

[in] Ustawiana opcja.

 Dwval

[in] Ustawienia dla opcji.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła dla tej funkcji zwraca jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Opcja została pomyślnie ustawiona.|
|SCC_I_SHARESUBPROJOK|Zwracany, `nOption` jeśli `SCC_OPT_SHARESUBPROJ` był, a wtyczka kontroli źródła umożliwia ideom ustawianie folderu docelowego.|
|SCC_E_OPNOTSUPPORTED|Opcja nie została ustawiona i nie powinna być na nich polegana.|

## <a name="remarks"></a>Uwagi
 Ide wywołuje tę funkcję, aby kontrolować zachowanie wtyczki kontroli źródła. Pierwszy parametr, , wskazuje ustawianą wartość, a drugi , wskazuje, co należy zrobić `nOption` `dwVal` z wartością. Wtyczka przechowuje te informacje skojarzone z , więc idee muszą wywołać tę funkcję po wywołaniu `pvContext``,` [SccInitialize](../extensibility/sccinitialize-function.md) (ale niekoniecznie po każdym wywołaniu [SccOpenProject).](../extensibility/sccopenproject-function.md)

 Podsumowanie opcji i ich wartości:

|`nOption`|`dwValue`|Opis|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Włącza/wyłącza kolejkowanie zdarzeń w tle.|
|`SCC_OPT_USERDATA`|Dowolna wartość|Określa wartość użytkownika, która ma zostać przekazana do funkcji wywołania zwrotnego [OPTNAMECHANGEPFN.](../extensibility/optnamechangepfn.md)|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Wskazuje, czy ide aktualnie obsługuje anulowanie operacji.|
|`SCC_OPT_NAMECHANGEPFN`|Wskaźnik do funkcji [wywołania zwrotnego OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)|Ustawia wskaźnik na funkcję wywołania zwrotnego zmiany nazwy.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Wskazuje, czy idee zezwalają na ręczne wyewidencjonowanie plików (za pośrednictwem interfejsu użytkownika kontroli źródła) lub czy muszą być wyewidencjonowane tylko za pośrednictwem wtyczki kontroli źródła.|
|`SCC_OPT_SHARESUBPROJ`|Nie dotyczy|Jeśli wtyczka kontroli źródła umożliwia ideowi IDE określenie lokalnego folderu projektu, wtyczka zwraca wartość `SCC_I_SHARESUBPROJOK` .|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 Jeśli `nOption` to `SCC_OPT_EVENTQUEUE` , idee wyłącza (lub ponownie włączające) przetwarzanie w tle. Na przykład podczas kompilacji środowiska IDE może poinstruować wtyczkę kontroli źródła, aby zatrzymała przetwarzanie bezczynne dowolnego rodzaju. Po kompilacji ponownie włączy przetwarzanie w tle, aby kolejka zdarzeń wtyczki była zawsze aktualne. Odpowiadająca `SCC_OPT_EVENTQUEUE` wartości `nOption` , istnieją dwie możliwe wartości `dwVal` dla , a mianowicie i `SCC_OPT_EQ_ENABLE` `SCC_OPT_EQ_DISABLE` .

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 Jeśli wartość właściwości to `nOption` `SCC_OPT_HASCANCELMODE` , ide umożliwia użytkownikom anulowanie długich operacji. Ustawienie `dwVal` wartości `SCC_OPT_HCM_NO` (ustawienie domyślne) wskazuje, że w ide nie ma trybu anulowania. Wtyczka kontroli źródła musi oferować własny przycisk Anuluj, jeśli chce, aby użytkownik mógł anulować. `SCC_OPT_HCM_YES` wskazuje, że idee zapewniają możliwość anulowania operacji, więc wtyczka SCC nie musi wyświetlać własnego przycisku Anuluj. Jeśli idee mają ustawienie , jest ono przygotowane do odpowiadania na komunikaty i wysyłane do funkcji wywołania zwrotnego `dwVal` `SCC_OPT_HCM_YES` `SCC_MSG_STATUS` `DOCANCEL` `lpTextOutProc` (zobacz [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Jeśli w idee nie ustawiono tej zmiennej, wtyczka nie powinna wysyłać tych dwóch komunikatów.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 Jeśli nOption jest ustawiona na wartość , a zarówno wtyczka kontroli źródła, jak i idee na to zezwalają, wtyczka może w rzeczywistości zmienić nazwę lub przenieść plik podczas operacji kontroli `SCC_OPT_NAMECHANGEPFN` źródła. Parametr `dwVal` zostanie ustawiony na wskaźnik funkcji typu [OPTNAMECHANGEPFN.](../extensibility/optnamechangepfn.md) Podczas operacji kontroli źródła wtyczka może wywołać tę funkcję, przekazując trzy parametry. Są to stara nazwa (z w pełni kwalifikowaną ścieżką) pliku, nowa nazwa (z w pełni kwalifikowaną ścieżką) tego pliku i wskaźnik do informacji, które mają znaczenie dla środowiska IDE. Ide wysyła w tym ostatnim wskaźniku, wywołując obiekt z ustawionym na `SccSetOption` , `nOption` z `SCC_OPT_USERDATA` `dwVal` wskaźnikiem na dane. Obsługa tej funkcji jest opcjonalna. Wtyczka VSSCI, która używa tej możliwości, musi zainicjować wskaźnik funkcji i zmienne danych użytkownika do , i nie może wywołać funkcji zmiany nazwy, chyba że została `NULL` jej nadana. Powinna być również przygotowana do przechowywania podanej wartości lub zmiany jej w odpowiedzi na nowe wywołanie `SccSetOption` . Nie nastąpi to w trakcie operacji polecenia kontroli źródła, ale może się to zdarzyć między poleceniami.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 Jeśli nOption jest ustawiona na , ide wskazuje, że pliki w aktualnie otwartym projekcie nigdy nie powinny być wyewidencjonowane ręcznie za pomocą interfejsu użytkownika systemu `SCC_OPT_SCCCHECKOUTONLY` kontroli źródła. Zamiast tego pliki powinny być wyewidencjonowane tylko za pośrednictwem wtyczki kontroli źródła w ramach kontroli środowiska IDE. Jeśli ustawiono wartość , oznacza to, że pliki powinny być traktowane normalnie przez wtyczkę i mogą być wyewidencjonowane za pomocą interfejsu użytkownika `dwValue` `SCC_OPT_SCO_NO` kontroli źródła. Jeśli ustawiono wartość , wówczas tylko wtyczka może wyewidencjonać pliki, a interfejs użytkownika systemu kontroli źródła nie `dwValue` `SCC_OPT_SCO_YES` powinien być wywoływany. Dotyczy to sytuacji, w których ide może mieć "pseudo-pliki", które warto sprawdzać tylko za pośrednictwem środowiska IDE.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 Jeśli jest ustawiona na , ide testuje, czy wtyczka kontroli źródła może używać określonego folderu lokalnego podczas dodawania `nOption` `SCC_OPT_SHARESUBPROJ` plików z kontroli źródła. Wartość `dwVal` parametru nie ma znaczenia w tym przypadku. Jeśli wtyczka umożliwia ideowi IDE określenie lokalnego folderu docelowego, w którym pliki zostaną dodane z kontroli źródła po [wywołaniu SccAddFromScc,](../extensibility/sccaddfromscc-function.md) wtyczka musi zostać zwrócona, gdy zostanie wywołana `SCC_I_SHARESUBPROJOK` `SccSetOption` funkcja. Następnie ide używa `lplpFileNames` parametru funkcji `SccAddFromScc` do przekazania do folderu docelowego. Wtyczka używa tego folderu docelowego do miejsca plików dodanych z kontroli źródła. Jeśli wtyczka nie zostanie zwrócona, gdy opcja zostanie ustawiona, idee zakładają, że wtyczka może dodawać pliki tylko w bieżącym `SCC_I_SHARESUBPROJOK` `SCC_OPT_SHARESUBPROJ` folderze lokalnym.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
