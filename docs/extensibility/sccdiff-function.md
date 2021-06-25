---
description: Ta funkcja wyświetla (lub opcjonalnie po prostu sprawdza) różnice między bieżącym plikiem (na dysku lokalnym) i jego ostatnią wersją zaewidencjonowaną w systemie kontroli źródła.
title: SccDiff, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 484d8b5e988ede9b50099e3c0376f2c3afce8317
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904659"
---
# <a name="sccdiff-function"></a>Funkcja SccDiff
Ta funkcja wyświetla (lub opcjonalnie po prostu sprawdza) różnice między bieżącym plikiem (na dysku lokalnym) i jego ostatnią wersją zaewidencjonowaną w systemie kontroli źródła.

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

[in] Struktura kontekstu wtyczki kontroli źródła.

 Hwnd

[in] Dojście do okna IDE, które wtyczka kontroli źródła może używać jako elementu nadrzędnego dla wszystkich okien dialogowych, które zawiera.

 lpFileName

[in] Nazwa pliku, dla którego żądana jest różnica.

 Foptions

[in] Flagi poleceń. Zobacz uwagi, aby uzyskać szczegółowe informacje.

 pvOptions

[in] Opcje specyficzne dla wtyczki kontroli źródła.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła dla tej funkcji zwraca jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Kopia robocza i wersja serwera są identyczne.|
|SCC_I_FILESDIFFERS|Kopia robocza różni się od wersji w ramach kontroli źródła.|
|SCC_I_RELOADFILE|Należy ponownie załadować plik lub projekt.|
|SCC_E_FILENOTCONTROLLED|Plik nie jest pod kontrolą źródła.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_ACCESSFAILURE|Występuje problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub zdyskulacji. Zaleca się ponawianie próby.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd; nie uzyskano różnicy pliku.|
|SCC_E_FILENOTEXIST|Nie znaleziono pliku lokalnego.|

## <a name="remarks"></a>Uwagi
 Ta funkcja służy do dwóch różnych celów. Domyślnie wyświetla listę zmian w pliku. Wtyczka kontroli źródła otwiera własne okno w formacie, który wybierze, aby wyświetlić różnice między plikiem użytkownika na dysku a najnowszą wersją pliku w ramach kontroli źródła.

 Alternatywnie może być konieczne po prostu określenie, czy plik został zmieniony. Na przykład w środowisku IDE może być konieczne ustalenie, czy można bezpiecznie wyewidencjonować plik bez informowania użytkownika. W takim przypadku idee przekazuje `SCC_DIFF_CONTENTS` flagę . Wtyczka kontroli źródła musi sprawdzać plik na dysku (bajt po bajtach) względem pliku kontrolowanego przez źródło i zwracać wartość wskazującą, czy dwa pliki różnią się bez wyświetlania czegokolwiek użytkownikowi.

 Jako optymalizację wydajności wtyczka kontroli źródła może używać alternatywnej metody opartej na sumy kontrolnej lub znaczniku czasu zamiast porównania bajt po bajtach wywoływanego przez element : te formy porównywania są oczywiście szybsze, ale mniej `SCC_DIFF_CONTENTS` niezawodne. Nie wszystkie systemy kontroli źródła mogą obsługiwać te alternatywne metody porównania, a wtyczka może wymagać powrotu do porównania zawartości. Wszystkie wtyczki kontroli źródła muszą co najmniej obsługiwać porównanie zawartości.

> [!NOTE]
> Flagi szybkiej różnicy wzajemnie się wykluczają. Prawidłowe jest, aby przekazać żadnych flag, ale nie jest prawidłowa jednocześnie przekazać więcej niż jeden. `SCC_DIFF_QUICK_DIFF`, która jest maską łączącą wszystkie flagi, może służyć do testowania, ale nigdy nie powinna być przekazywana jako parametr.

|`fOption`|Znaczenie|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|Porównanie bez uwzględniania liter (może być używane do szybkiej lub wizualnej różnicy).|
|SCC_DIFF_IGNORESPACE|Ignoruje odstępy (może służyć do szybkiej lub wizualnej różnicy).|
|SCC_DIFF_QD_CONTENTS|Dyskretnie porównuje plik w bajtach.|
|SCC_DIFF_QD_CHECKSUM|Dyskretnie porównuje plik za pośrednictwem sumy kontrolnej, jeśli jest obsługiwana. Jeśli nie jest obsługiwana, powrót do porównania zawartości.|
|SCC_DIFF_QD_TIME|Dyskretnie porównuje plik za pośrednictwem znacznika czasu, jeśli jest obsługiwany. Jeśli nie jest obsługiwana, powrót do porównania zawartości.|

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-in-api-functions.md)
