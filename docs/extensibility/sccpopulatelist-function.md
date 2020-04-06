---
title: Funkcja SccPopulateList | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f518413adba1546bcff4f7cf2e62b4563cf1bcc7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700529"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList, funkcja
Ta funkcja aktualizuje listę plików dla określonego polecenia kontroli źródła i dostarcza stan kontroli źródła dla wszystkich podanych plików.

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

[w] Struktura kontekstu wtyczki formantu źródła.

 nKommand

[w] Polecenie kontroli źródła, które zostanie zastosowane do `lpFileNames` wszystkich plików w tablicy (zobacz [Kod polecenia,](../extensibility/command-code-enumerator.md) aby uzyskać listę możliwych poleceń).

 nFiles

[w] Liczba plików w `lpFileNames` tablicy.

 lpFileNames

[w] Tablica nazw plików znanych IDE.

 pfnPopuluj

[w] Funkcja wywołania zwrotnego IDE do wywołania, aby dodać i usunąć pliki (zobacz [POPLISTFUNC](../extensibility/poplistfunc.md) szczegóły).

 pvCallerData

[w] Wartość, która ma być przekazana bez zmian do funkcji wywołania zwrotnego.

 lpStatus

[w, na zewnątrz] Tablica dla wtyczki formantu źródła do zwracania flag stanu dla każdego pliku.

 Foptions

[w] Flagi poleceń (szczegółowe informacje można znaleźć w sekcji "Flaga Listy wypełnień" [w bitflagach używanych przez określone polecenia).](../extensibility/bitflags-used-by-specific-commands.md)

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Powodzenie.|
|SCC_E_NONSPECIFICERROR|Niespecyficzna awaria.|

## <a name="remarks"></a>Uwagi
 Ta funkcja sprawdza listę plików pod kątem jego bieżącego stanu. Używa funkcji `pfnPopulate` wywołania zwrotnego, aby powiadomić rozmówcę, gdy `nCommand`plik nie spełnia kryteriów dla . Na przykład jeśli polecenie `SCC_COMMAND_CHECKIN` jest i plik na liście nie jest wyewidencjonowany, następnie wywołania zwrotnego jest używany do informowania wywołującego. Od czasu do czasu wtyczka kontroli źródła może znaleźć inne pliki, które mogą być częścią polecenia i dodać je. Umożliwia to na przykład użytkownikowi języka Visual Basic wyewidencjonowanie pliku bmp, który jest używany przez jego projekt, ale nie pojawia się w pliku projektu języka Visual Basic. Użytkownik wybiera polecenie **Pobierz** w IDE. IDE wyświetli listę wszystkich plików, które uważa, że użytkownik może uzyskać, `SccPopulateList` ale przed wyświetleniem listy, funkcja jest wywoływana, aby upewnić się, że lista, która ma być wyświetlana jest aktualna.

## <a name="example"></a>Przykład
 IDE tworzy listę plików, które uważa, że użytkownik może uzyskać. Przed wyświetleniem tej listy `SccPopulateList` wywołuje funkcję, dając wtyczek kontroli źródła możliwość dodawania i usuwania plików z listy. Wtyczka modyfikuje listę, wywołując daną funkcję wywołania zwrotnego (więcej informacji można znaleźć w [funkcji POPLISTFUNC).](../extensibility/poplistfunc.md)

 Wtyczka kontynuuje wywoływanie `pfnPopulate` funkcji, która dodaje i usuwa pliki, dopóki nie zostanie `SccPopulateList` zakończona, a następnie powróci z funkcji. IDE można następnie wyświetlić jego listę. Tablica `lpStatus` reprezentuje wszystkie pliki na oryginalnej liście przekazywane przez IDE. Wtyczka wypełnia stan wszystkich tych plików oprócz korzystania z funkcji wywołania zwrotnego.

> [!NOTE]
> Wtyczka kontroli źródła zawsze ma możliwość po prostu powrócić natychmiast z tej funkcji, pozostawiając listę, jak to jest. Jeśli wtyczka implementuje tę funkcję, może to `SCC_CAP_POPULATELIST` wskazać, ustawiając możliwości bitflag w pierwszym wywołaniu [SccInitialize](../extensibility/sccinitialize-function.md). Domyślnie wtyczka powinna zawsze zakładać, że wszystkie elementy przekazywane są plikami. Jednak jeśli IDE ustawia `SCC_PL_DIR` flagę `fOptions` w parametrze, wszystkie elementy przekazywane w są uważane za katalogi. Wtyczka powinna dodać wszystkie pliki, które należą do katalogów. IDE nigdy nie przejdzie w mieszaninie plików i katalogów.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Flagi bitowe używane przez określone polecenia ](../extensibility/bitflags-used-by-specific-commands.md)
- [Kod polecenia](../extensibility/command-code-enumerator.md)
