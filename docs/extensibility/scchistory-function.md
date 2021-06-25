---
description: Ta funkcja wyświetla historię określonych plików.
title: Funkcja SccHistory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1208bd0cb13661f1aa60bb9f97c9e4502e517e6d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902543"
---
# <a name="scchistory-function"></a>SccHistory, funkcja
Ta funkcja wyświetla historię określonych plików.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccHistory(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Parametry
 `pvContext`

[in] Struktura kontekstu wtyczki kontroli źródła.

 `hWnd`

[in] Dojście do okna IDE, które wtyczka kontroli źródła może używać jako elementu nadrzędnego dla wszystkich okien dialogowych, które zawiera.

 `nFiles`

[in] Liczba plików określona w `lpFileName` tablicy.

 `lpFileName`

[in] Tablica w pełni kwalifikowanych nazw plików.

 `fOptions`

[in] Flagi poleceń (obecnie nie są używane).

 `pvOptions`

[in] Opcje specyficzne dla wtyczki kontroli źródła.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła dla tej funkcji zwraca jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Historia wersji została pomyślnie uzyskana.|
|SCC_I_RELOADFILE|System kontroli źródła rzeczywiście zmodyfikował plik na dysku podczas pobierania historii (na przykład przez pobranie jego starej wersji), więc idee powinny ponownie załadować ten plik.|
|SCC_E_FILENOTCONTROLLED|Plik nie jest pod kontrolą źródła.|
|SCC_E_OPNOTSUPPORTED|System kontroli źródła nie obsługuje tej operacji.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_ACCESSFAILURE|Występuje problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub zdyskulacji. Zaleca się ponawianie próby.|
|SCC_E_PROJNOTOPEN|Projekt nie został otwarty.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd. Nie można uzyskać historii plików.|

## <a name="remarks"></a>Uwagi
 Wtyczka kontroli źródła może wyświetlać własne okno dialogowe, w których jest wyświetlana historia każdego pliku, przy użyciu elementu `hWnd` jako okna nadrzędnego. Alternatywnie można użyć opcjonalnej wyjściowej funkcji wywołania zwrotnego dostarczonej do [funkcji SccOpenProject,](../extensibility/sccopenproject-function.md) jeśli jest obsługiwana.

 Należy pamiętać, że w pewnych okolicznościach badanego pliku może ulec zmianie podczas wykonywania tego wywołania. Na przykład polecenie history daje użytkownikowi możliwość uzyskania [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] starej wersji pliku. W takim przypadku wtyczka kontroli źródła zwraca ostrzeżenie środowiska IDE o potrzebie `SCC_I_RELOAD` ponownego załadowania pliku.

> [!NOTE]
> Jeśli wtyczka kontroli źródła nie obsługuje tej funkcji dla tablicy plików, można wyświetlić tylko historię plików dla pierwszego pliku.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
