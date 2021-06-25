---
description: Ta funkcja wyświetla właściwości kontroli źródła dla pliku lub projektu.
title: Funkcja SccProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cd50353ab29c05e5e5db2dc2b3f363af46ca8aa7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904194"
---
# <a name="sccproperties-function"></a>SccProperties, funkcja
Ta funkcja wyświetla właściwości kontroli źródła dla pliku lub projektu.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccProperties (
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName
);
```

#### <a name="parameters"></a>Parametry
 pvContext

[in] Struktura kontekstu wtyczki kontroli źródła.

 Hwnd

[in] Dojście do okna IDE, które wtyczka kontroli źródła może używać jako elementu nadrzędnego dla wszystkich okien dialogowych, które zawiera.

 lpFileName

[in] W pełni kwalifikowana nazwa ścieżki pliku lub projektu.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła dla tej funkcji zwraca jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Właściwości zostały pomyślnie wyświetlone.|
|SCC_I_RELOADFILE|System kontroli wersji zmodyfikował właściwości pliku, więc ide powinno ponownie załadować ten plik.|
|SCC_E_PROJNOTOPEN|Określony projekt nie został otwarty w kontroli źródła.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie ma autoryzacji do wyświetlania właściwości tego pliku lub projektu.|
|SCC_E_FILENOTCONTROLLED|Określony plik lub projekt nie jest pod kontrolą źródła.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Wystąpił nieznany lub ogólny błąd.|

## <a name="remarks"></a>Uwagi
 Wtyczka kontroli źródła wyświetla właściwości we własnym oknie dialogowym.

 Właściwości są definiowane przez wtyczkę kontroli źródła i mogą się różnić od wtyczki do wtyczki. Jeśli wtyczka umożliwia użytkownikowi zmianę właściwości kontroli źródła pliku, powinien zostać zwrócony sygnał środowiska IDE, że ten plik lub projekt musi zostać `SCC_I_RELOAD` ponownie załadowany.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
