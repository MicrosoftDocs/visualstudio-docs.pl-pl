---
title: Funkcja SccWillCreateSccFile | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0694fd6b4ba82faf8b05354765fc5734efe2ef4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700209"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile, funkcja
Ta funkcja określa, czy wtyczka kontroli źródła obsługuje tworzenie MSSCCPRJ. SCC dla każdego z podanych plików.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccWillCreateSccFile(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPBOOL  pbSccFiles
);
```

#### <a name="parameters"></a>Parametry
 Pcontext

[w] Wskaźnik kontekstu wtyczki formantu źródła.

 nFiles

[w] Liczba nazw plików zawartych `lpFileNames` w tablicy, a `pbSccFiles` także długość tablicy.

 lpFileNames

[w] Tablica w pełni kwalifikowanych nazw plików do sprawdzenia (tablica musi być przydzielona przez wywołującego).

 pbSccFiles (Pliki pbScc)

[w, na zewnątrz] Tablica, w której mają być przechowywane wyniki.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Powodzenie.|
|SCC_E_INVALIDFILEPATH|Jedna ze ścieżek w tablicy jest nieprawidłowa.|
|SCC_E_NONSPECIFICERROR|Niespecyficzna awaria.|

## <a name="remarks"></a>Uwagi
 Ta funkcja jest wywoływana z listą plików, aby ustalić, czy wtyczka kontroli źródła zapewnia obsługę w MSSCCPRJ. SCC dla każdego z podanych plików (więcej informacji na temat MSSCCPRJ. SCC, zobacz [MSSCCPRJ. SCC ).](../extensibility/mssccprj-scc-file.md) Wtyczki kontroli źródła można zadeklarować, czy mają możliwość tworzenia MSSCCPRJ. pliki SCC, `SCC_CAP_SCCFILE` deklarując podczas inicjowania. Wtyczka zwraca `TRUE` lub `FALSE` na plik `pbSccFiles` w tablicy, aby wskazać, które z danych plików mają MSSCCPRJ. Wsparcie SCC. Jeśli dodatek zwraca kod sukcesu z funkcji, wartości w tablicy zwracanej są honorowane. W przypadku awarii tablica jest ignorowana.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [Plik MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
