---
title: Funkcja SccDirDiff | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 86169e52a4965fae785fcda224f91318a02920b5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005608"
---
# <a name="sccdirdiff-function"></a>Funkcja SccDirDiff
Funkcja ta wyświetla różnice między bieżącym katalogu lokalnym na dysku klienta i odpowiedniego projektu objętego kontrolą źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
### <a name="parameters"></a>Parametry  
 pContext  
 [in] Struktura kontekście wtyczki kontroli źródła.  
  
 hWnd  
 [in] Uchwyt okna środowiska IDE, które wtyczka do kontroli źródła można użyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.  
  
 lpDirName  
 [in] W pełni kwalifikowana ścieżka do katalogu lokalnego, dla których chcesz wyświetlić różnica visual.  
  
 Flagidw  
 [in] Polecenie flagi (zobacz uwagi sekcji).  
  
 pvOptions  
 [in] Opcje plug-określonych kontroli źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Katalogu na dysku jest taka sama jak projekt w kontroli kodu źródłowego.|  
|SCC_I_FILESDIFFER|Katalogu na dysku jest inny niż projekt w kontroli kodu źródłowego.|  
|SCC_I_RELOADFILE|Pliku lub projektu wymaga ponownego załadowania.|  
|SCC_E_FILENOTCONTROLLED|Katalog nie jest pod kontrolą kodu źródłowego.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji o zasoby. Ponowienie próby jest zalecane.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Wystąpił nieokreślony błąd.|  
|SCC_E_FILENOTEXIST|Nie można odnaleźć katalogu lokalnego.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest używana w celu poinstruowania wtyczka do kontroli źródła aby wyświetlać użytkownikowi listę zmian w określonym katalogu. Dodatek otwiera osobnym oknie w formacie własnego wyboru, aby wyświetlić różnice w katalogu użytkownika na dysku i odpowiedniego projektu pod kontrolą wersji.  
  
 Jeśli wtyczka obsługuje porównania katalogów w ogóle, nawet jeśli nie są obsługiwane opcje "szybkie diff" musi obsługiwać porównania katalogów na podstawie nazwy pliku.  
  
|`dwFlags`|Interpretacja|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|Porównanie bez uwzględniania wielkości liter (mogą być używane do szybkiego diff lub wizualizacji).|  
|SCC_DIFF_IGNORESPACE|Ignoruje biały znak (mogą być używane do szybkiego diff lub wizualizacji).|  
|SCC_DIFF_QD_CONTENTS|Jeśli jest obsługiwany przez wtyczka do kontroli źródła, dyskretnie porównuje katalogu bajt po bajcie.|  
|SCC_DIFF_QD_CHECKSUM|Jeśli obsługiwane przez dodatek typu plug-in, dyskretnie porównuje katalogu za pomocą sumy kontrolnej lub, jeśli nie jest obsługiwane, powraca do SCC_DIFF_QD_CONTENTS.|  
|SCC_DIFF_QD_TIME|Jeśli obsługiwane przez dodatek typu plug-in, dyskretnie porównuje katalogiem, za pośrednictwem jego sygnatura czasowa lub, jeśli nie jest obsługiwane, powraca na SCC_DIFF_QD_CHECKSUM lub SCC_DIFF_QD_CONTENTS.|  
  
> [!NOTE]
>  Ta funkcja używa tego samego flag poleceń jako [SccDiff](../extensibility/sccdiff-function.md). Jednak nie obsługuje operacji "szybkie diff" w przypadku katalogów wybrać wtyczki kontroli źródła.  
  
## <a name="see-also"></a>Zobacz także  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)