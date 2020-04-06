---
title: QUERYCHANGESFUNC | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30864cae95672f4026084a94c5474d165b124cba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701631"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Jest to funkcja wywołania zwrotnego używana przez operację [SccQueryChanges](../extensibility/sccquerychanges-function.md) do wyliczania kolekcji nazw plików i określania stanu każdego pliku.

 Funkcja `SccQueryChanges` jest podana lista plików i `QUERYCHANGESFUNC` wskaźnik do wywołania zwrotnego. Wtyczka kontroli źródła wylicza na danej liście i zapewnia stan (za pośrednictwem tego wywołania zwrotnego) dla każdego pliku na liście.

## <a name="signature"></a>Sygnatura

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Parametry
 pvCallerData

[w] Parametr `pvCallerData` przekazany przez wywołującego (IDE) do [SccQueryChanges](../extensibility/sccquerychanges-function.md). Wtyczka kontroli źródła nie należy podejmować żadnych założeń dotyczących zawartości tej wartości.

 pChangesDana

[w] Wskaźnik do [struktury struktura QUERYCHANGESDATA](#LinkQUERYCHANGESDATA) opisująca zmiany w pliku.

## <a name="return-value"></a>Wartość zwracana
 IDE zwraca odpowiedni kod błędu:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Kontynuuj przetwarzanie.|
|SCC_I_OPERATIONCANCELED|Zatrzymaj przetwarzanie.|
|SCC_E_xxx|Każdy odpowiedni błąd SCC powinien zatrzymać przetwarzanie.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a>Struktura QUERYCHANGESDATA
 Struktura przekazywana dla każdego pliku wygląda następująco:

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

 dwSize Rozmiar tej struktury (w bajtach).

 lpFileName Oryginalna nazwa pliku dla tego elementu.

 dwChangeType Kod wskazujący stan pliku:

|Code|Opis|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|Nie można powiedzieć, co się zmieniło.|
|`SCC_CHANGE_UNCHANGED`|Brak zmian nazwy dla tego pliku.|
|`SCC_CHANGE_DIFFERENT`|Plik o innej tożsamości, ale ta sama nazwa istnieje w bazie danych.|
|`SCC_CHANGE_NONEXISTENT`|Plik nie istnieje ani w bazie danych, ani lokalnie.|
|`SCC_CHANGE_DATABASE_DELETED`|Plik usunięty w bazie danych.|
|`SCC_CHANGE_LOCAL_DELETED`|Plik został usunięty lokalnie, ale plik nadal istnieje w bazie danych. Jeśli nie można tego `SCC_CHANGE_DATABASE_ADDED`ustalić, zwróć .|
|`SCC_CHANGE_DATABASE_ADDED`|Plik dodany do bazy danych, ale nie istnieje lokalnie.|
|`SCC_CHANGE_LOCAL_ADDED`|Plik nie istnieje w bazie danych i jest nowym plikiem lokalnym.|
|`SCC_CHANGE_RENAMED_TO`|Plik został zmieniony lub przeniesiony `lpLatestName`do bazy danych jako .|
|`SCC_CHANGE_RENAMED_FROM`|Plik zmieniono nazwę lub `lpLatestName`przeniesiono do bazy danych z ; jeśli jest to zbyt drogie, aby śledzić, zwróć inną flagę, taką jak `SCC_CHANGE_DATABASE_ADDED`.|

 lpLatestName Bieżąca nazwa pliku dla tego elementu.

## <a name="see-also"></a>Zobacz też
- [Funkcje wywołania zwrotnego zaimplementowane przez IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Kody błędów](../extensibility/error-codes.md)
