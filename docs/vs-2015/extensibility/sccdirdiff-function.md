---
title: Funkcja SccDirDiff | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 81279e0fdb0df6600686adc57bb1c5489e8e7aab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64780820"
---
# <a name="sccdirdiff-function"></a>SccDirDiff, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja wyświetla różnice między bieżącym katalogiem lokalnym na dysku klienta i odpowiednim projektem pod kontrolą źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 podczas Struktura kontekstu wtyczki kontroli źródła.  
  
 Właściwość  
 podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.  
  
 lpDirName  
 podczas W pełni kwalifikowana ścieżka do katalogu lokalnego, dla którego ma zostać wyświetlona różnica wizualna.  
  
 flagiDW  
 podczas Flagi poleceń (patrz sekcja uwagi).  
  
 pvOptions  
 podczas Opcje dotyczące wtyczki kontroli źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Katalog na dysku jest taki sam jak projekt w kontroli kodu źródłowego.|  
|SCC_I_FILESDIFFER|Katalog na dysku różni się od projektu w kontroli kodu źródłowego.|  
|SCC_I_RELOADFILE|Plik lub projekt musi zostać ponownie załadowany.|  
|SCC_E_FILENOTCONTROLLED|Katalog nie znajduje się pod kontrolą kodu źródłowego.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zalecana jest ponowna próba.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nieokreślony błąd.|  
|SCC_E_FILENOTEXIST|Nie można znaleźć katalogu lokalnego.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja służy do nakazuje wtyczki kontroli źródła, aby wyświetlić użytkownikowi listę zmian w określonym katalogu. Wtyczka otwiera własne okno w wybranym formacie, aby wyświetlić różnice między katalogiem użytkownika na dysku i odpowiednim projektem w kontroli wersji.  
  
 Jeśli wtyczka obsługuje porównanie katalogów, musi obsługiwać porównanie katalogów na podstawie nazwy pliku, nawet jeśli opcje "szybkiej diff" nie są obsługiwane.  
  
|`dwFlags`|Interpretacja|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|Porównanie bez uwzględniania wielkości liter (może być używane w przypadku szybkiej Diffie lub wizualizacji).|  
|SCC_DIFF_IGNORESPACE|Ignoruje biały znak (może być używany w przypadku opcji Quick-diff lub wizualny).|  
|SCC_DIFF_QD_CONTENTS|Jeśli jest obsługiwana przez wtyczkę kontroli źródła, dyskretnie porównuje katalog, bajt według bajtu.|  
|SCC_DIFF_QD_CHECKSUM|Jeśli jest to obsługiwane przez wtyczkę, dyskretnie porównuje katalog za pośrednictwem sumy kontrolnej lub, jeśli nie jest obsługiwany, powraca do SCC_DIFF_QD_CONTENTS.|  
|SCC_DIFF_QD_TIME|Jeśli jest to obsługiwane przez wtyczkę, dyskretnie porównuje katalog za pośrednictwem sygnatury czasowej lub, jeśli nie jest obsługiwany, powraca do SCC_DIFF_QD_CHECKSUM lub SCC_DIFF_QD_CONTENTS.|  
  
> [!NOTE]
> Ta funkcja używa tych samych flag poleceń co [SccDiff](../extensibility/sccdiff-function.md). Jednakże wtyczka do kontroli źródła może nie obsługiwać operacji "szybkiej diff" dla katalogów.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
