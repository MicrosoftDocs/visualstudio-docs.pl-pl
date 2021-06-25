---
description: Ta funkcja aktualizuje listę plików dla określonego polecenia kontroli źródła i dostarcza stan kontroli źródła dla wszystkich danych plików.
title: SccPopulateList, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b386c576b48e14b6118f62d451c42ac20f048b45
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902348"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList, funkcja
Ta funkcja aktualizuje listę plików dla określonego polecenia kontroli źródła i dostarcza stan kontroli źródła dla wszystkich danych plików.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccPopulateList (
   LPVOID          pvContext,
   enum SCCCOMMAND nCommand,
   LONG            nFiles,
   LPCSTR*         lpFileNames,
   POPLISTFUNC     pfnPopulate,
   LPVOID          pvCallerData,
   LPLONG          lpStatus,
   LONG            fOptions
);
```

#### <a name="parameters"></a>Parametry
 pvContext

[in] Struktura kontekstu wtyczki kontroli źródła.

 nCommand

[in] Polecenie kontroli źródła, które zostanie zastosowane do wszystkich plików w `lpFileNames` tablicy (zobacz [Kod](../extensibility/command-code-enumerator.md) polecenia, aby uzyskać listę możliwych poleceń).

 nFiles

[in] Liczba plików w `lpFileNames` tablicy.

 lpFileNames

[in] Tablica nazw plików znanych w idee IDE.

 pfnPopulate

[in] Funkcja wywołania zwrotnego środowiska IDE do wywołania w celu dodawania i usuwania plików (zobacz [POPLISTFUNC,](../extensibility/poplistfunc.md) aby uzyskać szczegółowe informacje).

 pvCallerData

[in] Wartość, która ma zostać przekazana bez zmian do funkcji wywołania zwrotnego.

 lpStatus

[in, out] Tablica wtyczki kontroli źródła, która zwraca flagi stanu dla każdego pliku.

 Foptions

[in] Flagi poleceń (aby uzyskać szczegółowe informacje, zobacz sekcję "PopulateList flagi" [flagi Bitflags](../extensibility/bitflags-used-by-specific-commands.md) używane przez określone polecenia).

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła dla tej funkcji zwraca jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Powodzenie.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Ta funkcja sprawdza listę plików pod jego bieżącym stanem. Używa on funkcji `pfnPopulate` wywołania zwrotnego do powiadamiania wywołującego, gdy plik nie spełnia kryteriów dla `nCommand` . Jeśli na przykład polecenie to , a plik na liście nie zostanie wyewidencjonowany, wywołanie zwrotne zostanie użyte do `SCC_COMMAND_CHECKIN` poinformowania wywołującego. Czasami wtyczka kontroli źródła może znaleźć inne pliki, które mogą być częścią polecenia, i dodać je. Dzięki temu użytkownik może na przykład Visual Basic wyewidencjonowyć plik .bmp, który jest używany przez jego projekt, ale nie jest wyświetlany w Visual Basic projektu. Użytkownik wybiera polecenie **Get w** idee IDE. W idee zostanie wyświetlona lista wszystkich plików, które użytkownik może pobrać, ale zanim lista zostanie wyświetlona, funkcja zostanie wywołana, aby upewnić się, że lista do wyświetlenia jest `SccPopulateList` aktualne.

## <a name="example"></a>Przykład
 Ide tworzy listę plików, które użytkownik może pobrać. Zanim wyświetli tę listę, wywołuje funkcję , zapewniając wtyczce kontroli źródła możliwość dodawania i usuwania plików `SccPopulateList` z listy. Wtyczka modyfikuje listę przez wywołanie danej funkcji wywołania zwrotnego (zobacz [POPLISTFUNC,](../extensibility/poplistfunc.md) aby uzyskać więcej informacji).

 Wtyczka kontynuuje wywołanie funkcji , która dodaje i usuwa pliki do czasu jej zakończeniu, a następnie `pfnPopulate` wraca z `SccPopulateList` funkcji. Następnie idee mogą wyświetlać swoją listę. Tablica `lpStatus` reprezentuje wszystkie pliki z oryginalnej listy przekazanej przez ideę IDE. Wtyczka wypełnia stan wszystkich tych plików oprócz korzystania z funkcji wywołania zwrotnego.

> [!NOTE]
> Wtyczka kontroli kodu źródłowego zawsze ma możliwość natychmiastowego powrotu z tej funkcji, pozostawiając listę bez takiej możliwości. Jeśli wtyczka implementuje tę funkcję, może to wskazać, ustawiając bitflag możliwości w pierwszym wywołaniu funkcji `SCC_CAP_POPULATELIST` [SccInitialize.](../extensibility/sccinitialize-function.md) Domyślnie wtyczka powinna zawsze zakładać, że wszystkie przekazywane elementy są plikami. Jeśli jednak idee ustawią flagę w parametrze , wszystkie przekazywane elementy będą traktowane `SCC_PL_DIR` `fOptions` jako katalogi. Wtyczka powinna dodawać wszystkie pliki, które należą do katalogów. Ide nigdy nie będzie przekazywać różnych plików i katalogów.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Flagi bitowe używane przez określone polecenia ](../extensibility/bitflags-used-by-specific-commands.md)
- [Kod polecenia](../extensibility/command-code-enumerator.md)
