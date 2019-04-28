---
title: Funkcja SccOpenProject | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: af2b33d31d813533d833e4a5c15a3b562bc2e94e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446788"
---
# <a name="sccopenproject-function"></a>SccOpenProject, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja otwiera istniejący projekt kontroli źródła lub tworzy nowy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccOpenProject (  
   LPVOID        pvContext,  
   HWND          hWnd,  
   LPSTR         lpUser,  
   LPCSTR        lpProjName,  
   LPCSTR        lpLocalProjPath,  
   LPSTR         lpAuxProjPath,  
   LPCSTR        lpComment,  
   LPTEXTOUTPROC lpTextOutProc,  
   LONG          dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekście wtyczki kontroli źródła.  
  
 hWnd  
 [in] Uchwyt okna środowiska IDE, które wtyczka do kontroli źródła można użyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.  
  
 lpUser  
 [out w] Nazwa użytkownika (nie przekraczając liczby SCC_USER_SIZE, w tym terminator o wartości NULL).  
  
 lpProjName  
 [in] Ciąg, który identyfikuje nazwę projektu.  
  
 lpLocalProjPath  
 [in] Ścieżka do folderu roboczego dla projektu.  
  
 lpAuxProjPath  
 [out w] Opcjonalny ciąg pomocnicze, identyfikowanie projektu (nie przekraczając liczby SCC_AUXPATH_SIZE, w tym terminator o wartości NULL).  
  
 lpComment  
 [in] Komentarz do nowego projektu, która jest tworzona.  
  
 lpTextOutProc  
 [in] Funkcja wywołania zwrotnego opcjonalne do wyświetlania tekstu w danych wyjściowych z wtyczka do kontroli źródła.  
  
 Flagidw  
 [in] Sygnały czy nowy projekt musi zostać utworzona, jeśli projekt jest nieznany w źródle kontrolować wtyczki. Wartość może być kombinacją `SCC_OP_CREATEIFNEW` i `SCC_OP_SILENTOPEN.`  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Podczas otwierania projektu zakończyło się pomyślnie.|  
|SCC_E_INITIALIZEFAILED|Nie można zainicjować projektu.|  
|SCC_E_INVALIDUSER|Użytkownik nie może zalogować do systemu kontroli źródła.|  
|SCC_E_COULDNOTCREATEPROJECT|Projekt nie istnieje przed wywołaniem;  `SCC_OPT_CREATEIFNEW` została ustawiona flaga, ale nie można utworzyć projektu.|  
|SCC_E_PROJSYNTAXERR|Składnia nieprawidłowy projekt.|  
|SCC_E_UNKNOWNPROJECT|Projekt jest nieznany do wtyczki kontroli źródła i `SCC_OPT_CREATEIFNEW` nie ustawiono flagi.|  
|SCC_E_INVALIDFILEPATH|Ścieżka pliku nieprawidłowy lub nie do użytku.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji o zasoby. Ponowienie próby jest zalecane.|  
|SCC_E_NONSPECFICERROR|Nieokreślony błąd; Nie można zainicjować systemu kontroli źródła.|  
  
## <a name="remarks"></a>Uwagi  
 IDE może przekazać nazwę użytkownika (`lpUser`), lub ją po prostu przekazać wskaźnik na pusty ciąg. W przypadku nazwy użytkownika, wtyczka do kontroli źródła należy używać go jako domyślny. Jednak jeśli nazwa nie została przekazana lub logowanie nie powiodło się o podanej nazwie, wtyczka powinien zostać wyświetlony monit logowania i zwraca prawidłową nazwę w `lpUser` po odebraniu prawidłową nazwą logowania`.` ponieważ wtyczki mogą zmienić ciągu nazwy użytkownika , IDE będzie zawsze Przydziel bufor o rozmiarze (`SCC_USER_LEN`+ 1 lub SCC_USER_SIZE, w tym miejsce terminator o wartości null).  
  
