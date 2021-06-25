---
description: Ta funkcja umożliwia użytkownikowi przeglądanie plików, które znajdują się już w systemie kontroli źródła, a następnie ich część w bieżącym projekcie.
title: SccAddFromScc, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48560f135d73c4e53ba132845f4c768cdf4ac982
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904880"
---
# <a name="sccaddfromscc-function"></a>Funkcja SccAddFromScc
Ta funkcja umożliwia użytkownikowi przeglądanie plików, które znajdują się już w systemie kontroli źródła, a następnie ich część w bieżącym projekcie. Na przykład ta funkcja może pobrać wspólny plik nagłówkowy do bieżącego projektu bez kopiowania pliku. Tablica zwracanych plików zawiera listę plików, które użytkownik `lplpFileNames` chce dodać do projektu IDE.

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

[in] Struktura kontekstu wtyczki kontroli źródła.

 Hwnd

[in] Dojście do okna IDE, które wtyczka kontroli źródła może używać jako elementu nadrzędnego dla wszystkich okien dialogowych, które udostępnia.

 lpnFiles

[in, out] Bufor liczby dodawanych plików. (Jest `NULL` tak, jeśli pamięć wskazywana przez `lplpFileNames` ma zostać zwolniona. Zobacz uwagi, aby uzyskać szczegółowe informacje).

 Lplpfilenames

[in, out] Tablica wskaźników do wszystkich nazw plików bez ścieżek katalogów. Ta tablica jest przydzielana i freed przez wtyczkę kontroli źródła. Jeśli = 1 i nie jest , imię w `lpnFiles` `lplpFileNames` `NULL` tablicy wskazywane przez `lplpFileNames` zawiera folder docelowy.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła dla tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Pliki zostały pomyślnie umieszczone i dodane do projektu.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana bez efektu.|
|SCC_I_RELOADFILE|Należy ponownie załadować plik lub projekt.|

## <a name="remarks"></a>Uwagi
 Ide wywołuje tę funkcję. Jeśli wtyczka kontroli źródła obsługuje określanie lokalnego folderu docelowego, idee przekazuje wartość = 1 i przekazuje `lpnFiles` nazwę folderu lokalnego do pliku `lplpFileNames` .

 Po zwracaniu wywołania funkcji wtyczka przypisała wartości do elementów i , przydzielając pamięć dla tablicy nazw plików w razie potrzeby (należy zauważyć, że ta alokacja zastępuje `SccAddFromScc` `lpnFiles` wskaźnik w `lplpFileNames` obiekcie `lplpFileNames` ). Wtyczka kontroli źródła jest odpowiedzialna za umieszczenie wszystkich plików w katalogu użytkownika lub w określonym folderze oznaczenia. Następnie idee dodają pliki do projektu IDE.

 Na koniec idee wywołuje tę funkcję po raz drugi, przekazując dla `NULL` . `lpnFiles` Jest to interpretowane jako specjalny sygnał przez wtyczkę kontroli źródła w celu zwolnienia pamięci przydzielonej dla tablicy nazw plików w programie `lplpFileNames``.`

 `lplpFileNames` jest `char ***` wskaźnikiem. Wtyczka kontroli źródła umieszcza wskaźnik do tablicy wskaźników do nazw plików, przekazując listę w standardowy sposób dla tego interfejsu API.

> [!NOTE]
> Początkowe wersje interfejsu API VSSCI nie umożliwiały wskazania projektu docelowego dla dodanych plików. Aby to uwzględnić, semantyka parametru została rozszerzona, aby był on parametrem `lplpFIleNames` wejściowym/wychodzącym, a nie parametrem wyjściowym. Jeśli określono tylko jeden plik, czyli wartość wskazywana przez `lpnFiles` = 1, pierwszy element elementu zawiera folder `lplpFileNames` docelowy. Aby użyć tej nowej semantyki, ide wywołuje funkcję `SccSetOption` z `nOption` parametrem ustawionym na `SCC_OPT_SHARESUBPROJ` . Jeśli wtyczka kontroli źródła nie obsługuje semantyki, zwraca wartość `SCC_E_OPTNOTSUPPORTED` . Spowoduje to wyłączenie korzystania z funkcji **Dodaj z kontroli** źródła. Jeśli wtyczka obsługuje funkcję Dodaj z **kontroli** kodu źródłowego ( ), musi obsługiwać `SCC_CAP_ADDFROMSCC` nową semantykę i zwracać element `SCC_I_SHARESUBPROJOK` .

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
