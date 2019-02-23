---
title: Funkcja SccAddFromScc | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 199f89d7c2ce4c9674ed9d79ec13a1b392b70371
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56707006"
---
# <a name="sccaddfromscc-function"></a>Funkcja SccAddFromScc
Ta funkcja umożliwia użytkownikowi przeglądanie w poszukiwaniu plików, które znajdują się już w systemie kontroli źródła i następnie wprowadzić tych plików będących częścią bieżącego projektu. Na przykład tej funkcji można uzyskać z wspólnego pliku nagłówkowego do bieżącego projektu bez kopiowania pliku. Zwracana tablica plików, `lplpFileNames`, zawiera listę plików, które użytkownik chce, aby dodać do projektu środowiska IDE.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccAddFromScc (
   LPVOID   pvContext,
   HWND     hWnd,
   LPLONG   lpnFiles,
   LPCSTR** lplpFileNames
);
```

### <a name="parameters"></a>Parametry
 pvContext

[in] Struktura kontekście wtyczki kontroli źródła.

 hWnd

[in] Uchwyt okna środowiska IDE, które wtyczka do kontroli źródła można użyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.

 lpnFiles

[out w] Bufor liczbę plików, które są dodawane w. (Jest to `NULL` Jeśli pamięci wskazywany przez `lplpFileNames` ma zostać zwolniona. Zobacz uwagi Aby uzyskać szczegółowe informacje).

 lplpFileNames

[out w] Tablica wskaźników do nazwy pliku bez ścieżki katalogu. Ta tablica jest przydzielny i wolny, wtyczka do kontroli źródła. Jeśli `lpnFiles` = 1 i `lplpFileNames` nie `NULL`, imię w tablicy, wskazywana przez `lplpFileNames` zawiera folder docelowy.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Pliki zostały pomyślnie się i dodane do projektu.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana z żadnego efektu.|
|SCC_I_RELOADFILE|Pliku lub projektu wymaga ponownego załadowania.|

## <a name="remarks"></a>Uwagi
 IDE wywołuje tę funkcję. Jeśli wtyczka do kontroli źródła obsługuje, określając folder lokalne miejsce docelowe, IDE przekazuje `lpnFiles` = 1 i przekazuje nazwę folderu lokalnego na `lplpFileNames`.

 Po wywołaniu `SccAddFromScc` funkcja zwraca, wtyczka przypisał wartości do `lpnFiles` i `lplpFileNames`, przydzielania pamięci dla tablicy nazwy pliku, zgodnie z potrzebami (należy pamiętać, że ten przydział zastępuje wskaźnika w `lplpFileNames`). Wtyczka do kontroli źródła jest odpowiedzialny za wprowadzanie wszystkich plików w katalogu użytkownika lub w folderze określonym oznaczenia. IDE dodaje pliki w projekcie środowiska IDE.

 Na koniec IDE wywołuje tę funkcję, po raz drugi, przekazując `NULL` dla `lpnFiles`. To jest interpretowany jako sygnał specjalne przez dodatek typu plug-in, aby zwolnić pamięć przydzielona dla tablicy nazw plików w kontroli źródła `lplpFileNames``.`

 `lplpFileNames` jest `char ***` wskaźnika. Wtyczka do kontroli źródła umieszcza wskaźnik do tablicy wskaźników do nazw plików, w związku z tym przekazanie na liście w sposób standardowy dla tego interfejsu API.

> [!NOTE]
>  Początkowej wersji interfejsu API VSSCI nie podał sposób, aby wskazać projekt docelowy dla dodanych plików. Aby uwzględnić to semantykę `lplpFIleNames` parametru zostały rozszerzone i ułatwiają parametrem wchodzącym/wychodzącym zamiast parametru wyjściowego. Jeśli tylko jeden plik zostanie określony, oznacza to, że wartość wskazywana przez `lpnFiles` = 1, a następnie pierwszy element `lplpFileNames` zawiera folder docelowy. Aby użyć tych nowych semantyki wywołania IDE `SccSetOption` funkcją `nOption`parametr `SCC_OPT_SHARESUBPROJ`. Jeśli wtyczka do kontroli źródła nie obsługuje semantykę, zwraca `SCC_E_OPTNOTSUPPORTED`. Wykonując tak wyłącza użycie **Dodaj z kontroli źródła** funkcji. Jeśli wtyczka obsługuje **Dodaj z kontroli źródła** funkcji (`SCC_CAP_ADDFROMSCC`), a następnie musi obsługują semantyki nowego i wróć `SCC_I_SHARESUBPROJOK`.

## <a name="see-also"></a>Zobacz także
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)