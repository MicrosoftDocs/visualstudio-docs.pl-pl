---
title: SccSetOption Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 825aba3c77d4986d9187b147f90725eda4d6e5aa
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682612"
---
# <a name="sccsetoption-function"></a>SccSetOption, funkcja
Funkcja ta Ustawia opcje, które kontrolują zachowanie wtyczka do kontroli źródła.

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

[in] Struktura kontekście wtyczki kontroli źródła.

 nOption

[in] Opcja, która jest ustawiona.

 dwVal

[in] Ustawienia opcji.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Pomyślnie ustawiono opcję.|
|SCC_I_SHARESUBPROJOK|Zwracane, gdy `nOption` został `SCC_OPT_SHARESUBPROJ` i wtyczka do kontroli źródła umożliwia IDE ustawić folder docelowy.|
|SCC_E_OPNOTSUPPORTED|Opcja nie została ustawiona i nie należy polegać.|

## <a name="remarks"></a>Uwagi
 IDE wywołuje tę funkcję, aby kontrolować zachowanie wtyczka do kontroli źródła. Pierwszy parametr `nOption`, wskazuje wartość, która jest ustawiona, podczas gdy drugi, `dwVal`, wskazuje, co należy zrobić z daną wartością. Wtyczka przechowuje te informacje skojarzone z `pvContext``,` tak IDE, musisz wywołać tę funkcję po wywołaniu [SccInitialize](../extensibility/sccinitialize-function.md) (ale niekoniecznie po każdym wywołaniu [SccOpenProject](../extensibility/sccopenproject-function.md)).

 Podsumowanie opcji i ich wartości:

|`nOption`|`dwValue`|Opis|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Włącza/wyłącza tła, kolejkowanie zdarzeń.|
|`SCC_OPT_USERDATA`|Dowolne wartości|Określa wartość użytkownika, które zostaną przekazane do [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) funkcji wywołania zwrotnego.|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Wskazuje, czy IDE obecnie obsługuje anulowanie operacji.|
|`SCC_OPT_NAMECHANGEPFN`|Wskaźnik do [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) funkcji wywołania zwrotnego|Ustawia wskaźnik do funkcji wywołania zwrotnego zmiany nazwy.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Wskazuje, czy IDE umożliwia sprawdzanie poza jego pliki ręcznie (za pośrednictwem interfejsu użytkownika kontroli źródła), lub czy ich musi być wyewidencjonowany tylko za pośrednictwem wtyczka do kontroli źródła.|
|`SCC_OPT_SHARESUBPROJ`|Brak|Jeśli wtyczka do kontroli źródła umożliwia IDE określić folder lokalny projekt, zwraca wtyczki `SCC_I_SHARESUBPROJOK`.|

## <a name="sccopteventqueue"></a>SCC_OPT_EVENTQUEUE
 Jeśli `nOption` jest `SCC_OPT_EVENTQUEUE`, IDE jest wyłączenie (lub ponowne włączenie) przetwarzania w tle. Na przykład podczas kompilacji, IDE może wydać polecenie wtyczka do kontroli źródła Aby zatrzymać przetwarzanie na idle wszelkiego rodzaju. Po kompilacji będzie on ponownie włączyć przetwarzania w tle na bieżąco wtyczki do firmy kolejki zdarzeń. Odpowiadający `SCC_OPT_EVENTQUEUE` wartość `nOption`, istnieją dwie możliwe wartości `dwVal`, to znaczy, `SCC_OPT_EQ_ENABLE` i `SCC_OPT_EQ_DISABLE`.

