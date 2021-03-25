---
description: Ta funkcja ustawia opcje kontrolujące zachowanie wtyczki kontroli źródła.
title: Funkcja SccSetOption | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 031de256b231bbd95e7535af80448db5140cba7e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090151"
---
# <a name="sccsetoption-function"></a>SccSetOption, funkcja
Ta funkcja ustawia opcje kontrolujące zachowanie wtyczki kontroli źródła.

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

podczas Struktura kontekstu wtyczki kontroli źródła.

 nOption

podczas Opcja, która jest ustawiana.

 dwVal

podczas Ustawienia dla opcji.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Opcja została pomyślnie ustawiona.|
|SCC_I_SHARESUBPROJOK|Zwracany, jeśli `nOption` był `SCC_OPT_SHARESUBPROJ` i wtyczka do kontroli źródła umożliwia IDE Ustawianie folderu docelowego.|
|SCC_E_OPNOTSUPPORTED|Opcja nie została ustawiona i nie powinna być oparta na.|

## <a name="remarks"></a>Uwagi
 IDE wywołuje tę funkcję, aby kontrolować zachowanie wtyczki kontroli źródła. Pierwszy parametr, `nOption` , wskazuje wartość, która jest ustawiana, a drugi, wskazuje, `dwVal` co należy zrobić z tą wartością. Wtyczka przechowuje te informacje skojarzone z `pvContext``,` , dlatego IDE musi wywołać tę funkcję po wywołaniu [SccInitialize](../extensibility/sccinitialize-function.md) (ale niekoniecznie po każdym wywołaniu [SccOpenProject](../extensibility/sccopenproject-function.md)).

 Podsumowanie opcji i ich wartości:

