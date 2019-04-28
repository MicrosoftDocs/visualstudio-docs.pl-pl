---
title: Funkcja SccGet | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2a5d5065ca427f0319174aa59e6b87d356816d4c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432430"
---
# <a name="sccget-function"></a>SccGet, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja pobiera kopię jeden lub więcej plików do przeglądania i kompilacji, ale nie do edycji. W większości systemów pliki są oznaczone jako tylko do odczytu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekstu wtyczka do kontroli źródła.  
  
 hWnd  
 [in] Uchwyt okna środowiska IDE, które wtyczka do kontroli źródła można użyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.  
  
 Niepowodzeń  
 [in] Liczba plików określonych w `lpFileNames` tablicy.  
  
 lpFileNames  
 [in] Tablica z w pełni kwalifikowane nazwy plików do pobrania.  
  
 fOptions  
 [in] Polecenie flagi (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 pvOptions  
 [in] Opcje plug-określonych kontroli źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Powodzenie operacji pobierania.|  
|SCC_E_FILENOTCONTROLLED|Plik nie jest pod kontrolą źródła.|  
|SCC_E_OPNOTSUPPORTED|System kontroli źródła nie obsługuje tej operacji.|  
|SCC_E_FILEISCHECKEDOUT|Nie można pobrać pliku, który użytkownik aktualnie został wyewidencjonowany.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji o zasoby. Ponowienie próby jest zalecane.|  
|SCC_E_NOSPECIFIEDVERSION|Określono nieprawidłową wersję lub daty/godziny.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd; Nie można zsynchronizować pliku.|  
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie ma uprawnień do wykonania tej operacji.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana z liczbą i tablicę nazw plików, które mają zostać pobrane. Jeśli środowisko IDE przekazuje flagę `SCC_GET_ALL`, oznacza to, że elementy w `lpFileNames` nie są pliki, ale katalogów, a wszystkie pliki w kontroli źródła w danym katalogi, które mają być pobierane.  
  
 `SCC_GET_ALL` Flagi mogą być łączone z `SCC_GET_RECURSIVE` flagę, aby pobrać wszystkie pliki w danym katalogów i wszystkie podkatalogi również.  
  
> [!NOTE]
> `SCC_GET_RECURSIVE` nigdy nie powinien być przekazywany bez `SCC_GET_ALL`. Należy również zauważyć, że jeśli katalogi C:\A i C:\A\B Pobierz zarówno przekazywane na rekursywny, C:\A\B i jego podkatalogach faktycznie pobierany dwa razy. Odpowiada za IDE — i nie źródło sterowania dodatku plug-in — Aby upewnić się, że duplikaty takich są przechowywane poza tablicy.  
  
 Na koniec, nawet jeśli wtyczka kontroli źródła określony `SCC_CAP_GET_NOUI` flagi na inicjowanie, wskazujący, że nie ma interfejsu użytkownika dla polecenia Get, ta funkcja nadal może zostać wywołana przez środowisko IDE do pobierania plików. Flaga po prostu oznacza, że środowisko IDE nie wyświetla element menu Get, wtyczka nie powinien zapewniać wszelkich elementów interfejsu użytkownika.  
  
## <a name="renaming-and-sccget"></a>Zmienianie nazwy i SccGet  
 Sytuacja: użytkownik wyewidencjonuje pliku, na przykład a.txt i modyfikuje je. Zanim a.txt mogą zostać zaewidencjonowane, drugi użytkownik zmienia nazwę a.txt na b.txt w bazie danych kontroli źródła, sprawdza out b.txt, sprawia, że pewnych zmian w pliku i sprawdza, czy pliku. Pierwszy użytkownik chce, aby zmiany wprowadzone przez drugi użytkownik, więc pierwszy użytkownik zmienia nazwę swojej lokalnej wersji pliku a.txt na b.txt i wykonuje pobierania pliku. Jednak lokalna pamięć podręczna, która śledzi numery wersji nadal uzna za pierwszą wersję a.txt są przechowywane lokalnie, a więc kontroli źródła nie może rozpoznać różnice.  
  
 Istnieją dwa sposoby, aby rozwiązać ten problem, gdzie w lokalnej pamięci podręcznej wersji kontroli źródła staje się zsynchronizowany z bazy danych kontroli źródła:  
  
1. Nie zezwalaj na zmianę nazwy pliku w bazie danych kontroli źródła, która jest obecnie wyewidencjonowany.  
  
2. Czy wielokrotność "Usuń stare" następuje "Dodaj nowe". Następującego algorytmu jest jednym ze sposobów osiągnięcia tego.  
  
    1. Wywołaj [SccQueryChanges](../extensibility/sccquerychanges-function.md) funkcji, aby dowiedzieć się więcej na temat zmiany nazwy a.txt do b.txt w bazie danych kontroli źródła.  
  
    2. Zmień nazwę lokalnych a.txt b.txt.  
  
    3. Wywołaj `SccGet` funkcji dla a.txt i b.txt.  
  
    4. Ponieważ a.txt nie istnieje w bazie danych kontroli źródła, wersja lokalna pamięć podręczna są przeczyszczane Brak a.txt informacji o wersji.  
  
    5. Plik b.txt wyewidencjonowany jest scalany z zawartości pliku lokalnego b.txt.  
  
    6. Teraz mogą zostać zaewidencjonowane b.txt zaktualizowany plik.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Flagi bitowe używane przez określone polecenia ](../extensibility/bitflags-used-by-specific-commands.md)
