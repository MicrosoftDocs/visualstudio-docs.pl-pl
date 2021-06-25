---
description: Ta funkcja sprawdza wcześniej wyewidencjonowane pliki w systemie kontroli źródła, zapisując zmiany i tworząc nową wersję.
title: SccCheckin, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d324c03096df5178decd6f6954928df3f2c6b9aa
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904750"
---
# <a name="scccheckin-function"></a>SccCheckin, funkcja
Ta funkcja sprawdza wcześniej wyewidencjonowane pliki w systemie kontroli źródła, zapisując zmiany i tworząc nową wersję. Ta funkcja jest wywoływana z licznikiem i tablicą nazw plików do zaewidencjonowania.

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

[in] Struktura kontekstu wtyczki kontroli źródła.

 Hwnd

[in] Dojście do okna IDE, które wtyczka SCC może używać jako elementu nadrzędnego dla wszystkich okien dialogowych, które zawiera.

 nFiles

[in] Liczba plików wybranych do zaewidencjonowania.

 lpFileNames

[in] Tablica w pełni kwalifikowanych nazw ścieżek lokalnych plików do zaewidencjonowania.

 lpComment

[in] Komentarz do zastosowania do każdego z zaznaczonych plików, które są zaewidencjonowane. Ten parametr ma wartość , jeśli wtyczka kontroli `NULL` źródła powinna monitować o komentarz.

 Foptions

[in] Flagi poleceń: 0 lub `SCC_KEEP_CHECKEDOUT` .

 pvOptions

[in] Opcje specyficzne dla wtyczki SCC.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła dla tej funkcji zwraca jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Plik został pomyślnie zaewidencjonowany.|
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie jest pod kontrolą kodu źródłowego.|
|SCC_E_ACCESSFAILURE|Występuje problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub z powodu wystąpienia problemów z siecią. Zaleca się ponawianie próby.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd. Plik nie został zaewidencjonowany.|
|SCC_E_NOTCHECKEDOUT|Użytkownik nie wyewidencjonował pliku, więc nie może go zaewidencjonować.|
|SCC_E_CHECKINCONFLICT|Nie można wykonać zaewidencji, ponieważ:<br /><br /> — Inny użytkownik zaewidencjonował się wcześniej i `bAutoReconcile` miał wartość false.<br /><br /> -lub-<br /><br /> - Nie można wykonać automatycznego scalania (na przykład gdy pliki są binarne).|
|SCC_E_VERIFYMERGE|Plik został automatycznie scalony, ale nie został zaewidencjonowany w oczekiwaniu na weryfikację użytkownika.|
|SCC_E_FIXMERGE|Plik został automatycznie scalony, ale nie został zaewidencjonowany z powodu konfliktu scalania, który musi zostać rozwiązany ręcznie.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed zakończeniem.|
|SCC_I_RELOADFILE|Należy ponownie załadować plik lub projekt.|
|SCC_E_FILENOTEXIST|Nie znaleziono pliku lokalnego.|

## <a name="remarks"></a>Uwagi
 Komentarz dotyczy wszystkich plików, które są zaewidencjonowane. Argument komentarza może być ciągiem. W takim przypadku wtyczka kontroli źródła może monitować użytkownika o ciąg komentarza `null` dla każdego pliku.

 Argumentowi można nadawać wartość flagi , aby wskazać intencję użytkownika, aby zaewidencjonić plik i `fOptions` `SCC_KEEP_CHECKEDOUT` sprawdzić go ponownie.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-in-api-functions.md)
