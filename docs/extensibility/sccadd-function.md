---
description: Ta funkcja dodaje nowe pliki do systemu kontroli źródła.
title: SccAdd, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f73a91f7f801ca89a633f1722e0c4d1183fb3dc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904854"
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

[in] Struktura kontekstu wtyczki kontroli źródła.

 Hwnd

[in] Dojście do okna IDE, które wtyczka kontroli źródła może używać jako elementu nadrzędnego dla wszystkich okien dialogowych, które udostępnia.

 nFiles

[in] Liczba plików wybranych do dodania do bieżącego projektu, jak podano w `lpFileNames` tablicy.

 lpFileNames

[in] Tablica w pełni kwalifikowanych nazw lokalnych plików do dodania.

 lpComment

[in] Komentarz do zastosowania do wszystkich dodawanych plików.

 pfOptions

[in] Tablica flag poleceń, dostarczanych dla każdego pliku.

 pvOptions

[in] Opcje specyficzne dla wtyczki kontroli źródła.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła dla tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Operacja dodawania powiodła się.|
|SCC_E_FILEALREADYEXISTS|Wybrany plik jest już pod kontrolą źródła.|
|SCC_E_TYPENOTSUPPORTED|Typ pliku (na przykład binarny) nie jest obsługiwany przez system kontroli źródła.|
|SCC_E_OPNOTSUPPORTED|System kontroli źródła nie obsługuje tej operacji.|
|SCC_E_ACCESSFAILURE|Występuje problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub zdyskusją. Zaleca się ponawianie próby.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_NONSPECIFICERROR|Nieokreślona awaria; dodawanie nie jest wykonywane.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed zakończeniem.|
|SCC_I_RELOADFILE|Należy ponownie załadować plik lub projekt.|
|SCC_E_FILENOTEXIST|Nie znaleziono pliku lokalnego.|

## <a name="remarks"></a>Uwagi
 Typy `fOptions` zwykle są tutaj zastępowane tablicą , z jedną `pfOptions` `LONG` specyfikacją opcji na plik. Jest to spowodowane tym, że typ pliku może się różnić w zależności od pliku.

> [!NOTE]
> Określenie opcji i dla tego samego pliku jest nieprawidłowe, ale prawidłowe jest `SCC_FILETYPE_TEXT` określenie żadnej z tych `SCC_FILETYPE_BINARY` opcji. Ustawienie nie jest takie samo jak ustawienie , w którym to przypadku wtyczka kontroli źródła automatycznie określa `SCC_FILETYPE_AUTO` typ pliku.

 Poniżej znajduje się lista flag używanych w `pfOptions` tablicy:

|Opcja|Wartość|Znaczenie|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|Wtyczka kontroli źródła powinna wykryć typ pliku.|
|SCC_FILETYPE_TEXT|0x01|Wskazuje plik tekstowy ASCII.|
|SCC_FILETYPE_BINARY|0x02|Wskazuje typ pliku inny niż tekst ASCII.|
|SCC_ADD_STORELATEST|0x04|Przechowuje tylko najnowszą kopię pliku bez różnic.|
|SCC_FILETYPE_TEXT_ANSI|0x08|Traktuje plik jako tekst ANSI.|
|SCC_FILETYPE_UTF8|0x10|Traktuje plik jako tekst Unicode w formacie UTF8.|
|SCC_FILETYPE_UTF16LE|0x20|Traktuje plik jako tekst Unicode w formacie UTF16 Little Endian.|
|SCC_FILETYPE_UTF16BE|0x40|Traktuje plik jako tekst Unicode w formacie UTF16 Big Endian.|

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-in-api-functions.md)
