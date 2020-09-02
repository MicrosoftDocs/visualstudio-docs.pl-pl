---
title: Funkcja SccDirQueryInfo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7334ddd1ce6c7f9feac63253246e55b65121e18b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64780274"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja bada listę w pełni kwalifikowanych katalogów dla ich bieżącego stanu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 podczas Struktura kontekstu wtyczki kontroli źródła.  
  
 nDirs  
 podczas Liczba katalogów wybranych do zapytania.  
  
 lpDirNames  
 podczas Tablica w pełni kwalifikowanych ścieżek katalogów, do których mają być wysyłane zapytania.  
  
 lpStatus  
 [in. out] Struktura tablicy dla wtyczki kontroli źródła w celu zwrócenia flag stanu (zobacz [kod stanu katalogu](../extensibility/directory-status-code-enumerator.md) w celu uzyskania szczegółowych informacji).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Zapytanie zakończyło się pomyślnie.|  
|SCC_E_OPNOTSUPPORTED|System kontroli kodu źródłowego nie obsługuje tej operacji.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zalecana jest ponowna próba.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Funkcja wypełnia tablicę zwracaną z maską bitów z `SCC_DIRSTATUS` rodziny (zobacz [kod stanu katalogu](../extensibility/directory-status-code-enumerator.md)), jeden wpis dla każdego podanym katalogu. Tablica Stanów jest przydzielone przez obiekt wywołujący.  
  
 IDE używa tej funkcji przed zmianą nazwy katalogu, aby sprawdzić, czy katalog jest pod kontrolą źródła, badając, czy ma odpowiedni projekt. Jeśli katalog nie znajduje się pod kontrolą źródła, środowisko IDE może zapewnić użytkownikowi odpowiednie ostrzeżenie.  
  
> [!NOTE]
> Jeśli wtyczka kontroli źródła zdecyduje się nie zaimplementować co najmniej jednej wartości stanu, niezaimplementowane bity powinny mieć wartość zero.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Kod stanu katalogu](../extensibility/directory-status-code-enumerator.md)
