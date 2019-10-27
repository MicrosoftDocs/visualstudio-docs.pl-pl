---
title: Funkcja SccHistory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0ce0b38b8e602688875549edbac671e664809482
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721241"
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

podczas Struktura kontekstu wtyczki kontroli źródła.

 `hWnd`

podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.

 `nFiles`

podczas Liczba plików określona w tablicy `lpFileName`.

 `lpFileName`

podczas Tablica w pełni kwalifikowanych nazw plików.

 `fOptions`

podczas Flagi poleceń (obecnie nie są używane).

 `pvOptions`

podczas Opcje dotyczące wtyczki kontroli źródła.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Pomyślnie uzyskano historię wersji.|
|SCC_I_RELOADFILE|System kontroli źródła rzeczywiście zmodyfikował plik na dysku podczas pobierania historii (na przykład przez uzyskanie starej wersji), dlatego IDE powinien ponownie załadować ten plik.|
|SCC_E_FILENOTCONTROLLED|Plik nie znajduje się pod kontrolą źródła.|
|SCC_E_OPNOTSUPPORTED|System kontroli źródła nie obsługuje tej operacji.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zalecana jest ponowna próba.|
|SCC_E_PROJNOTOPEN|Projekt nie został otwarty.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd. Nie można uzyskać historii plików.|

## <a name="remarks"></a>Uwagi
 Wtyczka do kontroli źródła może wyświetlić własne okno dialogowe, aby pokazać historię każdego pliku przy użyciu `hWnd` jako okna nadrzędnego. Alternatywnie można użyć opcjonalnej wyjściowej funkcji wywołania zwrotnego tekstu dostarczonej do [SccOpenProject](../extensibility/sccopenproject-function.md) , jeśli jest ona obsługiwana.

 Należy zauważyć, że w pewnych okolicznościach sprawdzany plik może ulec zmianie podczas wykonywania tego wywołania. Na przykład polecenie History [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] umożliwia użytkownikowi uzyskanie starej wersji pliku. W takim przypadku wtyczka do kontroli źródła zwraca `SCC_I_RELOAD`, aby ostrzec środowisko IDE wymagane do ponownego załadowania pliku.

> [!NOTE]
> Jeśli wtyczka kontroli źródła nie obsługuje tej funkcji dla tablicy plików, można wyświetlić tylko historię plików dla pierwszego pliku.

## <a name="see-also"></a>Zobacz także
- [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)