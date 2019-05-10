---
title: Funkcja SccRename | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e78975acab0bf30f1f188cdd7b6454fd6e74ce6f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54783742"
---
# <a name="sccrename-function"></a>SccRename, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja zmienia nazwę pliku w systemie kontroli źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccRename(  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName,  
   LPCSTR lpNewName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekście wtyczki kontroli źródła.  
  
 hWnd  
 [in] Uchwyt okna środowiska IDE, które wtyczka do kontroli źródła można użyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.  
  
 lpFileName  
 [in] W pełni kwalifikowaną nazwę pliku nazwa jest zmieniana.  
  
 lpNewName  
 [in] W pełni kwalifikowana nazwa nowego. Jeśli ścieżka katalogu jest inna, plik został przeniesiony w z jednego podkatalogu do innego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Pomyślnie ukończono operację zmiany nazwy.|  
|SCC_E_PROJNOTOPEN|Projekt nie jest otwarty pod kontrolą źródła.|  
|SCC_E_FILENOTCONTROLLED|Plik nie jest pod kontrolą źródła.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji o zasoby.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie ma uprawnień do wykonania tej operacji.|  
|SCC_E_COULDNOTCREATEPROJECT|Nie można utworzyć projektu jako część procesu zmiany nazwy.|  
|SCC_E_OPNOTPERFORMED|Nie można wykonać operacji.|  
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony lub ogólny błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja może służyć do zmiany nazwy pliku lub przenieść je z jednej lokalizacji do innej, w systemie kontroli źródła. Wtyczka do kontroli źródła nie należy próbować uzyskać dostęp do pliku na dysku. Odpowiada środowiska IDE można zmienić nazwy pliku lokalnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)
