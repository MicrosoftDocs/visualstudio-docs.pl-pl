---
title: Funkcja SccDiff | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b68df68ce7fa4ad5cbc98db256204ddf8623d2c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701020"
---
# <a name="sccdiff-function"></a>SccDiff, funkcja
Ta funkcja wyświetla (lub opcjonalnie tylko sprawdza) różnice między bieżącym plikiem (na dysku lokalnym) a jego ostatnią wersją zaewidencjonowanym w systemie kontroli źródła.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccDiff(
   LPVOID    pvContext,
   HWND      hWnd,
   LPCSTR    lpFileName,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametry
 pvContext

[w] Struktura kontekstu wtyczki formantu źródła.

 Hwnd

[w] Dojście do okna IDE, którego wtyczka formantu źródła może używać jako element nadrzędny dla wszystkich okien dialogowych, które udostępnia.

 lpFileName

[w] Nazwa pliku, dla którego żądana jest różnica.

 Foptions

[w] Flagi poleceń. Zobacz Uwagi, aby uzyskać szczegółowe informacje.

 pvOpcje

[w] Opcje specyficzne dla wtyczki sterowania źródłem.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Kopia robocza i wersja serwera są identyczne.|
|SCC_I_FILESDIFFERS|Kopia robocza różni się od wersji pod kontrolą źródła.|
|SCC_I_RELOADFILE|Plik lub projekt musi zostać ponownie załadowany.|
|SCC_E_FILENOTCONTROLLED|Plik nie jest pod kontrolą źródła.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zaleca się ponowną próbę.|
|SCC_E_NONSPECIFICERROR|Niespecyficzna awaria; nie uzyskano różnicy w pliku.|
|SCC_E_FILENOTEXIST|Nie znaleziono pliku lokalnego.|

## <a name="remarks"></a>Uwagi
 Ta funkcja służy dwóm różnym celom. Domyślnie wyświetla listę zmian w pliku. Wtyczka kontroli źródła otwiera własne okno, w dowolnym formacie, aby wyświetlić różnice między plikiem użytkownika na dysku a najnowszą wersją pliku pod kontrolą źródła.

 Alternatywnie IDE może po prostu trzeba określić, czy plik został zmieniony. Na przykład IDE może być konieczne określenie, czy jest bezpieczne wyewidencjonowanie pliku bez informowania użytkownika. W takim przypadku IDE przechodzi `SCC_DIFF_CONTENTS` w flagę. Wtyczka kontroli źródła musi sprawdzić plik na dysku, bajt po bajcie, w stosunku do pliku kontrolowanego przez źródło i zwrócić wartość wskazującą, czy dwa pliki są różne bez wyświetlania czegokolwiek użytkownikowi.

 Jako optymalizacja wydajności wtyczka kontroli źródła może użyć alternatywy opartej na sumie kontrolnej lub sygnatury `SCC_DIFF_CONTENTS`czasowej zamiast porównania bajtów po bajcie, do którego wezwano: te formy porównania są oczywiście szybsze, ale mniej niezawodne. Nie wszystkie systemy kontroli źródła mogą obsługiwać te alternatywne metody porównywania, a wtyczka może być musiała wrócić do porównania zawartości. Wszystkie wtyczki kontroli źródła muszą co najmniej obsługiwać porównanie zawartości.

> [!NOTE]
> Flagi szybkiej różnicy wzajemnie się wykluczają. Jest prawidłowy, aby przekazać żadnych flag, ale nie jest prawidłowe, aby jednocześnie przekazać więcej niż jeden. `SCC_DIFF_QUICK_DIFF`, który jest maską, która łączy wszystkie flagi, może służyć do testowania, ale nigdy nie powinny być przekazywane jako parametr.

|`fOption`|Znaczenie|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|Porównanie bez uwzględniania wielkości liter (może być używane do szybkiej lub wizualnej różnicy).|
|SCC_DIFF_IGNORESPACE|Ignoruje odstępy (mogą być używane do szybkiej lub wizualnej różnicy).|
|SCC_DIFF_QD_CONTENTS|Po dyskretny porównuje plik, bajt po bajcie.|
|SCC_DIFF_QD_CHECKSUM|Po cichu porównuje plik za pomocą sumy kontrolnej, gdy jest obsługiwany. Jeśli nie jest obsługiwany, wraca do porównania zawartości.|
|SCC_DIFF_QD_TIME|Po cichu porównuje plik za pomocą sygnatury czasowej, gdy jest obsługiwany. Jeśli nie jest obsługiwany, wraca do porównania zawartości.|

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki sterowania źródłem](../extensibility/source-control-plug-in-api-functions.md)
