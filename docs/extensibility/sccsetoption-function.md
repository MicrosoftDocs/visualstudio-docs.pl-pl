---
title: Funkcja SccSetOption | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1adcbb47e9fce7037fe8942326e8836ade51e3eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700308"
---
# <a name="sccsetoption-function"></a>SccSetOption, funkcja
Ta funkcja ustawia opcje, które kontrolują zachowanie wtyczki formantu źródła.

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

[w] Struktura kontekstu wtyczki formantu źródła.

 nOpcja

[w] Opcja, która jest ustawiana.

 Dwval

[w] Ustawienia opcji.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Opcja została pomyślnie ustawiona.|
|SCC_I_SHARESUBPROJOK|Zwrócona, jeśli `nOption` była, `SCC_OPT_SHARESUBPROJ` a wtyczka kontroli źródła umożliwia IDE ustawienie folderu docelowego.|
|SCC_E_OPNOTSUPPORTED|Opcja ta nie została ustawiona i nie należy na niej polegać.|

## <a name="remarks"></a>Uwagi
 IDE wywołuje tę funkcję, aby kontrolować zachowanie wtyczki kontroli źródła. Pierwszy parametr `nOption`, wskazuje wartość, która jest ustawiana, `dwVal`podczas gdy drugi, wskazuje, co zrobić z tą wartością. Wtyczka przechowuje te informacje skojarzone z `pvContext``,` IDE więc IDE musi wywołać tę funkcję po wywołaniu [SccInitialize](../extensibility/sccinitialize-function.md) (ale niekoniecznie po każdym wywołaniu [SccOpenProject](../extensibility/sccopenproject-function.md)).

 Podsumowanie opcji i ich wartości:

|`nOption`|`dwValue`|Opis|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Włącza/wyłącza kolejkowanie zdarzeń w tle.|
|`SCC_OPT_USERDATA`|Dowolna wartość|Określa wartość użytkownika, która ma zostać przekazana do funkcji wywołania zwrotnego [OPTNAMECHANGEPFN.](../extensibility/optnamechangepfn.md)|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Wskazuje, czy IDE obecnie obsługuje anulowanie operacji.|
|`SCC_OPT_NAMECHANGEPFN`|Wskaźnik do funkcji wywołania zwrotnego [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)|Ustawia wskaźnik na funkcję wywołania zwrotnego zmiany nazwy.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Wskazuje, czy IDE umożliwia wyewidencjonowanie swoich plików ręcznie (za pośrednictwem interfejsu użytkownika kontroli źródła) lub czy muszą być wyewidencjonowane tylko za pośrednictwem wtyczki kontroli źródła.|
|`SCC_OPT_SHARESUBPROJ`|Nie dotyczy|Jeśli wtyczka formantu źródła umożliwia IDE określenie lokalnego folderu `SCC_I_SHARESUBPROJOK`projektu, wtyczka zwraca .|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 Jeśli `nOption` `SCC_OPT_EVENTQUEUE`tak, IDE wyłącza (lub ponownie włącza) przetwarzanie w tle. Na przykład podczas kompilacji IDE może poinstruować wtyczkę kontroli źródła, aby zatrzymać przetwarzanie na stanie bezczynności dowolnego rodzaju. Po kompilacji ponownie włączyć przetwarzanie w tle, aby utrzymać kolejkę zdarzeń wtyczki na bieżąco. Odpowiadająca `SCC_OPT_EVENTQUEUE` wartości `nOption`, istnieją dwie możliwe `dwVal`wartości dla `SCC_OPT_EQ_ENABLE` `SCC_OPT_EQ_DISABLE`, a mianowicie, i .

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 Jeśli wartość `nOption` jest `SCC_OPT_HASCANCELMODE`, IDE umożliwia użytkownikom anulowanie długich operacji. Ustawienie `dwVal` `SCC_OPT_HCM_NO` (domyślne) wskazuje, że IDE nie ma trybu anulowania. Wtyczka kontroli źródła musi oferować własny przycisk Anuluj, jeśli chce, aby użytkownik mógł anulować. `SCC_OPT_HCM_YES`wskazuje, że IDE zapewnia możliwość anulowania operacji, więc wtyczka SCC nie musi wyświetlać własnego przycisku Anuluj. Jeśli IDE `dwVal` ustawia `SCC_OPT_HCM_YES`się na , `SCC_MSG_STATUS` jest `DOCANCEL` przygotowany do `lpTextOutProc` odpowiedzi i wiadomości wysyłane do funkcji wywołania zwrotnego (patrz [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Jeśli IDE nie ustawia tej zmiennej, dodatek plug-in nie powinien wysyłać tych dwóch komunikatów.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 Jeśli nOption jest `SCC_OPT_NAMECHANGEPFN`ustawiona na , a zarówno wtyczka kontroli źródła, jak i IDE na to pozwalają, wtyczka może faktycznie zmienić nazwę lub przenieść plik podczas operacji kontroli źródła. Wskaźnik `dwVal` funkcji typu [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)zostanie ustawiony na wskaźnik funkcji . Podczas operacji kontroli źródła, wtyczka może wywołać tę funkcję, przekazując w trzech parametrach. Są to stara nazwa (z w pełni kwalifikowaną ścieżką) pliku, nowa nazwa (z w pełni kwalifikowaną ścieżką) tego pliku i wskaźnik do informacji, które mają znaczenie dla IDE. IDE wysyła w tym ostatnim `SccSetOption` `nOption` wskaźniku, wywołując z set to `SCC_OPT_USERDATA`, z `dwVal` wskazywaniem danych. Obsługa tej funkcji jest opcjonalna. Wtyczka VSSCI, która używa tej możliwości, musi zainicjować wskaźnik `NULL`funkcji i zmienne danych użytkownika do programu , i nie może wywoływać funkcji zmiany nazwy, chyba że została podana. Należy również przygotować się do utrzymania wartości, która została mu nadana `SccSetOption`lub do zmiany jej w odpowiedzi na nowe wezwanie do . Nie stanie się to w środku operacji polecenia kontroli źródła, ale może się zdarzyć między poleceniami.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 Jeśli nOption jest `SCC_OPT_SCCCHECKOUTONLY`ustawiona na , IDE wskazuje, że pliki w aktualnie otwartym projekcie nigdy nie powinny być wyewidencjonowane ręcznie za pośrednictwem interfejsu użytkownika systemu kontroli źródła. Zamiast tego pliki powinny być wyewidencjonowane tylko za pośrednictwem wtyczki kontroli źródła w obszarze ide kontroli. Jeśli `dwValue` jest `SCC_OPT_SCO_NO`ustawiona na , oznacza to, że pliki powinny być traktowane normalnie przez wtyczkę i mogą być wyewidencjonowane za pośrednictwem interfejsu użytkownika kontroli źródła. Jeśli `dwValue` jest `SCC_OPT_SCO_YES`ustawiona na , to tylko dodatek jest dozwolone do wyewidencjonowania plików i system kontroli źródła interfejsu użytkownika nie powinny być wywoływane. Jest to w sytuacjach, w których IDE może mieć "pseudo-files", które mają sens, aby sprawdzić tylko za pośrednictwem IDE.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 Jeśli`nOption` jest `SCC_OPT_SHARESUBPROJ`ustawiona na IDE jest testowanie, czy wtyczka kontroli źródła można użyć określonego folderu lokalnego podczas dodawania plików z formantu źródła. Wartość parametru `dwVal` nie ma znaczenia w tym przypadku. Jeśli dodatek umożliwia IDE określić lokalny folder docelowy, w którym pliki zostaną dodane z kontroli źródła, gdy wywoływana jest `SCC_I_SHARESUBPROJOK` [SccAddFromScc,](../extensibility/sccaddfromscc-function.md) wtyczka musi zwrócić, gdy `SccSetOption` funkcja jest wywoływana. IDE następnie używa `lplpFileNames` parametru `SccAddFromScc` funkcji do przekazania w folderze docelowym. Wtyczka używa tego folderu docelowego do umieszczania plików dodanych z kontrolki źródła. Jeśli dodatek nie powróci `SCC_I_SHARESUBPROJOK` po `SCC_OPT_SHARESUBPROJ` ustawieniu opcji, IDE zakłada, że dodatek jest w stanie dodawać pliki tylko w bieżącym folderze lokalnym.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
