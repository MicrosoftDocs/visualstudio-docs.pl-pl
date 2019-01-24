---
title: Funkcja SccInitialize | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ce52b65d028f82d75d4890b0b1298b4d13b7eafa
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54800509"
---
# <a name="sccinitialize-function"></a>SccInitialize, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja inicjuje wtyczka do kontroli źródła i udostępnia możliwości i ograniczeń do zintegrowanego środowiska programistycznego (IDE).  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccInitialize (  
   LPVOID* ppvContext,  
   HWND    hWnd,  
   LPCSTR  lpCallerName,  
   LPSTR   lpSccName,  
   LPLONG  lpSccCaps,  
   LPSTR   lpAuxPathLabel,  
   LPLONG  pnCheckoutCommentLen,  
   LPLONG  pnCommentLen  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppvContext`  
 [in] Wtyczka do kontroli źródła można umieścić wskaźnik do jego strukturę context tutaj.  
  
 `hWnd`  
 [in] Uchwyt okna środowiska IDE, które wtyczka do kontroli źródła można użyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.  
  
 `lpCallerName`  
 [in] Nazwa programu wywołanie wtyczek do kontroli źródła.  
  
 `lpSccName`  
 [out w] Bufor, w którym wtyczka do kontroli źródła umieszcza własną nazwę (aby nie przekroczyć `SCC_NAME_LEN`).  
  
 `lpSccCaps`  
 [out] Zwraca do kontroli źródła w dodatku plug-in flag funkcji.  
  
 `lpAuxPathLabel`  
 [out w] Bufor, w którym wtyczka do kontroli źródła umieszcza ciąg, który opisuje `lpAuxProjPath` parametr zwracany przez [SccOpenProject](../extensibility/sccopenproject-function.md) i [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (aby nie przekroczyć `SCC_AUXLABEL_LEN`).  
  
 `pnCheckoutCommentLen`  
 [out] Zwraca maksymalną dopuszczalną długość dla komentarz do wyewidencjonowania.  
  
 `pnCommentLen`  
 [out] Zwraca maksymalną dopuszczalną długość dla innych komentarzy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Inicjalizacja kontroli źródła zakończyła się pomyślnie.|  
|SCC_E_INITIALIZEFAILED|Nie można zainicjować systemu.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać podanej operacji.|  
|SCC_E_NONSPECFICERROR|Nieokreślony błąd; Nie można zainicjować systemu kontroli źródła.|  
  
## <a name="remarks"></a>Uwagi  
 IDE wywołuje tę funkcję, po pierwszym załadowaniu wtyczka do kontroli źródła. Dzięki temu środowisko IDE do przekazania pewne informacje, takie jak nazwa obiektu wywołującego, do wtyczki. IDE także otrzymuje pewne informacje, takie jak maksymalna dozwolona liczba znaków dla komentarzy i możliwości podłączenia do firmy.  
  
 `ppvContext` Wskazuje `NULL` wskaźnika. Wtyczka do kontroli źródła można przydzielić struktury na własny użytek i przechowują wskaźnik do tej struktury w `ppvContext`. IDE zostanie przekazany this, wskaźnik do każdej innych funkcji VSSCI API co dodatek typu plug-in mają dostępne informacje o kontekście bez konieczności uciekania się do globalnej pamięci masowej i obsługuje wiele wystąpień wtyczki. Ta struktura powinna cofnięta kiedy [SccUninitialize](../extensibility/sccuninitialize-function.md) jest wywoływana.  
  
 `lpCallerName` i `lpSccName` parametry Włącz IDE i wtyczka do kontroli źródła do wymiany nazwy. Te nazwy mogą być stosowane po prostu w celu rozróżnienia wielu wystąpień lub mogą faktycznie pojawiają się w menu i okien dialogowych.  
  
 `lpAuxPathLabel` Jest ciągiem, jako komentarz używany do identyfikowania ścieżka pomocnicze w ramach projektu, który jest przechowywany w pliku rozwiązania i przekazywane do kontroli źródła wtyczek w wywołaniu [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../includes/vsvss-md.md)] ciąg "SourceSafe projektu:"; inne źródła wtyczek kontroli powinien punktowanych za pomocą tego określonego ciągu.  
  
 `lpSccCaps` Parametr zapewnia kontrolę źródła wtyczki miejsce do przechowywania flag bitowych wskazujący możliwości podłączenia do firmy. (Aby uzyskać pełną listę flag bitowych możliwości, zobacz [flagi możliwości](../extensibility/capability-flags.md)). Na przykład jeśli wtyczka plany można zapisać wyniki do funkcji wywołania zwrotnego dostarczane przez obiekt wywołujący, wtyczka ustawiał możliwości bit SCC_CAP_TEXTOUT. Spowoduje to sygnał środowisku IDE nad tworzeniem okna, w którym wyniki kontroli wersji.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [Flagi możliwości](../extensibility/capability-flags.md)
