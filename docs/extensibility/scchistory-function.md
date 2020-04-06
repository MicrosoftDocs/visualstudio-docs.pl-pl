---
title: Funkcja SccHistory | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 734afefd97e61867076d487acbcf67f10f54e672
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700661"
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

[w] Struktura kontekstu wtyczki formantu źródła.

 `hWnd`

[w] Dojście do okna IDE, którego wtyczka formantu źródła może używać jako element nadrzędny dla wszystkich okien dialogowych, które udostępnia.

 `nFiles`

[w] Liczba plików określonych `lpFileName` w tablicy.

 `lpFileName`

[w] Tablica w pełni kwalifikowanych nazw plików.

 `fOptions`

[w] Flagi poleceń (obecnie nie używane).

 `pvOptions`

[w] Opcje specyficzne dla wtyczki sterowania źródłem.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Historia wersji została pomyślnie uzyskana.|
|SCC_I_RELOADFILE|System kontroli źródła faktycznie zmodyfikował plik na dysku podczas pobierania historii (na przykład przez uzyskanie starej jego wersji), więc IDE powinien ponownie załadować ten plik.|
|SCC_E_FILENOTCONTROLLED|Plik nie jest pod kontrolą źródła.|
|SCC_E_OPNOTSUPPORTED|System kontroli źródła nie obsługuje tej operacji.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zaleca się ponowną próbę.|
|SCC_E_PROJNOTOPEN|Projekt nie został otwarty.|
|SCC_E_NONSPECIFICERROR|Niespecyficzna awaria. Nie można uzyskać historii plików.|

## <a name="remarks"></a>Uwagi
 Wtyczka formantu źródła może wyświetlać własne okno dialogowe, `hWnd` aby wyświetlić historię każdego pliku, używając jako okna nadrzędnego. Alternatywnie można użyć opcjonalnej funkcji wywołania zwrotnego wyjściowego tekstu dostarczonej do [SccOpenProject,](../extensibility/sccopenproject-function.md) jeśli jest obsługiwana.

 Należy zauważyć, że w pewnych okolicznościach plik badane może ulec zmianie podczas wykonywania tego wywołania. Na przykład [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] polecenie historia daje użytkownikowi szansę na uzyskanie starej wersji pliku. W takim przypadku wtyczka kontroli źródła `SCC_I_RELOAD` zwraca, aby ostrzec IDE, że musi ponownie załadować plik.

> [!NOTE]
> Jeśli wtyczka formantu źródła nie obsługuje tej funkcji dla tablicy plików, można wyświetlić tylko historię plików dla pierwszego pliku.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