## <a name="sccopthascancelmode"></a>SCC_OPT_HASCANCELMODE
 Jeśli wartość `nOption` jest `SCC_OPT_HASCANCELMODE`, IDE pozwala użytkownikom na anulowanie operacji długie. Ustawienie `dwVal` do `SCC_OPT_HCM_NO` (domyślnie) wskazuje, że środowisko IDE ma nie Anuluj trybu. Wtyczka do kontroli źródła muszą oferować swoje własne przycisk Anuluj, jeśli chce, aby użytkownik mógł anulować. `SCC_OPT_HCM_YES` Wskazuje, IDE zapewnia możliwości anulowania operacji, więc SCC wtyczka musi wyświetlać swój własny przycisk Anuluj. Jeśli ustawia IDE `dwVal` do `SCC_OPT_HCM_YES`, jest gotowa na `SCC_MSG_STATUS` i `DOCANCEL` komunikaty wysyłane do `lpTextOutProc` funkcji wywołania zwrotnego (zobacz [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Jeśli IDE nie ustawi tę zmienną, wtyczkę należy nie będą wysyłane tych dwóch komunikatów.

## <a name="sccoptnamechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 Jeśli ustawiono nOption `SCC_OPT_NAMECHANGEPFN`, a oba źródła pozwalają na to wtyczka do kontroli i środowiska IDE, wtyczka może faktycznie zmienić nazwy ani przenieść pliku podczas operacji kontroli źródła. `dwVal` Zostanie ustawiona do wskaźnika funkcji typu [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Podczas operacji kontroli źródła dodatek można wywołać tę funkcję, przekazując trzech parametrów. Są to stara nazwa (z w pełni kwalifikowaną ścieżką) pliku nową nazwę (z w pełni kwalifikowaną ścieżką) pliku i wskaźnik do informacji, które mają znaczenie dla środowiska IDE programu. IDE wysyła ten ostatni wskaźnik, wywołując `SccSetOption` z `nOption` równa `SCC_OPT_USERDATA`, za pomocą `dwVal` wskazujący danych. Obsługa tej funkcji jest opcjonalna. Wtyczki VSSCI — czy wykorzystuje tę możliwość musi zostać zainicjowany funkcji wskaźnika i użytkownika danych zmienne do `NULL`, i go nie mogą wywoływać funkcja zmiany nazwy, chyba że przekazania jeden. On również powinna być przygotowana do przechowywania wartości podano lub je zmienić w odpowiedzi na nowe wywołanie w celu `SccSetOption`. Nie będzie to miało miejsce w trakcie wykonywania operacji polecenia kontroli źródła, ale problem może wystąpić między poleceniami.

## <a name="sccoptscccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 Jeśli ustawiono nOption `SCC_OPT_SCCCHECKOUTONLY`, IDE wskazująca, że pliki w aktualnie otwartym projekcie powinno nigdy nie można wyewidencjonować ręcznie za pomocą interfejsu użytkownika systemu kontroli źródła. Zamiast tego pliki powinny być sprawdzane wyłącznie za pośrednictwem wtyczka do kontroli źródła pod kontrolą środowiska IDE. Jeśli `dwValue` ustawiono `SCC_OPT_SCO_NO`, oznacza, że pliki powinny być traktowane zwykle wtyczki i może zostać wyewidencjonowany za pośrednictwem interfejsu użytkownika do kontroli źródła. Jeśli `dwValue` ustawiono `SCC_OPT_SCO_YES`, wówczas tylko dodatek jest dozwolone systemowi wyewidencjonowywanie plików i nie powinna być wywoływana interfejsu użytkownika systemu kontroli źródła. Dotyczy to sytuacji, w którym IDE może być "pseudo-files", które mają sens w celu zapoznania się wyłącznie za pośrednictwem środowiska IDE.

## <a name="sccoptsharesubproj"></a>SCC_OPT_SHARESUBPROJ
 Jeśli`nOption` ustawiono `SCC_OPT_SHARESUBPROJ`, IDE jest sprawdzenie, czy wtyczka do kontroli źródła można użyć określonego folderu lokalnego, podczas dodawania plików z kontroli źródła. Wartość `dwVal` parametru nie ma znaczenia, w tym przypadku. Jeśli wtyczka umożliwia IDE określić folder lokalne miejsce docelowe, w której zostaną dodane pliki ze źródła decyduje o [SccAddFromScc](../extensibility/sccaddfromscc-function.md) nosi nazwę, a następnie wtyczka musi zwracać `SCC_I_SHARESUBPROJOK` podczas `SccSetOption` jest — funkcja wywoływana. Następnie używa IDE `lplpFileNames` parametru `SccAddFromScc` funkcję, aby przekazać w folderze docelowym. Wtyczka korzysta z tego folderu docelowego można umieścić pliki dodane z kontroli źródła. Jeśli wtyczka nie zwróci `SCC_I_SHARESUBPROJOK` podczas `SCC_OPT_SHARESUBPROJ` wyboru jest zaznaczone, IDE przyjęto założenie, że wtyczki jest w stanie dodać pliki tylko w bieżącym folderze lokalnym.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)