---
title: Funkcja SccGet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 50281ffdd233debd3c10672868e9debd4b1f395f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965216"
---
# <a name="sccget-function"></a>SccGet, funkcja
Ta funkcja pobiera kopię co najmniej jednego pliku do przeglądania i kompilowania, ale nie do edycji. W większości systemów pliki są oznaczone jako tylko do odczytu.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccGet(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametry
 pvContext

podczas Struktura kontekstu wtyczki kontroli źródła.

 Właściwość

podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.

 nFiles

podczas Liczba plików określona w `lpFileNames` tablicy.

 lpFileNames

podczas Tablica w pełni kwalifikowanych nazw plików do pobrania.

 fOptions

podczas Flagi poleceń ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 pvOptions

podczas Opcje dotyczące wtyczki kontroli źródła.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Powodzenie operacji pobierania.|
|SCC_E_FILENOTCONTROLLED|Plik nie znajduje się pod kontrolą źródła.|
|SCC_E_OPNOTSUPPORTED|System kontroli źródła nie obsługuje tej operacji.|
|SCC_E_FILEISCHECKEDOUT|Nie można pobrać pliku, który obecnie został wyewidencjonowany przez użytkownika.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zalecana jest ponowna próba.|
|SCC_E_NOSPECIFIEDVERSION|Określono nieprawidłową wersję lub datę/godzinę.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd; plik nie został zsynchronizowany.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie ma autoryzacji do wykonania tej operacji.|

## <a name="remarks"></a>Uwagi
 Ta funkcja jest wywoływana z liczbą i tablicą nazw plików do pobrania. Jeśli IDE przeszedł flagę `SCC_GET_ALL` , oznacza to, że elementy w `lpFileNames` nie są plikami, ale katalogami i że wszystkie pliki w ramach kontroli źródła w danym katalogu mają być pobierane.

 `SCC_GET_ALL`Flaga może być łączona z `SCC_GET_RECURSIVE` flagą w celu pobrania wszystkich plików z danego katalogu i wszystkich podkatalogów.

> [!NOTE]
> `SCC_GET_RECURSIVE` nigdy nie powinno być przesyłane bez `SCC_GET_ALL` . Należy również pamiętać, że jeśli katalogi *C:\a* i *C:\A\B* są przesyłane do cyklicznego Get, *C:\A\B* i wszystkie jego podkatalogi zostaną rzeczywiście pobrane dwa razy. Jest to odpowiedzialność za środowisko IDE — a nie dla wtyczki kontroli źródła — aby upewnić się, że duplikaty, takie jak te, są przechowywane w tablicy.

 Na koniec, nawet jeśli wtyczka do kontroli źródła określiła `SCC_CAP_GET_NOUI` flagę inicjowania, wskazując, że nie ma interfejsu użytkownika dla polecenia Get, ta funkcja może być nadal wywoływana przez IDE w celu pobierania plików. Flaga po prostu oznacza, że IDE nie wyświetla elementu menu Pobierz i nie oczekuje, że wtyczka nie udostępnia żadnego interfejsu użytkownika.

## <a name="rename-files-and-sccget"></a>Zmień nazwy plików i SccGet
 Sytuacja: użytkownik sprawdza plik, na przykład *a.txt*, i modyfikuje go. Aby można było zaewidencjonować *a.txt* , drugi użytkownik zmienia nazwę *a.txt* do *b.txt* w bazie danych kontroli źródła, wyewidencjonuje *b.txt*, wprowadza modyfikacje pliku i sprawdza plik w. Pierwszy użytkownik chce, aby zmiany wprowadzone przez drugiego użytkownika zostały zmienione przez pierwszego użytkownika, a jego lokalna wersja *a.txt* pliku *b.txt* i pobiera plik. Jednak lokalna pamięć podręczna, która zachowuje śledzenie numerów wersji, nadal uważa, że pierwsza wersja *a.txt* jest przechowywana lokalnie i dlatego kontrola źródła nie może rozpoznać różnic.

 Istnieją dwa sposoby rozwiązania tej sytuacji, w której lokalna pamięć podręczna wersji kontroli źródła nie jest zsynchronizowana z bazą danych kontroli źródła:

1. Nie Zezwalaj na zmianę nazwy pliku w bazie danych kontroli źródła, który jest obecnie wyewidencjonowany.

2. Wykonaj odpowiednik "Usuń stare", a następnie "Dodaj nowe". Poniższy algorytm jest jednym ze sposobów, aby to osiągnąć.

    1. Wywołaj funkcję [SccQueryChanges](../extensibility/sccquerychanges-function.md) , aby dowiedzieć się więcej o zmianie nazwy *a.txt* na *b.txt* w bazie danych kontroli źródła.

    2. Zmień nazwę *a.txt* lokalnego na *b.txt*.

    3. Wywołaj `SccGet` funkcję dla obu *a.txt* i *b.txt*.

    4. Ponieważ *a.txt* nie istnieje w bazie danych kontroli źródła, w lokalnej pamięci podręcznej wersji zostanie przeczyszczona brakująca informacja o wersji *a.txt* .

    5. Wyewidencjonowany plik *b.txt* jest scalany z zawartością pliku *b.txt* lokalnego.

    6. Zaktualizowany plik *b.txt* można teraz zaewidencjonować.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflags używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md)
