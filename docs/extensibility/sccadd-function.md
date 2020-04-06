---
title: Funkcja SccAdd | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 23a6226b0d3cc2441a509c16b2e4672a766f3329
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701312"
---
# <a name="sccadd-function"></a>SccAdd, funkcja
Ta funkcja dodaje nowe pliki do systemu kontroli źródła.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccAdd(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG*     pfOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametry
 pvContext

[w] Struktura kontekstu wtyczki formantu źródła.

 Hwnd

[w] Dojście do okna IDE, którego wtyczka formantu źródła może używać jako element nadrzędny dla wszystkich okien dialogowych, które udostępnia.

 nFiles

[w] Liczba plików wybranych do dodania do bieżącego `lpFileNames` projektu, jak podano w tablicy.

 lpFileNames

[w] Tablica w pełni kwalifikowanych nazw lokalnych plików do dodania.

 lpKomentuj

[w] Komentarz ma być stosowany do wszystkich dodawanych plików.

 pfOptions (pfOptions)

[w] Tablica flag poleceń, podana na podstawie dla pliku.

 pvOpcje

[w] Opcje specyficzne dla wtyczki sterowania źródłem.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Operacja dodawania zakończyła się pomyślnie.|
|SCC_E_FILEALREADYEXISTS|Wybrany plik jest już pod kontrolą źródła.|
|SCC_E_TYPENOTSUPPORTED|Typ pliku (na przykład binarny) nie jest obsługiwany przez system kontroli źródła.|
|SCC_E_OPNOTSUPPORTED|System kontroli źródła nie obsługuje tej operacji.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zaleca się ponowną próbę.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_NONSPECIFICERROR|Niespecyficzna awaria; dodać nie wykonano.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed zakończeniem.|
|SCC_I_RELOADFILE|Plik lub projekt musi zostać ponownie załadowany.|
|SCC_E_FILENOTEXIST|Nie znaleziono pliku lokalnego.|

## <a name="remarks"></a>Uwagi
 Zwykle `fOptions` są zastępowane tutaj `pfOptions`przez tablicę, z jedną `LONG` specyfikacją opcji na plik. Dzieje się tak, ponieważ typ pliku może się różnić w zależności od pliku.

> [!NOTE]
> Jest nieprawidłowy, `SCC_FILETYPE_TEXT` aby `SCC_FILETYPE_BINARY` określić zarówno i opcje dla tego samego pliku, ale jest prawidłowy, aby określić żadnego z nich. Ustawienie nie jest takie `SCC_FILETYPE_AUTO`samo jak ustawienie , w którym to przypadku wtyczka kontroli źródła autodetects typu pliku.

 Poniżej znajduje się lista `pfOptions` flag używanych w tablicy:

|Opcja|Wartość|Znaczenie|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|Wtyczka kontroli źródła powinna wykryć typ pliku.|
|SCC_FILETYPE_TEXT|0x01|Wskazuje plik tekstowy ASCII.|
|SCC_FILETYPE_BINARY|0x02|Wskazuje typ pliku inny niż tekst ASCII.|
|SCC_ADD_STORELATEST|0x04|Przechowuje tylko najnowszą kopię pliku, bez delt.|
|SCC_FILETYPE_TEXT_ANSI|0x08|Traktuje plik jako tekst ANSI.|
|SCC_FILETYPE_UTF8|0x10|Traktuje plik jako tekst Unicode w formacie UTF8.|
|SCC_FILETYPE_UTF16LE|0x20|Traktuje plik jako tekst Unicode w formacie UTF16 Little Endian.|
|SCC_FILETYPE_UTF16BE|0x40|Traktuje plik jako tekst Unicode w formacie UTF16 Big Endian.|

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki sterowania źródłem](../extensibility/source-control-plug-in-api-functions.md)