|`nOption`|`dwValue`|Opis|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Włącza/wyłącza kolejkowanie zdarzeń w tle.|
|`SCC_OPT_USERDATA`|Arbitralna wartość|Określa wartość użytkownika, która ma zostać przeniesiona do funkcji wywołania zwrotnego [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) .|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Wskazuje, czy IDE obsługuje obecnie anulowanie operacji.|
|`SCC_OPT_NAMECHANGEPFN`|Wskaźnik do funkcji wywołania zwrotnego [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)|Ustawia wskaźnik na funkcję wywołania zwrotnego zmiany nazwy.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Wskazuje, czy IDE umożliwia ręczne wyewidencjonowywanie plików (za pomocą interfejsu użytkownika kontroli źródła) lub czy muszą one być wyewidencjonowane tylko za pomocą wtyczki kontroli źródła.|
|`SCC_OPT_SHARESUBPROJ`|Nie dotyczy|Jeśli wtyczka do kontroli źródła umożliwia środowisku IDE Określanie lokalnego folderu projektu, wtyczka jest zwracana `SCC_I_SHARESUBPROJOK` .|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 Jeśli `nOption` tak `SCC_OPT_EVENTQUEUE` , IDE wyłącza przetwarzanie w tle (lub ponowne Włączanie). Na przykład podczas kompilowania środowisko IDE może nakazać wtyczkę kontroli źródła, aby zatrzymać bezczynne przetwarzanie dowolnego rodzaju. Po kompilacji ponownie Włącz przetwarzanie w tle, aby zapewnić aktualność kolejki zdarzeń wtyczki. Odpowiadające `SCC_OPT_EVENTQUEUE` wartości `nOption` , są dostępne dwie wartości dla `dwVal` , mianowicie `SCC_OPT_EQ_ENABLE` i `SCC_OPT_EQ_DISABLE` .

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 Jeśli wartość `nOption` jest równa `SCC_OPT_HASCANCELMODE` , IDE umożliwia użytkownikom anulowanie długotrwałych operacji. Ustawienie `dwVal` `SCC_OPT_HCM_NO` (domyślnie) wskazuje, że IDE nie ma trybu anulowania. Wtyczka do kontroli źródła musi oferować swój własny przycisk Anuluj, jeśli chce, aby użytkownik mógł je anulować. `SCC_OPT_HCM_YES` wskazuje, że IDE zapewnia możliwość anulowania operacji, więc wtyczka SCC nie musi wyświetlać własnego przycisku Anuluj. Jeśli IDE ustawia `dwVal` na `SCC_OPT_HCM_YES` , jest przygotowana do odpowiadania `SCC_MSG_STATUS` i `DOCANCEL` komunikatów wysyłanych do `lpTextOutProc` funkcji wywołania zwrotnego (zobacz [lpTextOutProc](../extensibility/lptextoutproc.md)). Jeśli IDE nie ustawi tej zmiennej, wtyczka nie powinna wysyłać tych dwóch komunikatów.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 Jeśli nOption jest ustawiona na `SCC_OPT_NAMECHANGEPFN` , a zarówno Wtyczka kontroli źródła, jak i IDE zezwalają na to, wtyczka może faktycznie zmienić nazwę lub przenieść plik podczas operacji kontroli źródła. `dwVal`Zostanie ustawiony wskaźnik funkcji typu [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Podczas operacji kontroli źródła wtyczka może wywołać tę funkcję, przekazując trzy parametry. Są to stare nazwy (z w pełni kwalifikowaną ścieżką) pliku, Nowa nazwa (z w pełni kwalifikowaną ścieżką) tego pliku oraz wskaźnik do informacji, które mają znaczenie dla środowiska IDE. IDE wysyła w tym ostatnim wskaźniku, wywołując `SccSetOption` z `nOption` ustawionym na `SCC_OPT_USERDATA` , `dwVal` wskazując na dane. Obsługa tej funkcji jest opcjonalna. Wtyczka VSSCI, która korzysta z tej możliwości, musi inicjować swój wskaźnik funkcji i zmienne danych użytkownika do `NULL` i nie może wywołać funkcji zmiany nazwy, chyba że została określona. Należy również przygotować się do przechowywania wartości, którą podano, lub zmiany w odpowiedzi na nowe wywołanie `SccSetOption` . Nie będzie to miało miejsce w trakcie operacji polecenia kontroli źródła, ale może się zdarzyć między poleceniami.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 Jeśli nOption jest ustawiona na `SCC_OPT_SCCCHECKOUTONLY` , IDE wskazuje, że pliki w aktualnie otwartym projekcie nigdy nie powinny być wyewidencjonowane ręcznie za pomocą interfejsu użytkownika systemu kontroli źródła. Zamiast tego pliki powinny być wyewidencjonowywane tylko za pomocą wtyczki kontroli źródła w obszarze kontrolki IDE. Jeśli `dwValue` jest ustawiona na `SCC_OPT_SCO_NO` , oznacza to, że pliki powinny być przetwarzane zwykle przez wtyczkę i mogą być wyewidencjonowane za pośrednictwem interfejsu użytkownika kontroli źródła. Jeśli `dwValue` jest ustawiona na `SCC_OPT_SCO_YES` , wówczas tylko wtyczka może wyewidencjonować pliki, a interfejs użytkownika systemu kontroli źródła nie powinien być wywoływany. Dotyczy to sytuacji, w których środowisko IDE może mieć "pseudo pliki", co ma sens do wyewidencjonowania tylko za pomocą IDE.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 Jeśli `nOption` jest ustawiona na `SCC_OPT_SHARESUBPROJ` , IDE testuje, czy wtyczka do kontroli źródła może używać określonego folderu lokalnego podczas dodawania plików z kontroli źródła. Wartość `dwVal` parametru nie ma znaczenia w tym przypadku. Jeśli wtyczka umożliwia środowisku IDE określenie lokalnego folderu docelowego, do którego pliki zostaną dodane z kontroli źródła po wywołaniu [SccAddFromScc](../extensibility/sccaddfromscc-function.md) , wtyczka musi zwrócić, `SCC_I_SHARESUBPROJOK` gdy `SccSetOption` wywoływana jest funkcja. IDE następnie używa `lplpFileNames` parametru `SccAddFromScc` funkcji do przekazania do folderu docelowego. Wtyczka używa tego folderu docelowego do umieszczania plików dodanych z kontroli źródła. Jeśli wtyczka nie zwraca `SCC_I_SHARESUBPROJOK` `SCC_OPT_SHARESUBPROJ` , gdy opcja jest ustawiona, IDE zakłada, że wtyczka może dodawać pliki tylko w bieżącym folderze lokalnym.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
