---
title: Funkcja SccDiff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ff2b2d5e5a0043cde17fecd2d59c084d2958e32
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943117"
---
# <a name="sccdiff-function"></a>SccDiff, funkcja
Ta funkcja wyświetla (lub opcjonalnie sprawdza) różnice między bieżącym plikiem (na dysku lokalnym) i jego ostatnią wersją zaewidencjonowania w systemie kontroli źródła.

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

podczas Struktura kontekstu wtyczki kontroli źródła.

 Właściwość

podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.

 lpFileName

podczas Nazwa pliku, dla którego wymagana jest różnica.

 fOptions

podczas Flagi poleceń. Aby uzyskać szczegółowe informacje, zobacz uwagi.

 pvOptions

podczas Opcje dotyczące wtyczki kontroli źródła.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Kopia robocza i wersja serwera są identyczne.|
|SCC_I_FILESDIFFERS|Kopia robocza różni się od wersji pod kontrolą źródła.|
|SCC_I_RELOADFILE|Plik lub projekt musi zostać ponownie załadowany.|
|SCC_E_FILENOTCONTROLLED|Plik nie znajduje się pod kontrolą źródła.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zalecana jest ponowna próba.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd; nie uzyskano różnicy plików.|
|SCC_E_FILENOTEXIST|Nie znaleziono pliku lokalnego.|

## <a name="remarks"></a>Uwagi
 Ta funkcja służy do dwóch różnych celów. Domyślnie zostanie wyświetlona lista zmian w pliku. Wtyczka do kontroli źródła otwiera własne okno w dowolnym formacie, aby wyświetlić różnice między plikiem użytkownika na dysku a najnowszą wersją pliku pod kontrolą źródła.

 Alternatywnie środowisko IDE może po prostu określić, czy plik został zmieniony. Na przykład środowisko IDE może wymagać określenia, czy jest bezpiecznie do wyewidencjonowania pliku bez poinformowania użytkownika. W takim przypadku IDE przekazuje `SCC_DIFF_CONTENTS` flagę. Wtyczka do kontroli źródła musi sprawdzać plik na dysku, bajty w bajtach, w odniesieniu do pliku kontrolowanego przez źródło i zwracać wartość wskazującą, czy te dwa pliki są inne, bez wyświetlania niczego dla użytkownika.

 W ramach optymalizacji wydajności wtyczka do kontroli źródła może użyć alternatywy opartej na sumie kontrolnej lub sygnatury czasowej, a nie w porównaniu typu Byte-to-Byte wywoływanej przez `SCC_DIFF_CONTENTS` : te formy porównania są oczywiście szybsze, ale mniej niezawodne. Nie wszystkie systemy kontroli źródła mogą obsługiwać te alternatywne metody porównywania, a wtyczka może być powracać do porównania zawartości. Wszystkie wtyczki kontroli źródła muszą być co najmniej obsługiwane w porównaniu z zawartością.

> [!NOTE]
> Flagi szybkiej różnicy wykluczają się wzajemnie. Nie można przekazać żadnych flag, ale nie może być jednocześnie przekazana więcej niż jeden. `SCC_DIFF_QUICK_DIFF`, która jest maską, która łączy wszystkie flagi, może służyć do testowania, ale nigdy nie powinna być przenoszona jako parametr.

|`fOption`|Znaczenie|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|Porównanie bez uwzględniania wielkości liter (może być używane w przypadku różnic krótkich lub wizualnych).|
|SCC_DIFF_IGNORESPACE|Ignoruje biały znak (może być używany dla różnicy krótkiej lub wizualnej).|
|SCC_DIFF_QD_CONTENTS|Dyskretnie porównuje plik, bajt według bajtu.|
|SCC_DIFF_QD_CHECKSUM|Jeśli jest obsługiwana, dyskretnie porównuje plik przez sumę kontrolną. Jeśli nie jest obsługiwana, powraca do porównania zawartości.|
|SCC_DIFF_QD_TIME|W trybie dyskretnym porównuje plik za pośrednictwem sygnatury czasowej, jeśli jest obsługiwany. Jeśli nie jest obsługiwana, powraca do porównania zawartości.|

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
