---
title: Funkcja SccGet | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2d69308d2f569fc2e0d72dcf64c762687955d4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700893"
---
# <a name="sccget-function"></a>SccGet, funkcja
Ta funkcja pobiera kopię jednego lub więcej plików do przeglądania i kompilowania, ale nie do edycji. W większości systemów pliki są oznaczane jako tylko do odczytu.

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

[w] Struktura kontekstu wtyczki formantu źródła.

 Hwnd

[w] Dojście do okna IDE, którego wtyczka formantu źródła może używać jako element nadrzędny dla wszystkich okien dialogowych, które udostępnia.

 nFiles

[w] Liczba plików określonych `lpFileNames` w tablicy.

 lpFileNames

[w] Tablica w pełni kwalifikowanych nazw plików do pobrania.

 Foptions

[w] Flagi poleceń (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).

 pvOpcje

[w] Opcje specyficzne dla wtyczki sterowania źródłem.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Sukces operacji get.|
|SCC_E_FILENOTCONTROLLED|Plik nie jest pod kontrolą źródła.|
|SCC_E_OPNOTSUPPORTED|System kontroli źródła nie obsługuje tej operacji.|
|SCC_E_FILEISCHECKEDOUT|Nie można uzyskać pliku, który użytkownik aktualnie wyewidencjonował.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zaleca się ponowną próbę.|
|SCC_E_NOSPECIFIEDVERSION|Określono nieprawidłową wersję lub datę/godzinę.|
|SCC_E_NONSPECIFICERROR|Niespecyficzna awaria; nie został zsynchronizowany.|
|SCC_I_OPERATIONCANCELED|Operacja anulowana przed zakończeniem.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie jest upoważniony do wykonania tej operacji.|

## <a name="remarks"></a>Uwagi
 Ta funkcja jest wywoływana z liczbą i tablicą nazw plików do pobrania. Jeśli IDE przechodzi `SCC_GET_ALL`flagę, oznacza to, że elementy w `lpFileNames` nie są pliki, ale katalogi i że wszystkie pliki pod kontrolą źródła w danym katalogu mają być pobierane.

 Flagę `SCC_GET_ALL` można połączyć `SCC_GET_RECURSIVE` z flagą, aby pobrać wszystkie pliki w podanych katalogach i wszystkich podkatalogach.

> [!NOTE]
> `SCC_GET_RECURSIVE`nigdy nie powinny `SCC_GET_ALL`być przekazywane bez . Należy również zauważyć, że jeśli katalogi *C:\A* i *C:\A\B* są przekazywane na cykliczne get, *C:\A\B* i wszystkie jego podkatalogi zostaną faktycznie pobrane dwa razy. Jest to odpowiedzialność IDE, a nie wtyczki kontroli źródła, aby upewnić się, że duplikaty takie jak ten są przechowywane z tablicy.

 Na koniec nawet jeśli wtyczka kontroli `SCC_CAP_GET_NOUI` źródła określiła flagę podczas inicjowania, wskazując, że nie ma interfejsu użytkownika dla polecenia Pobierz, ta funkcja może nadal być wywoływana przez IDE w celu pobierania plików. Flaga oznacza po prostu, że IDE nie wyświetla Get elementu menu i że dodatek nie oczekuje się, aby zapewnić żadnych interfejsu użytkownika.

## <a name="rename-files-and-sccget"></a>Zmienianie nazw plików i SccGet
 Sytuacja: użytkownik wyewidencjonuje plik, na przykład *a.txt*i modyfikuje go. Zanim można zaewidencjonować *a.txt,* drugi użytkownik zmienia nazwę *a.txt* na *b.txt* w bazie danych kontroli źródła, wyewidencjonuje *b.txt*, wprowadza pewne modyfikacje do pliku i sprawdza plik. Pierwszy użytkownik chce zmiany wprowadzone przez drugiego użytkownika, więc pierwszy użytkownik zmienia nazwę lokalnej wersji pliku *a.txt* na *b.txt* i nie dostać się do pliku. Jednak lokalna pamięć podręczna, która przechowuje numery wersji nadal uważa, że pierwsza wersja *a.txt* jest przechowywana lokalnie i dlatego kontrola źródła nie może rozwiązać różnic.

 Istnieją dwa sposoby rozwiązania tej sytuacji, w której lokalna pamięć podręczna wersji kontroli źródła staje się zsynchronizowana z bazą danych kontroli źródła:

1. Nie zezwalaj na zmianę nazwy pliku w bazie danych kontroli źródła, która jest aktualnie wyewidencjonowana.

2. Wykonaj odpowiednik "delete old", a następnie "dodaj nowy". Poniższy algorytm jest jednym ze sposobów, aby to osiągnąć.

    1. Wywołanie [funkcji SccQueryChanges,](../extensibility/sccquerychanges-function.md) aby dowiedzieć się więcej o zmianie nazwy *a.txt* na *b.txt* w bazie danych kontroli źródła.

    2. Zmień nazwę lokalnego *a.txt* na *b.txt*.

    3. Wywołanie `SccGet` funkcji zarówno *a.txt,* jak i *b.txt*.

    4. Ponieważ *a.txt* nie istnieje w bazie danych kontroli źródła, pamięć podręczna wersji lokalnej jest czyszczona z brakujących informacji o wersji *a.txt.*

    5. Wyewidencjonowany plik *b.txt* jest scalany z zawartością lokalnego pliku *b.txt.*

    6. Zaktualizowany plik *b.txt* można teraz zaewidencjonować.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki sterowania źródłem](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflags używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md)
