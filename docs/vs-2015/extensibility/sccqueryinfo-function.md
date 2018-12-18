---
title: Funkcja SccQueryInfo | Dokumentacja firmy Microsoft
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
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a7093f712ab520502e36094ec571c0ee1a3ded18
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785082"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja pobiera informacje o stanie dla zestawu wybranych plików pod kontrolą źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccQueryInfo(  
   LPVOID  pvContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekście wtyczki kontroli źródła.  
  
 Niepowodzeń  
 [in] Liczba plików określonych w `lpFileNames` tablicy i długość `lpStatus` tablicy.  
  
 lpFileNames  
 [in] Tablica nazw plików, które ma zostać zbadany.  
  
 lpStatus  
 [out w] Tablica, w którym wtyczka do kontroli źródła zwraca flagi stanu dla każdego pliku. Aby uzyskać więcej informacji, zobacz [kod stanu pliku](../extensibility/file-status-code-enumerator.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Zapytania zakończyło się pomyślnie.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskiwaniem dostępu do systemu kontroli źródła prawdopodobnie spowodowane przez problemy z siecią lub rywalizacji o zasoby. Ponowienie próby jest zalecane.|  
|SCC_E_PROJNOTOPEN|Projekt nie jest otwarty pod kontrolą źródła.|  
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `lpFileName` jest pustym ciągiem, jest obecnie nie informacje o stanie do zaktualizowania. W przeciwnym razie jest pełna nazwa ścieżki pliku, dla którego zostały zmienione informacje o stanie.  
  
 Zwracana tablica może być maską bitów z `SCC_STATUS_xxxx` usługi bits. Aby uzyskać więcej informacji, zobacz [kod stanu pliku](../extensibility/file-status-code-enumerator.md). System kontroli źródła może nie obsługiwać wszystkich typów bitowych. Na przykład jeśli `SCC_STATUS_OUTOFDATE` nie jest dostępna, ale nie ustawiono bitu.  
  
 Wyewidencjonowywanie plików za pomocą tej funkcji, należy pamiętać o następujących `MSSCCI` stan wymagania:  
  
-   `SCC_STATUS_OUTBYUSER` jest ustawiona, gdy bieżący użytkownik ma wyewidencjonowania pliku.  
  
-   `SCC_STATUS_CHECKEDOUT` Nie można ustawić, chyba że `SCC_STATUS_OUTBYUSER` jest ustawiona.  
  
-   `SCC_STATUS_CHECKEDOUT` jest tylko ustawiona, gdy plik jest wyewidencjonowany do wyznaczonej katalogu roboczego.  
  
-   Jeśli plik jest wyewidencjonowany przez bieżącego użytkownika w katalogu innym niż katalog roboczy `SCC_STATUS_OUTBYUSER` jest ustawiona, ale `SCC_STATUS_CHECKEDOUT` nie jest.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Kod stanu pliku](../extensibility/file-status-code-enumerator.md)

