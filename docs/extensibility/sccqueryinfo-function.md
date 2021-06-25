---
description: Ta funkcja uzyskuje informacje o stanie dla zestawu wybranych plików w ramach kontroli źródła.
title: SccQueryInfo, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 369bbd8d783e5d33ea1519b7ad8a4a37476dc62b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904142"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo, funkcja
Ta funkcja uzyskuje informacje o stanie dla zestawu wybranych plików w ramach kontroli źródła.

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

[in] Struktura kontekstu wtyczki kontroli źródła.

 nFiles

[in] Liczba plików określonych w tablicy i `lpFileNames` długość `lpStatus` tablicy.

 lpFileNames

[in] Tablica nazw plików do zapytania.

 lpStatus

[in, out] Tablica, w której wtyczka kontroli kodu źródłowego zwraca flagi stanu dla każdego pliku. Aby uzyskać więcej informacji, zobacz [Kod stanu pliku](../extensibility/file-status-code-enumerator.md).

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła dla tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Zapytanie powiodło się.|
|SCC_E_ACCESSFAILURE|Występuje problem z dostępem do systemu kontroli kodu źródłowego, prawdopodobnie spowodowany problemami z siecią lub kontrą. Zaleca się ponawianie próby.|
|SCC_E_PROJNOTOPEN|Projekt nie jest otwarty pod kontrolą źródła.|
|SCC_E_NONSPECIFICERROR|Nieokreślona awaria.|

## <a name="remarks"></a>Uwagi
 Jeśli `lpFileName` ciąg jest pusty, obecnie nie ma żadnych informacji o stanie do zaktualizowania. W przeciwnym razie jest to pełna nazwa ścieżki pliku, dla którego informacje o stanie mogą ulec zmianie.

 Tablica zwracana może być maski `SCC_STATUS_xxxx` bitów. Aby uzyskać więcej informacji, zobacz [Kod stanu pliku](../extensibility/file-status-code-enumerator.md). System kontroli źródła może nie obsługiwać wszystkich typów bitów. Na przykład jeśli `SCC_STATUS_OUTOFDATE` bit nie jest oferowany, bit po prostu nie jest ustawiony.

 W przypadku korzystania z tej funkcji do wyewidencjoniania plików należy pamiętać o następujących `MSSCCI` wymaganiach dotyczących stanu:

- `SCC_STATUS_OUTBYUSER` jest ustawiany, gdy bieżący użytkownik wyewidencjonował plik.

- `SCC_STATUS_CHECKEDOUT` Nie można ustawić, chyba `SCC_STATUS_OUTBYUSER` że jest ustawiona.

- `SCC_STATUS_CHECKEDOUT` jest ustawiany tylko wtedy, gdy plik jest wyewidencjonowany do wyznaczonego katalogu roboczego.

- Jeśli plik jest wyewidencjonowany przez bieżącego użytkownika do katalogu innego niż katalog roboczy, jest `SCC_STATUS_OUTBYUSER` ustawiony, ale `SCC_STATUS_CHECKEDOUT` nie.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [Kod stanu pliku](../extensibility/file-status-code-enumerator.md)
