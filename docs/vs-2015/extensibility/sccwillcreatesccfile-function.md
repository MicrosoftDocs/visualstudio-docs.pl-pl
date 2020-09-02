---
title: Funkcja SccWillCreateSccFile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb0df475098a0fb0675327cece6dd9c643a0c4d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147960"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja określa, czy wtyczka do kontroli źródła obsługuje tworzenie MSSCCPRJ. Plik SCC dla każdego z określonych plików.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 podczas Liczba nazw plików zawartych w `lpFileNames` tablicy, a także długość `pbSccFiles` tablicy.  
  
 lpFileNames  
 podczas Tablica w pełni kwalifikowanych nazw plików do sprawdzenia (Tablica musi być przydzielone przez obiekt wywołujący).  
  
 pbSccFiles  
 [in. out] Tablica, w której mają być przechowywane wyniki.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Powodzenie.|  
|SCC_E_INVALIDFILEPATH|Jedna ze ścieżek w tablicy jest nieprawidłowa.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana z listą plików, aby określić, czy wtyczka do kontroli źródła zapewnia obsługę w MSSCCPRJ. Plik SCC dla każdego z podanych plików (Aby uzyskać więcej informacji na temat MSSCCPRJ. Plik SCC, zobacz [MSSCCPRJ. Plik SCC](../extensibility/mssccprj-scc-file.md)). Wtyczki kontroli źródła mogą zadeklarować, czy mają możliwość tworzenia MSSCCPRJ. Pliki SCC przez zadeklarowanie `SCC_CAP_SCCFILE` podczas inicjalizacji. Wtyczka zwraca `TRUE` lub `FALSE` na plik w `pbSccFiles` tablicy, aby wskazać, które z tych plików mają MSSCCPRJ. Obsługa SCC. Jeśli wtyczka zwraca kod sukcesu z funkcji, wartości w tablicy zwracanej są honorowane. W przypadku niepowodzenia tablica jest ignorowana.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Plik MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
