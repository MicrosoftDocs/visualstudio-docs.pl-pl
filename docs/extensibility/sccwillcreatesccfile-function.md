---
title: Funkcja SccWillCreateSccFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ac7657258b79b2e53bee8138bc5b2728f618eac
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720116"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile, funkcja
Ta funkcja określa, czy wtyczka do kontroli źródła obsługuje tworzenie MSSCCPRJ. Plik SCC dla każdego z określonych plików.

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
 pContext

podczas Wskaźnik kontekstu wtyczki kontroli źródła.

 nFiles

podczas Liczba nazw plików zawartych w tablicy `lpFileNames`, a także Długość tablicy `pbSccFiles`.

 lpFileNames

podczas Tablica w pełni kwalifikowanych nazw plików do sprawdzenia (Tablica musi być przydzielone przez obiekt wywołujący).

 pbSccFiles

[in. out] Tablica, w której mają być przechowywane wyniki.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Prawnego.|
|SCC_E_INVALIDFILEPATH|Jedna ze ścieżek w tablicy jest nieprawidłowa.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Ta funkcja jest wywoływana z listą plików, aby określić, czy wtyczka do kontroli źródła zapewnia obsługę w MSSCCPRJ. Plik SCC dla każdego z podanych plików (Aby uzyskać więcej informacji na temat MSSCCPRJ. Plik SCC, zobacz [MSSCCPRJ. Plik SCC](../extensibility/mssccprj-scc-file.md)). Wtyczki kontroli źródła mogą zadeklarować, czy mają możliwość tworzenia MSSCCPRJ. Pliki SCC przez zadeklarowanie `SCC_CAP_SCCFILE` podczas inicjowania. Wtyczka zwraca `TRUE` lub `FALSE` na plik w tablicy `pbSccFiles`, aby wskazać, które z tych plików mają MSSCCPRJ. Obsługa SCC. Jeśli wtyczka zwraca kod sukcesu z funkcji, wartości w tablicy zwracanej są honorowane. W przypadku niepowodzenia tablica jest ignorowana.

## <a name="see-also"></a>Zobacz także
- [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)
- [Plik MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)