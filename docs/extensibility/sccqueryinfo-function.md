---
title: Funkcja SccQueryInfo | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1efae18f15588f4dacf3409ea95e30af05397c6e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700480"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo, funkcja
Ta funkcja uzyskuje informacje o stanie zestawu wybranych plików pod kontrolą źródła.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccQueryInfo(
   LPVOID  pvContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPLONG  lpStatus
);
```

#### <a name="parameters"></a>Parametry
 pvContext

[w] Struktura kontekstu wtyczki formantu źródła.

 nFiles

[w] Liczba plików określonych `lpFileNames` w tablicy i `lpStatus` długość tablicy.

 lpFileNames

[w] Tablica nazw plików, które mają być wyszukiwane.

 lpStatus

[w, na zewnątrz] Tablica, w której wtyczka kontroli źródła zwraca flagi stanu dla każdego pliku. Aby uzyskać więcej informacji, zobacz [Kod stanu pliku](../extensibility/file-status-code-enumerator.md).

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Kwerenda zakończyła się pomyślnie.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z dostępem do systemu kontroli źródła, prawdopodobnie spowodowany problemami z siecią lub rywalizacją. Zaleca się ponowną próbę.|
|SCC_E_PROJNOTOPEN|Projekt nie jest otwarty pod kontrolą źródła.|
|SCC_E_NONSPECIFICERROR|Niespecyficzna awaria.|

## <a name="remarks"></a>Uwagi
 Jeśli `lpFileName` jest pusty ciąg, obecnie nie ma żadnych informacji o stanie do aktualizacji. W przeciwnym razie jest to pełna nazwa ścieżki pliku, dla którego informacje o stanie mogły ulec zmianie.

 Tablica zwracana może być `SCC_STATUS_xxxx` maską bitową bitów. Aby uzyskać więcej informacji, zobacz [Kod stanu pliku](../extensibility/file-status-code-enumerator.md). System kontroli źródła może nie obsługiwać wszystkich typów bitów. Na przykład, `SCC_STATUS_OUTOFDATE` jeśli nie jest oferowana, bit jest po prostu nie jest ustawiony.

 Korzystając z tej funkcji do wyewidencjonowywać pliki, należy zwrócić uwagę na następujące `MSSCCI` wymagania dotyczące stanu:

- `SCC_STATUS_OUTBYUSER`jest ustawiana, gdy bieżący użytkownik wyewidencjonował plik.

- `SCC_STATUS_CHECKEDOUT`nie można `SCC_STATUS_OUTBYUSER` ustawić, chyba że jest ustawiona.

- `SCC_STATUS_CHECKEDOUT`jest ustawiana tylko wtedy, gdy plik jest wyewidencjonowany do wyznaczonego katalogu roboczego.

- Jeśli plik jest wyewidencjonowany przez bieżącego użytkownika do `SCC_STATUS_OUTBYUSER` katalogu innego `SCC_STATUS_CHECKEDOUT` niż katalog roboczy, jest ustawiony, ale nie jest.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [Kod stanu pliku](../extensibility/file-status-code-enumerator.md)
