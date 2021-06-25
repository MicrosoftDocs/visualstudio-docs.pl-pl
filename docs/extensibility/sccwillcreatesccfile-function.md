---
description: Ta funkcja określa, czy wtyczka kontroli źródła obsługuje tworzenie pliku MSSCCPRJ. Plik SCC dla każdego z podanych plików.
title: SccWillCreateSccFile, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9f9e6df29b9f44d852c7c84488a3febf590fcc0e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900450"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile, funkcja
Ta funkcja określa, czy wtyczka kontroli źródła obsługuje tworzenie pliku MSSCCPRJ. Plik SCC dla każdego z podanych plików.

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

[in] Wskaźnik kontekstu wtyczki kontroli źródła.

 nFiles

[in] Liczba nazw plików zawartych w `lpFileNames` tablicy, a także długość `pbSccFiles` tablicy.

 lpFileNames

[in] Tablica w pełni kwalifikowanych nazw plików do sprawdzenia (tablica musi zostać przydzielona przez element wywołujący).

 pbSccFiles

[in, out] Tablica, w której mają być przechowywane wyniki.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła dla tej funkcji zwraca jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Powodzenie.|
|SCC_E_INVALIDFILEPATH|Jedna ze ścieżek w tablicy jest nieprawidłowa.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Ta funkcja jest wywoływana z listą plików, aby określić, czy wtyczka kontroli źródła zapewnia obsługę w mssccprj. Plik SCC dla każdego z podanych plików (aby uzyskać więcej informacji na temat msSCCPRJ. SCC, zobacz [MSSCCPRJ. Plik SCC](../extensibility/mssccprj-scc-file.md)). Wtyczki kontroli źródła mogą deklarować, czy mogą tworzyć pliki MSSCCPRJ. Pliki SCC przez deklarowanie `SCC_CAP_SCCFILE` podczas inicjowania. Wtyczka zwraca wartość lub dla każdego pliku w tablicy, aby wskazać, które `TRUE` z danych plików mają wartość `FALSE` `pbSccFiles` MSSCCPRJ. Obsługa SCC. Jeśli wtyczka zwraca kod powodzenia z funkcji , wartości w tablicy zwracanych wartości są honorowane. W przypadku awarii tablica jest ignorowana.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [Plik MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
