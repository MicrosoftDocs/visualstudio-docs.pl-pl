---
description: Ta funkcja pobiera kopię jednego lub większej liczby plików do wyświetlania i kompilowania, ale nie do edycji.
title: Funkcja SccGet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 805c19b0c326e8389b4e1905edf370ad042aac92
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904555"
---
# <a name="sccget-function"></a>Funkcja SccGet
Ta funkcja pobiera kopię jednego lub większej liczby plików do wyświetlania i kompilowania, ale nie do edycji. W większości systemów pliki są oznaczane jako tylko do odczytu.

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

[in] Struktura kontekstu wtyczki kontroli źródła.

 Hwnd

[in] Dojście do okna IDE, które wtyczka kontroli źródła może używać jako elementu nadrzędnego dla wszystkich okien dialogowych, które zawiera.

 nFiles

[in] Liczba plików określona w `lpFileNames` tablicy.

 lpFileNames

[in] Tablica w pełni kwalifikowanych nazw plików do pobrania.

 Foptions

[in] Flagi poleceń ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 pvOptions

[in] Opcje specyficzne dla wtyczki kontroli źródła.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła dla tej funkcji zwraca jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Powodzenie operacji get.|
|SCC_E_FILENOTCONTROLLED|Plik nie jest pod kontrolą źródła.|
|SCC_E_OPNOTSUPPORTED|System kontroli źródła nie obsługuje tej operacji.|
|SCC_E_FILEISCHECKEDOUT|Nie można pobrać pliku, który użytkownik obecnie wyewidencjonował.|
|SCC_E_ACCESSFAILURE|Występuje problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub zdyskulacji. Zaleca się ponawianie próby.|
|SCC_E_NOSPECIFIEDVERSION|Określono nieprawidłową wersję lub datę/godzina.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd; plik nie został zsynchronizowany.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed zakończeniem.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie ma autoryzacji do wykonania tej operacji.|

## <a name="remarks"></a>Uwagi
 Ta funkcja jest wywoływana z licznikiem i tablicą nazw plików do pobrania. Jeśli idee przekazuje flagę , oznacza to, że elementy w programie nie są plikami, ale katalogami, a wszystkie pliki w kontroli źródła w danych katalogach mają `SCC_GET_ALL` `lpFileNames` zostać pobrane.

 Flagę można połączyć z flagą , aby pobrać wszystkie pliki w danych katalogach i `SCC_GET_ALL` `SCC_GET_RECURSIVE` wszystkich podkatalogach.

> [!NOTE]
> `SCC_GET_RECURSIVE` Nigdy nie należy przechodzić bez `SCC_GET_ALL` . Należy również pamiętać, że jeśli katalogi *C:\A* i *C:\A\B* są przekazywane w cyklicznym pobieraniu, *C:\A\B* i wszystkie jego podkatalogi zostaną faktycznie pobrane dwukrotnie. To odpowiedzialność środowiska IDE — a nie wtyczki kontroli źródła — ma na celu zapewnienie, że takie duplikaty są przechowywane poza tablicą.

 Na koniec, nawet jeśli wtyczka kontroli źródła podała flagę podczas inicjowania, wskazując, że nie ma interfejsu użytkownika dla polecenia Get, ta funkcja może być nadal wywoływana przez ideę w celu pobrania `SCC_CAP_GET_NOUI` plików. Flaga oznacza po prostu, że w ide nie jest wyświetlany element menu Pobierz i że wtyczka nie powinien dostarczać żadnego interfejsu użytkownika.

## <a name="rename-files-and-sccget"></a>Zmienianie nazw plików i SccGet
 Sytuacja: użytkownik sprawdza plik, na przykłada.txt *,* i modyfikuje go. Przed *a.txt* zaewidencjonowania drugi użytkownik zmienia nazwę pliku *a.txt* na *b.txt* w bazie danych kontroli źródła, wyewidencjonował program *b.txt*, wprowadza pewne modyfikacje w pliku i zaewidencjonował plik. Pierwszy użytkownik chce, aby zmiany wprowadzone przez drugiego użytkownika zmieniły nazwę jego lokalnej wersji pliku *a.txt* na *b.txt* i przejmują plik. Jednak lokalna pamięć podręczna, która śledzi numery wersji, nadal myśli, że pierwsza wersja pakietu *a.txt* jest przechowywana lokalnie, więc kontrola źródła nie może rozwiązać różnic.

 Istnieją dwa sposoby rozwiązania tej sytuacji, w której lokalna pamięć podręczna wersji kontroli źródła nie jest zsynchronizowana z bazą danych kontroli źródła:

1. Nie zezwalaj na zmianę nazwy pliku w bazie danych kontroli źródła, która jest obecnie wyewidencjonowana.

2. Wykonaj odpowiednik "usuń stary", po którym następuje "dodaj nowy". Poniższy algorytm jest jednym ze sposobów osiągnięcia tego celu.

    1. Wywołaj [funkcję SccQueryChanges,](../extensibility/sccquerychanges-function.md) aby dowiedzieć się więcej na temat *zmiany nazwy* a.txtdob.txtw bazie danych kontroli źródła. 

    2. Zmień nazwę *lokalnegoa.txt* na *b.txt*.

    3. Wywołaj `SccGet` funkcję zarówno dla *a.txt,* *jak ib.txt*.

    4. Ponieważ *a.txt* nie istnieje w bazie danych kontroli źródła, lokalna pamięć podręczna wersji jest przeczyszczona z brakujących informacji *oa.txt* wersji.

    5. Wyewidencjonowany plikb.txtjest scalony z zawartością lokalnego *b.txt* pliku. 

    6. Zaktualizowany plik *b.txt* można teraz zaewidencjonować.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflags używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md)
