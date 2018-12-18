---
title: Funkcja SccRunScc | Dokumentacja firmy Microsoft
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
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 67d2ad2ee783d23e3bd8c960ad5a94eac3fbd908
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733688"
---
# <a name="sccrunscc-function"></a>SccRunScc, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja wywołuje narzędzia administracji kontroli źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekście wtyczki kontroli źródła.  
  
 hWnd  
 [in] Uchwyt okna środowiska IDE, które wtyczka do kontroli źródła można użyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.  
  
 Niepowodzeń  
 [in] Liczba plików określonych w `lpFileNames` tablicy.  
  
 lpFileNames  
 [in] Tablica nazw wybranego pliku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Pomyślnie wywołano narzędzia administracji kontroli źródła.|  
|SCC_I_OPERATIONCANCELED|Operacja została anulowana.|  
|SCC_E_INITIALIZEFAILED|Nie można zainicjować systemu kontroli źródła.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji o zasoby.|  
|SCC_E_CONNECTIONFAILURE|Nie można nawiązać połączenia z systemu kontroli źródła.|  
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie jest pod kontrolą źródła.|  
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja umożliwia obiektowi wywołującemu dostęp do pełnego zakresu funkcji systemu kontroli źródła, za pomocą narzędzia do administrowania zewnętrznych. Jeśli system kontroli źródła nie ma interfejsu użytkownika, wtyczka do kontroli źródła może implementować interfejs do wykonywania funkcji administracyjnych niezbędne.  
  
 Ta funkcja jest wywoływana z liczbą i Tablica nazw plików dla aktualnie wybranych plików. Jeśli narzędzie administracyjne obsługuje tę funkcję, lista plików może służyć do wstępnego wyboru plików w interfejs administracyjny; w przeciwnym razie listy można zignorować.  
  
 Ta funkcja jest zwykle wywoływane, gdy użytkownik wybierze **Uruchom \<serwera kontroli źródła >** z **pliku** -> **kontroli źródła** menu. To **Uruchom** opcję menu, które mogą być zawsze wyłączone lub nawet ukryte przez ustawienie wpisu rejestru. Zobacz [porady: Instalowanie wtyczki kontroli źródła](../extensibility/internals/how-to-install-a-source-control-plug-in.md) Aby uzyskać szczegółowe informacje. Ta funkcja jest wywoływana tylko wtedy, gdy [SccInitialize](../extensibility/sccinitialize-function.md) zwraca `SCC_CAP_RUNSCC` bit możliwości (zobacz [flagi możliwości](../extensibility/capability-flags.md) Aby uzyskać szczegółowe informacje na ten temat i inne możliwości usługi bits).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Porady: Instalowanie wtyczki kontroli źródła](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Flagi możliwości](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)

