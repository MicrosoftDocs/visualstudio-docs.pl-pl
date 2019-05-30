---
title: Funkcja SccRemove | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 70413c2e446f8ed226a58eb8ddfe62ede4a1d61f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338621"
---
# <a name="sccremove-function"></a>SccRemove, funkcja
Ta funkcja usuwa pliki z systemu kontroli źródła.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccRemove(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Parametry
 pvContext

[in] Struktura kontekście wtyczki kontroli źródła.

 hWnd

[in] Uchwyt okna środowiska IDE, które wtyczka do kontroli źródła można użyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.

 Niepowodzeń

[in] Liczba plików określonych w `lpFileNames` tablicy.

 lpFileNames

[in] Tablica nazw w pełni kwalifikowaną ścieżką lokalną plików do usunięcia.

 lpComment

[in] Komentarz, które mają być stosowane do każdego pliku usuwany.

 fOptions

[in] Polecenie flagi (nieużywane).

 pvOptions

[in] Opcje plug-określonych kontroli źródła.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Usuwanie zakończyło się pomyślnie.|
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie jest pod kontrolą źródła.|
|SCC_E_OPNOTSUPPORTED|System kontroli źródła nie obsługuje tej operacji.|
|SCC_E_ISCHECKEDOUT|Nie można usunąć pliku, ponieważ użytkownik ma aktualnie jego wyewidencjonowania.|
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji o zasoby.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd; plik nie został usunięty.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|

## <a name="remarks"></a>Uwagi
 Ta funkcja usuwa pliki z systemu kontroli źródła, ale nie spowoduje usunięcia z lokalnym dysku twardym użytkownika.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)