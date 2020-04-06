---
title: Funkcja SccAddFromScc | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1dd32e31330cdce958e463a40a4d92f88b09afb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701245"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc, funkcja
Ta funkcja umożliwia użytkownikowi przeglądanie plików, które znajdują się już w systemie kontroli źródła, a następnie uczynić te pliki częścią bieżącego projektu. Na przykład ta funkcja może uzyskać wspólny plik nagłówka do bieżącego projektu bez kopiowania pliku. Tablica zwracana `lplpFileNames`plików zawiera listę plików, które użytkownik chce dodać do projektu IDE.

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

[w] Struktura kontekstu wtyczki formantu źródła.

 Hwnd

[w] Dojście do okna IDE, którego wtyczka formantu źródła może używać jako element nadrzędny dla wszystkich okien dialogowych, które udostępnia.

 lpnFiles

[w, na zewnątrz] Bufor dla liczby plików, które są dodawane w. (Jest `NULL` to, jeśli pamięć `lplpFileNames` wskazana przez ma zostać zwolniony. Zobacz Uwagi, aby uzyskać szczegółowe informacje).)

 Lplpfilenames

[w, na zewnątrz] Tablica wskaźników do wszystkich nazw plików bez ścieżek katalogowych. Ta tablica jest przydzielana i zwalniana przez wtyczkę formantu źródła. Jeśli `lpnFiles` = 1 `lplpFileNames` `NULL`i nie jest , imię `lplpFileNames` w tablicy wskazywki zawiera folder docelowy.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Pliki zostały pomyślnie zlokalizowane i dodane do projektu.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana bez efektu.|
|SCC_I_RELOADFILE|Plik lub projekt musi zostać ponownie załadowany.|

## <a name="remarks"></a>Uwagi
 IDE wywołuje tę funkcję. Jeśli wtyczka formantu źródła obsługuje określanie lokalnego `lpnFiles` folderu docelowego, IDE `lplpFileNames`przekazuje = 1 i przekazuje nazwę folderu lokalnego do .

 Gdy wywołanie `SccAddFromScc` funkcji powróci, wtyczka ma przypisane `lpnFiles` `lplpFileNames`wartości do i , przydzielając pamięć dla tablicy nazw plików w `lplpFileNames`razie potrzeby (należy pamiętać, że ta alokacja zastępuje wskaźnik w ). Wtyczka kontroli źródła jest odpowiedzialna za umieszczenie wszystkich plików w katalogu użytkownika lub w folderze określonego oznaczenia. IDE następnie dodaje pliki do projektu IDE.

 Na koniec IDE wywołuje tę funkcję po `NULL` raz `lpnFiles`drugi, przechodząc do . Jest to interpretowane jako specjalny sygnał przez wtyczkę kontroli źródła w celu zwolnienia pamięci przydzielonej dla tablicy nazw plików w`lplpFileNames``.`

 `lplpFileNames`jest `char ***` wskaźnikiem. Wtyczka kontroli źródła umieszcza wskaźnik do tablicy wskaźników do nazw plików, przekazując w ten sposób listę w standardowy sposób dla tego interfejsu API.

> [!NOTE]
> Początkowe wersje interfejsu API VSSCI nie umożliwiają wskazania projektu docelowego dla dodanych plików. Aby to uwzględnić, semantyka `lplpFIleNames` parametru została zwiększona, aby uczynić go parametrem in/out, a nie parametrem wyjściowym. Jeśli określono tylko pojedynczy plik, oznacza to, `lpnFiles` że wartość wskazywowa `lplpFileNames` przez = 1, a następnie pierwszy element zawiera folder docelowy. Aby użyć tych nowych semantyki, `SccSetOption` IDE wywołuje `nOption`funkcję `SCC_OPT_SHARESUBPROJ`z parametrem ustawionym na . Jeśli wtyczka kontroli źródła nie obsługuje semantyki, `SCC_E_OPTNOTSUPPORTED`zwraca program . W ten sposób wyłącza użycie funkcji **Dodaj z kontroli źródła.** Jeśli wtyczka obsługuje funkcję **Dodaj z kontroli źródła** (`SCC_CAP_ADDFROMSCC`), musi ona obsługiwać `SCC_I_SHARESUBPROJOK`nową semantykę i zwracać .

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki sterowania źródłem](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
