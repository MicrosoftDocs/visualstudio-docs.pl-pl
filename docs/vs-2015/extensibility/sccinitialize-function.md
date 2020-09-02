---
title: Funkcja SccInitialize | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200039"
---
# <a name="sccinitialize-function"></a>SccInitialize, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja inicjuje wtyczkę kontroli źródła i zapewnia możliwości i limity zintegrowanego środowiska programistycznego (IDE).  
  
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
 podczas Wtyczka do kontroli źródła może umieścić wskaźnik do jego struktury kontekstu w tym miejscu.  
  
 `hWnd`  
 podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.  
  
 `lpCallerName`  
 podczas Nazwa programu wywołującego wtyczkę kontroli źródła.  
  
 `lpSccName`  
 [in. out] Bufor, w którym wtyczka do kontroli źródła umieszcza własną nazwę (nie przekracza `SCC_NAME_LEN` ).  
  
 `lpSccCaps`  
 określoną Zwraca flagi możliwości wtyczki kontroli źródła.  
  
 `lpAuxPathLabel`  
 [in. out] Bufor, w którym Wtyczka kontroli źródła umieszcza ciąg, który opisuje `lpAuxProjPath` parametr zwracany przez [SccOpenProject](../extensibility/sccopenproject-function.md) i [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (nie przekroczenia wartości `SCC_AUXLABEL_LEN` ).  
  
 `pnCheckoutCommentLen`  
 określoną Zwraca maksymalną dopuszczalną długość komentarza do wyewidencjonowania.  
  
 `pnCommentLen`  
 określoną Zwraca maksymalną dopuszczalną długość dla innych komentarzy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Inicjalizacja kontroli źródła zakończyła się pomyślnie.|  
|SCC_E_INITIALIZEFAILED|Nie można zainicjować systemu.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać określonej operacji.|  
|SCC_E_NONSPECFICERROR|Nieokreślony błąd; System kontroli źródła nie został zainicjowany.|  
  
## <a name="remarks"></a>Uwagi  
 IDE wywołuje tę funkcję, gdy najpierw ładuje wtyczkę kontroli źródła. Umożliwia IDE przekazywanie pewnych informacji, takich jak nazwa obiektu wywołującego, do wtyczki. IDE pobiera również pewne informacje, takie jak maksymalna dozwolona długość komentarzy i możliwości wtyczki.  
  
 `ppvContext`Punkty do `NULL` wskaźnika. Wtyczka do kontroli źródła może przydzielić strukturę do własnego użytku i przechowywać wskaźnik do tej struktury w `ppvContext` . IDE przekaże ten wskaźnik do każdej innej funkcji interfejsu API VSSCI, dzięki czemu wtyczka będzie mieć dostęp do informacji kontekstowych bez konieczności używania magazynu globalnego i obsługi wielu wystąpień wtyczki. Ta struktura powinna zostać cofnięta alokacja, gdy zostanie wywołana [SccUninitialize](../extensibility/sccuninitialize-function.md) .  
  
 `lpCallerName`Parametry i `lpSccName` umożliwiają Włączanie środowiska IDE i wtyczki kontroli źródła do nazw programu Exchange. Nazwy te mogą być używane po prostu do rozróżnienia między wieloma wystąpieniami lub mogą być wyświetlane w menu lub oknach dialogowych.  
  
 `lpAuxPathLabel`Parametr jest ciągiem używanym jako komentarz do identyfikacji pomocniczej ścieżki projektu przechowywanej w pliku rozwiązania i przekazaną do wtyczki kontroli źródła w wywołaniu [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../includes/vsvss-md.md)] używa ciągu "Project SourceSafe:"; inne wtyczki kontroli źródła nie mogą korzystać z tego konkretnego ciągu.  
  
 `lpSccCaps`Parametr udostępnia wtyczkę kontroli źródła w miejscu do przechowywania bitflags wskazujących możliwości wtyczki. (Aby zapoznać się z pełną listą możliwości bitflags, zobacz [flagi możliwości](../extensibility/capability-flags.md)). Na przykład, jeśli wtyczka planuje pisać wyniki do funkcji wywołania zwrotnego dostarczonej przez wywołującego, wtyczka ustawi SCC_CAP_TEXTOUT bit możliwości. Spowoduje to nasygnalizowanie środowiska IDE w celu utworzenia okna dla wyników kontroli wersji.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [Flagi możliwości](../extensibility/capability-flags.md)
