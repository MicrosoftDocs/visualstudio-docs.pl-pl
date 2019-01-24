---
title: Funkcja SccCreateSubProject | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c2f28d8bb9ebc440db69085324becb6a96c19afe
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54752597"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja tworzy podprojekt o podanej nazwie w ramach istniejącego projektu nadrzędnej określonej przez `lpParentProjPath` argumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccCreateSubProject(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpParentProjPath,  
   LPCSTR lpSubProjName,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpSubProjPath  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 [in] Wskaźnik kontekście wtyczki kontroli źródła.  
  
 hWnd  
 [in] Uchwyt okna środowiska IDE, które wtyczka do kontroli źródła można użyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.  
  
 lpUser  
 [out w] Nazwa użytkownika (maksymalnie SCC_USER_SIZE tym terminator o wartości NULL).  
  
 lpParentProjPath  
 [in] Ciąg identyfikujący ścieżkę projektu nadrzędnego (maksymalnie SCC_PRJPATH_SIZE tym terminator o wartości NULL).  
  
 lpSubProjName  
 [in] Nazwa sugerowane podprojekt (maksymalnie SCC_PRJPATH_SIZE tym terminator o wartości NULL).  
  
 lpAuxProjPath  
 [out w] Pomocnicze ciąg identyfikujący projekt (maksymalnie SCC_PRJPATH_SIZE tym terminator o wartości NULL).  
  
 lpSubProjPath  
 [out w] Ciąg danych wyjściowych, który identyfikuje ścieżkę dla podprojektu (maksymalnie SCC_PRJPATH_SIZE tym terminator o wartości NULL).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Podprojekt został pomyślnie utworzony.|  
|SCC_E_INITIALIZEFAILED|Nie można zainicjować projektu nadrzędnego.|  
|SCC_E_INVALIDUSER|Użytkownik nie może zalogować do systemu kontroli źródła.|  
|SCC_E_COULDNOTCREATEPROJECT|Nie można utworzyć podprojektu.|  
|SCC_E_PROJSYNTAXERR|Składnia nieprawidłowy projekt.|  
|SCC_E_UNKNOWNPROJECT|Projekt nadrzędny jest nieznany wtyczka do kontroli źródła.|  
|SCC_E_INVALIDFILEPATH|Ścieżka pliku nieprawidłowy lub nie do użytku.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji o zasoby. Ponowienie próby jest zalecane.|  
|SCC_E_CONNECTIONFAILURE|Wystąpił problem podczas połączenia wtyczki kontroli źródła.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Wystąpił nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli podprojekt o tej nazwie już istnieje, funkcja może zmienić domyślną nazwę utworzyć unikatowy, na przykład dodając "_\<liczba >" do niego. Obiekt wywołujący musi być gotowi do zaakceptowania zmian `lpUser`, `lpSubProjPath`, i `lpAuxProjPath`. `lpSubProjPath` i`lpAuxProjPath` argumenty są następnie używane w wywołaniu [SccOpenProject](../extensibility/sccopenproject-function.md). Nie powinny one być modyfikowane przez obiekt wywołujący po powrocie. Te ciągi umożliwiają dla dodatku typu plug-in do śledzenia informacji wymaganych do skojarzenia z projektu kontroli źródła. Obiekt wywołujący IDE nie są wyświetlane te dwa parametry po powrocie, ponieważ wtyczki mogą używać sformatowany ciąg, który może nie być przydatny do wyświetlania. Funkcja zwróci kod powodzenia lub niepowodzenia i jeśli to się powiedzie, wypełnia zmiennej `lpSubProjPath` ze ścieżką pełną projektu do nowego projektu.  
  
 Ta funkcja jest podobny do [SccGetProjPath](../extensibility/sccgetprojpath-function.md), chyba że dyskretnie tworzy projekt, a nie monitowania użytkownika o wybranie jednego. Gdy `SccCreateSubProject` funkcja jest wywoływana, `lpParentProjName` i `lpAuxProjPath` nie jest pusty i będą odpowiadać prawidłowym projektem. Te ciągi są zazwyczaj odbierane przez środowisko IDE z poprzedniego wywołania `SccGetProjPath` funkcji lub [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).  
  
 `lpUser` Argument jest nazwą użytkownika. IDE przejdzie w tej samej nazwy użytkownika, który poprzednio odbierał z `SccGetProjPath`, a wtyczka do kontroli źródła, należy użyć nazwy jako domyślny. Jeśli użytkownik ma już otwartego połączenia przy użyciu wtyczki, wtyczka powinna spróbuj wyeliminować żadnych monitów, aby upewnić się, że funkcja działa w trybie dyskretnym. Jednakże, jeśli logowanie nie powiedzie się, wtyczka powinien zostać wyświetlony monit użytkownika dla nazwy logowania, a po odebraniu prawidłową nazwą logowania — dostęp próbny nazwę z powrotem w `lpUser`. Ponieważ wtyczki mogą zmienić ten ciąg, IDE zawsze przydzieli bufor o rozmiarze (SCC_USER_LEN + 1 lub SCC_USER_SIZE, w tym miejsce terminator o wartości null). Jeśli ciąg zostanie zmieniona, nowy ciąg musi być prawidłową nazwą logowania (co najmniej jako prawidłowe jako stary ciąg).  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Uwagi techniczne SccCreateSubProject i SccGetParentProjectPath  
 Dodawanie rozwiązania i projekty do kontroli źródła został uproszczony w programie Visual Studio, aby zminimalizować liczbę przypadków, gdy użytkownik jest monitowany o wybierz lokalizacje w systemie kontroli źródła. Zmiany te zostaną aktywowane przez program Visual Studio, jeśli wtyczka do kontroli źródła, obsługuje zarówno z nowych funkcji `SccCreateSubProject` i `SccGetParentProjectPath`. Jednak następujący wpis rejestru można wyłączyć te zmiany i przywrócić poprzednie zachowanie programu Visual Studio (źródło sterowania wtyczki interfejsu API w wersji 1.1):  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = dword: 00000001  
  
 Jeśli ten wpis rejestru nie istnieje lub ma wartość DWORD: 00000000, Visual Studio próbuje użyć nowych funkcji `SccCreateSubProject` i `SccGetParentProjectPath`.  
  
 Jeśli wpis rejestru DWORD: 00000001 programu Visual Studio nie jest podejmowana próba użycia tych nowych funkcji, a operacje dodania do kontroli źródła działają podobnie jak w poprzednich wersjach programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
