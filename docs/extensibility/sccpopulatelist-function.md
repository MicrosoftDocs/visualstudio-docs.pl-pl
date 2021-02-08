---
title: Funkcja SccPopulateList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2deb30b606de686269e095fffe369a7d56adb453
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836933"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList, funkcja
Ta funkcja aktualizuje listę plików dla określonego polecenia kontroli źródła i udostępnia stan kontroli źródła na wszystkich danych plikach.

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

podczas Struktura kontekstu wtyczki kontroli źródła.

 Nwykonywane polecenie

podczas Polecenie kontroli źródła, które zostanie zastosowane do wszystkich plików w `lpFileNames` tablicy (zobacz [kod polecenia](../extensibility/command-code-enumerator.md) , aby wyświetlić listę możliwych poleceń).

 nFiles

podczas Liczba plików w `lpFileNames` tablicy.

 lpFileNames

podczas Tablica nazw plików znanych IDE.

 pfnPopulate

podczas Funkcja wywołania zwrotnego IDE do wywołania dodawania i usuwania plików (zobacz [POPLISTFUNC](../extensibility/poplistfunc.md) , aby uzyskać szczegółowe informacje).

 pvCallerData

podczas Wartość, która ma zostać przeniesiona bez zmian do funkcji wywołania zwrotnego.

 lpStatus

[in. out] Tablica dla wtyczki kontroli źródła w celu zwrócenia flag stanu dla każdego pliku.

 fOptions

podczas Flagi poleceń (zobacz sekcję "Flaga PopulateList" w [Bitflags używane przez określone polecenia,](../extensibility/bitflags-used-by-specific-commands.md) Aby uzyskać szczegółowe informacje).

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Powodzenie.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Ta funkcja bada listę plików w bieżącym stanie. Używa `pfnPopulate` funkcji wywołania zwrotnego do powiadomienia obiektu wywołującego, gdy plik jest niezgodny z kryteriami dla `nCommand` . Na przykład jeśli polecenie jest, `SCC_COMMAND_CHECKIN` a plik na liście nie jest wyewidencjonowany, wywołanie zwrotne jest używane do informowania obiektu wywołującego. Czasami wtyczka do kontroli źródła może znaleźć inne pliki, które mogą być częścią polecenia i dodać je. Pozwala to na przykład Visual Basic użytkownikowi na wyewidencjonowanie pliku BMP, który jest używany przez jego projekt, ale nie jest wyświetlany w Visual Basic pliku projektu. Użytkownik wybiera polecenie **Get** w IDE. W środowisku IDE zostanie wyświetlona lista wszystkich plików, które uzna, że użytkownik może uzyskać, ale przed wyświetleniem listy `SccPopulateList` Funkcja jest wywoływana, aby upewnić się, że lista do wyświetlenia jest aktualna.

## <a name="example"></a>Przykład
 Środowisko IDE tworzy listę plików, które mogą zostać pobrane przez użytkownika. Zanim zostanie wyświetlona ta lista, wywołuje `SccPopulateList` funkcję, zapewniając wtyczkę kontroli źródła możliwość dodawania i usuwania plików z listy. Wtyczka modyfikuje listę, wywołując daną funkcję wywołania zwrotnego (zobacz [POPLISTFUNC](../extensibility/poplistfunc.md) , aby uzyskać więcej informacji).

 Wtyczka kontynuuje wywoływanie `pfnPopulate` funkcji, która dodaje i usuwa pliki, dopóki nie zostanie zakończona, a następnie zwraca z `SccPopulateList` funkcji. IDE może wyświetlić listę. `lpStatus`Tablica reprezentuje wszystkie pliki z oryginalnej listy przekazaną przez IDE. Wtyczka wypełnia stan wszystkich tych plików oprócz używania funkcji wywołania zwrotnego.

> [!NOTE]
> Wtyczka do kontroli źródła zawsze ma opcję natychmiastowego zwrócenia od tej funkcji, pozostawiając listę w takiej postaci. Jeśli wtyczka implementuje tę funkcję, może to wskazywać, ustawiając `SCC_CAP_POPULATELIST` bitflag możliwości w pierwszym wywołaniu [SccInitialize](../extensibility/sccinitialize-function.md). Domyślnie wtyczka powinna założyć, że wszystkie elementy, które są przesyłane, są plikami. Jeśli jednak IDE ustawi `SCC_PL_DIR` flagę w `fOptions` parametrze, wszystkie elementy, które są przesyłane, są traktowane jako katalogi. Wtyczka powinna dodać wszystkie pliki należące do katalogów. IDE nigdy nie przejdzie do kombinacji plików i katalogów.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Flagi bitowe używane przez określone polecenia ](../extensibility/bitflags-used-by-specific-commands.md)
- [Kod polecenia](../extensibility/command-code-enumerator.md)
