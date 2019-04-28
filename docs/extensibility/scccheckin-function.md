---
title: Funkcja SccCheckin | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 178cebb974147a95aac35ebabe484dc4a7777407
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62802996"
---
# <a name="scccheckin-function"></a>Funkcja SccCheckin
Ta funkcja sprawdza, czy wcześniej pobranych plików do systemu kontroli źródła, przechowywania zmian i tworzenie nowej wersji. Ta funkcja jest wywoływana z liczbą i tablicę nazw plików do wyewidencjonowania.

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

[in] Struktura kontekście wtyczki kontroli źródła.

 hWnd

[in] Uchwyt okna środowiska IDE, które SCC wtyczki mogą służyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.

 Niepowodzeń

[in] Liczba plików wybranych do wyewidencjonowania.

 lpFileNames

[in] Tablica nazw w pełni kwalifikowaną ścieżką lokalną plików do wyewidencjonowania.

 lpComment

[in] Komentarz, które mają być stosowane do każdego z wybranych plików, które zostały zaewidencjonowane. Ten parametr jest `NULL` Jeśli wtyczka do kontroli źródła, powinien zostać wyświetlony monit o komentarz.

 fOptions

[in] Command flag, albo 0 lub `SCC_KEEP_CHECKEDOUT`.

 pvOptions

[in] SCC plug-określonych opcji.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Plik został pomyślnie zaewidencjonowany.|
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie jest pod kontrolą kodu źródłowego.|
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji o zasoby. Ponowienie próby jest zalecane.|
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd. Plik nie została zaewidencjonowana.|
|SCC_E_NOTCHECKEDOUT|Użytkownik nie został wyewidencjonowany pliku, więc nie można sprawdzić.|
|SCC_E_CHECKINCONFLICT|Nie można wykonać zaewidencjonowania, ponieważ:<br /><br /> -Inny użytkownik zaewidencjonował wyprzedzeniem i `bAutoReconcile` była wartość false.<br /><br /> —lub—<br /><br /> Nie można wykonać automatyczne scalanie, (na przykład w przypadku plików binarnych).|
|SCC_E_VERIFYMERGE|Plik został scalony automatycznie, ale nie został zaewidencjonowany oczekiwania na weryfikację użytkownika.|
|SCC_E_FIXMERGE|Plik został scalony automatycznie, ale nie został zaewidencjonowany ze względu na konflikt scalania, które należy ręcznie rozwiązać.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|
|SCC_I_RELOADFILE|Pliku lub projektu wymaga ponownego załadowania.|
|SCC_E_FILENOTEXIST|Nie można odnaleźć pliku lokalnego.|

## <a name="remarks"></a>Uwagi
 Komentarza ma zastosowanie do wszystkich plików, które zostały zaewidencjonowane. Argument komentarz może być `null` ciągu, w którym to przypadku wtyczka do kontroli źródła może monitować użytkownika o ciąg komentarza dla każdego pliku.

 `fOptions` Wartość może być podany argument `SCC_KEEP_CHECKEDOUT` flagę wskazującą intencji użytkownika Zaewidencjonuj go i ponownie Sprawdź wprowadzone zmiany.

## <a name="see-also"></a>Zobacz także
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)