---
title: Funkcja SccRename | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 929eff85a5dddb96ad518593a955950052dbced7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731314"
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

