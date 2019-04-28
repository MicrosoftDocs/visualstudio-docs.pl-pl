---
title: SccHistory Function | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8df85c03201e46768c43fb64cc41b7fa081eb91a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446831"
---
# <a name="scchistory-function"></a>SccHistory, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkcja ta wyświetla historię określonych plików.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccHistory(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pvContext`  
 [in] Struktura kontekście wtyczki kontroli źródła.  
  
 `hWnd`  
 [in] Uchwyt okna środowiska IDE, które wtyczka do kontroli źródła można użyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.  
  
 `nFiles`  
 [in] Liczba plików określonych w `lpFileName` tablicy.  
  
 `lpFileName`  
 [in] Tablica z w pełni kwalifikowane nazwy plików.  
  
 `fOptions`  
 [in] Polecenie flagi (aktualnie nieużywane).  
  
 `pvOptions`  
 [in] Opcje plug-określonych kontroli źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Historia wersji zostały pomyślnie pobrane.|  
|SCC_I_RELOADFILE|System kontroli źródła faktycznie zmodyfikowany plik na dysku podczas pobierania historii (na przykład przez pobranie starej wersji), aby załadować ponownie ten plik IDE.|  
|SCC_E_FILENOTCONTROLLED|Plik nie jest pod kontrolą źródła.|  
|SCC_E_OPNOTSUPPORTED|System kontroli źródła nie obsługuje tej operacji.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji o zasoby. Ponowienie próby jest zalecane.|  
|SCC_E_PROJNOTOPEN|Projekt nie został otwarty.|  
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd. Nie można uzyskać historii plików.|  
  
## <a name="remarks"></a>Uwagi  
 Wtyczka do kontroli źródła może wyświetlać swoje własne okno dialogowe, aby wyświetlić historię każdego pliku, przy użyciu `hWnd` jako okno nadrzędne. Alternatywnie opcjonalny tekst dane wyjściowe wywołania zwrotnego funkcji dostarczonych [SccOpenProject](../extensibility/sccopenproject-function.md) mogą być używane, jeśli jest obsługiwana.  
  
 Należy pamiętać, że w pewnych okolicznościach pliku sprawdzane mogą się zmieniać podczas wykonywania tego wywołania. Na przykład [!INCLUDE[vsvss](../includes/vsvss-md.md)] polecenie history zapewnia możliwość pobrania starej wersji pliku. W takiej sytuacji zwraca wtyczki kontroli źródła `SCC_I_RELOAD` ostrzec IDE, że trzeba ponownie załadować plik.  
  
> [!NOTE]
> Jeśli wtyczka do kontroli źródła nie obsługuje tej funkcji dla plików, można wyświetlić pliku historii pierwszego pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)
