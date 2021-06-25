---
title: QueryCHANGESFUNC | Microsoft Docs
description: Funkcja wywołania zwrotnego QUERYCHANGESFUNC służy do wyliczania kolekcji nazw plików i określania stanu każdego pliku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: b061fbfb6644f77348574020c0a5cb614691ae6b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899137"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Jest to funkcja wywołania zwrotnego używana przez operację [SccQueryChanges](../extensibility/sccquerychanges-function.md) do wyliczania kolekcji nazw plików i określania stanu każdego pliku.

 Funkcja `SccQueryChanges` ma nadaną listę plików i wskaźnik do wywołania `QUERYCHANGESFUNC` zwrotnego. Wtyczka kontroli źródła wylicza dane na danej liście i zapewnia stan (za pośrednictwem tego wywołania zwrotnego) dla każdego pliku na liście.

## <a name="signature"></a>Podpis

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Parametry
 pvCallerData

[in] Parametr `pvCallerData` przekazany przez wywołujący (IDE) do [SccQueryChanges](../extensibility/sccquerychanges-function.md). Wtyczka kontroli źródła nie powinna mieć żadnych założeń dotyczących zawartości tej wartości.

 pChangesData

[in] Wskaźnik do struktury [QUERYCHANGESDATA](#LinkQUERYCHANGESDATA) opisującej zmiany w pliku.

## <a name="return-value"></a>Wartość zwracana
 Ide zwraca odpowiedni kod błędu:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Kontynuuj przetwarzanie.|
|SCC_I_OPERATIONCANCELED|Zatrzymaj przetwarzanie.|
|SCC_E_xxx|Wszelkie odpowiednie błędy SCC powinny przestać przetwarzać.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a> QUERYCHANGESDATA, struktura
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

|Kod|Opis|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|Nie można stwierdzić, co się zmieniło.|
|`SCC_CHANGE_UNCHANGED`|Nazwa tego pliku nie zmienia się.|
|`SCC_CHANGE_DIFFERENT`|Plik z inną tożsamością, ale taka sama nazwa istnieje w bazie danych.|
|`SCC_CHANGE_NONEXISTENT`|Plik nie istnieje ani w bazie danych, ani lokalnie.|
|`SCC_CHANGE_DATABASE_DELETED`|Plik usunięty w bazie danych.|
|`SCC_CHANGE_LOCAL_DELETED`|Plik został usunięty lokalnie, ale plik nadal istnieje w bazie danych. Jeśli nie można tego ustalić, `SCC_CHANGE_DATABASE_ADDED` zwróć .|
|`SCC_CHANGE_DATABASE_ADDED`|Plik dodany do bazy danych, ale nie istnieje lokalnie.|
|`SCC_CHANGE_LOCAL_ADDED`|Plik nie istnieje w bazie danych i jest nowym plikiem lokalnym.|
|`SCC_CHANGE_RENAMED_TO`|Nazwa pliku została zmieniona lub przeniesiona w bazie danych jako `lpLatestName` .|
|`SCC_CHANGE_RENAMED_FROM`|Nazwa pliku została zmieniona lub przeniesiona w bazie danych z . Jeśli śledzenie jest zbyt kosztowne, zwróć `lpLatestName` inną flagę, taką jak `SCC_CHANGE_DATABASE_ADDED` .|

 lpLatestName Bieżąca nazwa pliku dla tego elementu.

## <a name="see-also"></a>Zobacz też
- [Funkcje wywołania zwrotnego implementowane przez ide](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Kody błędów](../extensibility/error-codes.md)
