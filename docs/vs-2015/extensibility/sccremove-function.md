---
title: Funkcja SccRemove | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 62974f585fe164c7ccf7ea21a19d22939d806d73
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199976"
---
# <a name="sccremove-function"></a>SccRemove, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja usuwa pliki z systemu kontroli źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccRemove(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 podczas Struktura kontekstu wtyczki kontroli źródła.  
  
 Właściwość  
 podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.  
  
 nFiles  
 podczas Liczba plików określona w `lpFileNames` tablicy.  
  
 lpFileNames  
 podczas Tablica w pełni kwalifikowanych nazw ścieżek lokalnych dla plików do usunięcia.  
  
 lpComment  
 podczas Komentarz, który ma zostać zastosowany do każdego usuniętego pliku.  
  
 fOptions  
 podczas Flagi poleceń (nieużywane).  
  
 pvOptions  
 podczas Opcje dotyczące wtyczki kontroli źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Usuwanie powiodło się.|  
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie znajduje się pod kontrolą źródła.|  
|SCC_E_OPNOTSUPPORTED|System kontroli źródła nie obsługuje tej operacji.|  
|SCC_E_ISCHECKEDOUT|Nie można usunąć pliku, ponieważ użytkownik jest aktualnie wyewidencjonowany.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd; plik nie został usunięty.|  
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja usuwa pliki z systemu kontroli źródła, ale nie usuwa ich z lokalnego dysku twardego użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
