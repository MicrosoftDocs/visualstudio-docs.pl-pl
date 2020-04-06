---
title: Funkcja SccCheckin | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5ba512642e1a63d9d39856f96194d717583d44f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701180"
---
# <a name="scccheckin-function"></a>SccCheckin, funkcja
Ta funkcja sprawdza wcześniej wyewidencjonowane pliki do systemu kontroli źródła, przechowując zmiany i tworząc nową wersję. Ta funkcja jest wywoływana z liczbą i tablicą nazw plików, które mają zostać zaewidencjonowane.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccCheckin (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPSTR*    lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametry
 pvContext

[w] Struktura kontekstu wtyczki formantu źródła.

 Hwnd

[w] Dojście do okna IDE, które wtyczka SCC może używać jako element nadrzędny dla wszystkich okien dialogowych, które zapewnia.

 nFiles

[w] Liczba plików wybranych do zaewidencjonowania.

 lpFileNames

[w] Tablica w pełni kwalifikowanych nazw ścieżek lokalnych plików do zaewidencjonowania.

 lpKomentuj

[w] Komentarz ma zostać zastosowany do każdego z zaznaczonych plików, które są zaewidencjonowane. Ten parametr `NULL` jest, jeśli wtyczka kontroli źródła powinna monitować o komentarz.

 Foptions

[w] Flagi poleceń, 0 `SCC_KEEP_CHECKEDOUT`lub .

 pvOpcje

[w] Opcje specyficzne dla wtyczek SCC.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Plik został pomyślnie zaewidencjonowany.|
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie jest pod kontrolą kodu źródłowego.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zaleca się ponowną próbę.|
|SCC_E_NONSPECIFICERROR|Niespecyficzna awaria. Plik nie został zaewidencjonowany.|
|SCC_E_NOTCHECKEDOUT|Użytkownik nie wyewidencjonował pliku, więc nie może go zaewidencjonował.|
|SCC_E_CHECKINCONFLICT|Nie można wykonać checkin, ponieważ:<br /><br /> - Inny użytkownik sprawdził się `bAutoReconcile` z wyprzedzeniem i był fałszywy.<br /><br /> — lub —<br /><br /> - Nie można wykonać automatycznego scalania (na przykład, gdy pliki są binarne).|
|SCC_E_VERIFYMERGE|Plik został automatycznie scalony, ale nie został zaewidencjonowany w oczekiwaniu na weryfikację użytkownika.|
|SCC_E_FIXMERGE|Plik został automatycznie scalony, ale nie został zaewidencjonowany z powodu konfliktu scalania, który musi zostać rozwiązany ręcznie.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed zakończeniem.|
|SCC_I_RELOADFILE|Plik lub projekt musi zostać ponownie załadowany.|
|SCC_E_FILENOTEXIST|Nie znaleziono pliku lokalnego.|

## <a name="remarks"></a>Uwagi
 Komentarz dotyczy wszystkich zaewidencjonowanych plików. Argument komentarza może `null` być ciągiem, w którym to przypadku wtyczka kontroli źródła może monitować użytkownika o ciąg komentarza dla każdego pliku.

 Argument `fOptions` może mieć wartość flagi, `SCC_KEEP_CHECKEDOUT` aby wskazać zamiar użytkownika, aby zaewidencjonować plik i wyewidencjonować go ponownie.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki sterowania źródłem](../extensibility/source-control-plug-in-api-functions.md)
