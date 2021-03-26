---
title: QUERYCHANGESFUNC | Microsoft Docs
description: Funkcja wywołania zwrotnego QUERYCHANGESFUNC służy do wyliczania kolekcji nazw plików i określania stanu każdego pliku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cc797d68f6df6d9aab93554ba95955a7d9f45eea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068625"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Jest to funkcja wywołania zwrotnego używana przez operację [SccQueryChanges](../extensibility/sccquerychanges-function.md) do wyliczania kolekcji nazw plików i określania stanu każdego pliku.

 `SccQueryChanges`Funkcja otrzymuje listę plików i wskaźnik do `QUERYCHANGESFUNC` wywołania zwrotnego. Wtyczka do kontroli źródła wylicza daną listę i zapewnia stan (za pośrednictwem tego wywołania zwrotnego) dla każdego pliku na liście.

## <a name="signature"></a>Podpis

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Parametry
 pvCallerData

podczas `pvCallerData` Parametr przesłany przez obiekt wywołujący (IDE) do [SccQueryChanges](../extensibility/sccquerychanges-function.md). Wtyczka do kontroli źródła nie powinna mieć żadnych założeń dotyczących zawartości tej wartości.

 pChangesData

podczas Wskaźnik do struktury [struktury QUERYCHANGESDATA](#LinkQUERYCHANGESDATA) opisującej zmiany w pliku.

## <a name="return-value"></a>Wartość zwracana
 IDE zwraca odpowiedni kod błędu:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Kontynuuj przetwarzanie.|
|SCC_I_OPERATIONCANCELED|Zatrzymaj przetwarzanie.|
|SCC_E_xxx|Każdy odpowiedni błąd SCC powinien przerwać przetwarzanie.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a> QUERYCHANGESDATA, struktura
 Struktura przeniesiona dla każdego pliku wygląda następująco:

```cpp
struct QUERYCHANGESDATA_A
{
    DWORD  dwSize;
    LPCSTR lpFileName;
    DWORD  dwChangeType;
    LPCSTR lpLatestName;
};

typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;

struct QUERYCHANGESDATA_W
{
    DWORD   dwSize;
    LPCWSTR lpFileName;
    DWORD   dwChangeType;
    LPCWSTR lpLatestName;
};
```

 dwSize rozmiar tej struktury (w bajtach).

 lpFileName oryginalną nazwę pliku dla tego elementu.

 Kod dwChangeType wskazujący stan pliku:

|Kod|Opis|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|Nie można ustalić, co zostało zmienione.|
|`SCC_CHANGE_UNCHANGED`|Brak zmian nazw dla tego pliku.|
|`SCC_CHANGE_DIFFERENT`|Plik z inną tożsamością, ale w bazie danych istnieje taka sama nazwa.|
|`SCC_CHANGE_NONEXISTENT`|Plik nie istnieje w bazie danych lub lokalnie.|
|`SCC_CHANGE_DATABASE_DELETED`|Plik został usunięty z bazy danych.|
|`SCC_CHANGE_LOCAL_DELETED`|Plik został usunięty lokalnie, ale plik nadal istnieje w bazie danych. Jeśli nie można określić, zwróć `SCC_CHANGE_DATABASE_ADDED` .|
|`SCC_CHANGE_DATABASE_ADDED`|Plik został dodany do bazy danych, ale nie istnieje lokalnie.|
|`SCC_CHANGE_LOCAL_ADDED`|Plik nie istnieje w bazie danych i jest nowym plikiem lokalnym.|
|`SCC_CHANGE_RENAMED_TO`|Plik został zmieniony lub przeniesiony do bazy danych jako `lpLatestName` .|
|`SCC_CHANGE_RENAMED_FROM`|Plik został zmieniony lub przeniesiony do bazy danych z `lpLatestName` ; Jeśli jest zbyt kosztowny do śledzenia, zwróć inną flagę, taką jak `SCC_CHANGE_DATABASE_ADDED` .|

 lpLatestName bieżącą nazwę pliku dla tego elementu.

## <a name="see-also"></a>Zobacz też
- [Funkcje wywołania zwrotnego zaimplementowane przez IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Kody błędów](../extensibility/error-codes.md)
