---
description: Ta funkcja zmienia nazwę pliku w systemie kontroli źródła.
title: SccRename, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fb3fa392cd4ed31d907fe5913f8d7965a20df05b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900463"
---
# <a name="sccrename-function"></a>SccRename, funkcja
Ta funkcja zmienia nazwę pliku w systemie kontroli źródła.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccRename(
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName,
   LPCSTR lpNewName
);
```

#### <a name="parameters"></a>Parametry
 pvContext

[in] Struktura kontekstu wtyczki kontroli źródła.

 Hwnd

[in] Dojście do okna IDE, które wtyczka kontroli źródła może używać jako elementu nadrzędnego dla wszystkich okien dialogowych, które udostępnia.

 lpFileName

[in] W pełni kwalifikowana nazwa pliku, który jest zmieniany.

 lpNewName (Nazwa lpNewName)

[in] W pełni kwalifikowana nowa nazwa. Jeśli ścieżka katalogu jest inna, plik został przeniesiony z jednego podkatalogu do innego.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła dla tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Operacja zmiany nazwy została ukończona pomyślnie.|
|SCC_E_PROJNOTOPEN|Projekt nie jest otwarty pod kontrolą źródła.|
|SCC_E_FILENOTCONTROLLED|Plik nie jest pod kontrolą źródła.|
|SCC_E_ACCESSFAILURE|Występuje problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub zdyskulacji.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie ma autoryzacji do ukończenia tej operacji.|
|SCC_E_COULDNOTCREATEPROJECT|Nie można utworzyć projektu w ramach procesu zmiany nazwy.|
|SCC_E_OPNOTPERFORMED|Operacja nie została wykonana.|
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony lub ogólny błąd.|

## <a name="remarks"></a>Uwagi
 Ta funkcja może służyć do zmiany nazwy pliku lub przenoszenia go z jednej lokalizacji do innej w systemie kontroli źródła. Wtyczka kontroli źródła nie powinna próbować uzyskać dostępu do pliku na dysku. Zmiana nazwy pliku lokalnego należy do obowiązków środowiska IDE.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
