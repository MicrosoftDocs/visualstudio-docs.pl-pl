---
title: Funkcja SccPopulateList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a2cfdf5a617352d7ba0c2db00e7705343f1eb5e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720874"
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

podczas Polecenie kontroli źródła, które zostanie zastosowane do wszystkich plików w tablicy `lpFileNames` (zobacz [kod polecenia](../extensibility/command-code-enumerator.md) , aby wyświetlić listę możliwych poleceń).

 nFiles

podczas Liczba plików w tablicy `lpFileNames`.

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
|SCC_OK|Prawnego.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Ta funkcja bada listę plików w bieżącym stanie. Używa funkcji wywołania zwrotnego `pfnPopulate` do powiadomienia obiektu wywołującego, gdy plik jest niezgodny z kryteriami `nCommand`. Na przykład jeśli polecenie jest `SCC_COMMAND_CHECKIN`, a plik na liście nie zostanie wyewidencjonowany, wywołanie zwrotne zostanie użyte do poinformowania obiektu wywołującego. Czasami wtyczka do kontroli źródła może znaleźć inne pliki, które mogą być częścią polecenia i dodać je. Pozwala to na przykład Visual Basic użytkownikowi na wyewidencjonowanie pliku BMP, który jest używany przez jego projekt, ale nie jest wyświetlany w Visual Basic pliku projektu. Użytkownik wybiera polecenie **Get** w IDE. W środowisku IDE zostanie wyświetlona lista wszystkich plików, które uzna, że użytkownik może uzyskać, ale przed wyświetleniem listy zostanie wywołana funkcja `SccPopulateList`, aby upewnić się, że lista do wyświetlenia jest aktualna.

## <a name="example"></a>Przykład
 Środowisko IDE tworzy listę plików, które mogą zostać pobrane przez użytkownika. Przed wyświetleniem tej listy wywołuje funkcję `SccPopulateList`, dając do wtyczki kontroli źródła możliwość dodawania i usuwania plików z listy. Wtyczka modyfikuje listę, wywołując daną funkcję wywołania zwrotnego (zobacz [POPLISTFUNC](../extensibility/poplistfunc.md) , aby uzyskać więcej informacji).

 Wtyczka kontynuuje wywoływanie funkcji `pfnPopulate`, która dodaje i usuwa pliki, dopóki nie zostanie zakończona, a następnie zwraca z funkcji `SccPopulateList`. IDE może wyświetlić listę. Tablica `lpStatus` reprezentuje wszystkie pliki z oryginalnej listy przekazaną przez IDE. Wtyczka wypełnia stan wszystkich tych plików oprócz używania funkcji wywołania zwrotnego.

> [!NOTE]
> Wtyczka do kontroli źródła zawsze ma opcję natychmiastowego zwrócenia od tej funkcji, pozostawiając listę w takiej postaci. Jeśli wtyczka implementuje tę funkcję, może to wskazywać, ustawiając `SCC_CAP_POPULATELIST` możliwości bitflag w pierwszym wywołaniu [SccInitialize](../extensibility/sccinitialize-function.md). Domyślnie wtyczka powinna założyć, że wszystkie elementy, które są przesyłane, są plikami. Jeśli jednak IDE ustawi flagę `SCC_PL_DIR` w parametrze `fOptions`, wszystkie elementy, które są przesyłane, będą traktowane jako katalogi. Wtyczka powinna dodać wszystkie pliki należące do katalogów. IDE nigdy nie przejdzie do kombinacji plików i katalogów.

## <a name="see-also"></a>Zobacz także
- [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Flagi bitowe używane przez określone polecenia ](../extensibility/bitflags-used-by-specific-commands.md)
- [Kod polecenia](../extensibility/command-code-enumerator.md)