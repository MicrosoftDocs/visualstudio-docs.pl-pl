---
description: Ta funkcja uzyskuje informacje o stanie zestawu wybranych plików pod kontrolą źródła.
title: Funkcja SccQueryInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 911219605859025f1877d040b5932714b10f836a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073901"
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

podczas Struktura kontekstu wtyczki kontroli źródła.

 nFiles

podczas Liczba plików określona w `lpFileNames` tablicy i długość `lpStatus` tablicy.

 lpFileNames

podczas Tablica nazw plików, do których mają być wysyłane zapytania.

 lpStatus

[in. out] Tablica, w której wtyczka do kontroli źródła zwraca flagi stanu dla każdego pliku. Aby uzyskać więcej informacji, zobacz [kod stanu pliku](../extensibility/file-status-code-enumerator.md).

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Zapytanie zostało wykonane pomyślnie.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie spowodowany przez problemy z siecią lub rywalizacją. Zalecana jest ponowna próba.|
|SCC_E_PROJNOTOPEN|Projekt nie jest otwarty w kontroli źródła.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Jeśli `lpFileName` jest pustym ciągiem, nie ma obecnie informacji o stanie do zaktualizowania. W przeciwnym razie jest to pełna nazwa ścieżki pliku, dla którego mogą ulec zmianie informacje o stanie.

 Tablica zwracana może być maską bitową `SCC_STATUS_xxxx` bitów. Aby uzyskać więcej informacji, zobacz [kod stanu pliku](../extensibility/file-status-code-enumerator.md). System kontroli źródła może nie obsługiwać wszystkich typów bitowych. Na przykład jeśli `SCC_STATUS_OUTOFDATE` nie jest oferowana, bit nie jest ustawiony.

 W przypadku używania tej funkcji do wyewidencjonowania plików należy pamiętać o następujących `MSSCCI` wymaganiach dotyczących stanu:

- `SCC_STATUS_OUTBYUSER` jest ustawiany, gdy bieżący użytkownik wyewidencjonuje plik.

- `SCC_STATUS_CHECKEDOUT` nie można ustawić, chyba że `SCC_STATUS_OUTBYUSER` jest ustawiony.

- `SCC_STATUS_CHECKEDOUT` jest ustawiana tylko wtedy, gdy plik jest wyewidencjonowany do wyznaczonych katalogów roboczych.

- Jeśli plik jest wyewidencjonowany przez bieżącego użytkownika do katalogu innego niż katalog roboczy, `SCC_STATUS_OUTBYUSER` jest ustawiony, ale `SCC_STATUS_CHECKEDOUT` nie jest.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [Kod stanu pliku](../extensibility/file-status-code-enumerator.md)