> [!NOTE]
> Pierwszą akcją IDE może wymagać wykonania może być wywołanie `SccOpenProject` funkcji lub [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Z tego powodu w obu z nich ma takie same `lpUser` parametru.  
  
 `lpAuxProjPath` i`lpProjName` są odczytywane z pliku rozwiązania lub zostaną one zwrócone w wyniku wywołania `SccGetProjPath` funkcji. Parametry te zawierają ciągi, które wtyczka do kontroli źródła zostanie skojarzony z projektem i mają znaczenie tylko dla wtyczki. Jeśli nie takie ciągi znajdują się w pliku rozwiązania, a użytkownik nie ma monicie do przeglądania (która zwraca ciąg za pośrednictwem `SccGetProjPath` funkcji), IDE przekazuje puste ciągi dla obu `lpAuxProjPath` i `lpProjName`i oczekuje, że te wartości do zaktualizowania Wtyczka gdy ta funkcja zwraca.  
  
 `lpTextOutProc` jest wskaźnikiem do funkcji wywołania zwrotnego, udostępniane przez środowisko IDE będzie wtyczka do kontroli źródła na potrzeby wyświetlania danych wyjściowych polecenia wynik. Ta funkcja wywołania zwrotnego jest szczegółowo opisane w [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
> [!NOTE]
> Jeśli wtyczka do kontroli źródła nie chce skorzystać z tej, musi być zainstalowany `SCC_CAP_TEXTOUT` znacznik w [SccInitialize](../extensibility/sccinitialize-function.md). Jeśli nie ustawiono tej flagi lub IDE nie obsługuje tej funkcji `lpTextOutProc` będzie `NULL`.  
  
 `dwFlags` Parametr określa wynik w przypadku, gdy do projektu jest obecnie nie istnieje. Składa się z dwóch flag bitowych, `SCC_OP_CREATEIFNEW` i `SCC_OP_SILENTOPEN`. Jeśli projekt jest już otwarty, funkcja po prostu otwiera projekt i zwraca `SCC_OK`. Jeśli projekt nie istnieje, a jeśli `SCC_OP_CREATEIFNEW` flaga jest włączona, wtyczka do kontroli źródła można utworzyć projekt w systemie kontroli źródła, otwórz go i zwracają `SCC_OK`. Jeśli projekt nie istnieje, a `SCC_OP_CREATEIFNEW` flaga jest wyłączona, wtyczki należy następnie wyszukiwać `SCC_OP_SILENTOPEN` flagi. Jeśli tej flagi nie jest włączony, wtyczki może monitować użytkownika o podanie nazwy projektu. Jeśli tę flagę znajduje się na, wtyczkę należy po prostu zwrócenia `SCC_E_UNKNOWNPROJECT`.  
  
## <a name="calling-order"></a>Kolejności wywoływania  
 W trakcie normalnego przebiegu zdarzenia [SccInitialize](../extensibility/sccinitialize-function.md) może zostać wywołane najpierw otworzyć sesji kontroli źródła. Sesja może składać się wywołania `SccOpenProject`, następuje inne wywołania funkcji API wtyczki kontroli źródła i będą kończyć się wywołanie [SccCloseProject](../extensibility/scccloseproject-function.md). Takie sesje mogą należy powtórzyć kilkakrotnie przed [SccUninitialize](../extensibility/sccuninitialize-function.md) jest wywoływana.  
  
 Jeśli zestawy wtyczki kontroli źródła `SCC_CAP_REENTRANT` bit w `SccInitialize`, a następnie powyżej sekwencji sesji może być powtarzany tyle razy równolegle. Różne `pvContext` struktury śledzenia różne sesje, w których każdy `pvContext` jest skojarzony z jednym Otwórz projekt w danym momencie. Na podstawie`pvContext` parametr wtyczki można określić, który projekt odwołuje się do dowolnego konkretnego wywołania. Jeśli bit możliwości `SCC_CAP_REENTRANT` nie ustawiono, nonreentrant wtyczek kontroli kodu źródłowego są ograniczone zdolności do pracy z wieloma projektami.  
  
> [!NOTE]
> `SCC_CAP_REENTRANT` Bitowa została wprowadzona w wersji 1.1 API wtyczki kontroli źródła. Nie jest ustawiona, lub w wersji 1.0 jest ignorowana, a wszystkie w wersji 1.0 źródła wtyczek kontroli są zakłada się, że nonreentrant.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [Ograniczenia długości ciągów](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
