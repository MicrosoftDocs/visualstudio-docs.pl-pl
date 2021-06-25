---
description: Ta funkcja tworzy podprojekt o podanej nazwie w istniejącym projekcie nadrzędnym określonym przez argument lpParentProjPath.
title: SccCreateSubProject, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a6df7a801d282113b530f24472419a9735256702
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904685"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject, funkcja
Ta funkcja tworzy podprojekt o podanej nazwie w ramach istniejącego projektu nadrzędnego określonego przez `lpParentProjPath` argument .

## <a name="syntax"></a>Składnia

```cpp
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

### <a name="parameters"></a>Parametry
 Pcontext

[in] Wskaźnik kontekstu wtyczki kontroli źródła.

 Hwnd

[in] Dojście do okna IDE, które wtyczka kontroli źródła może używać jako elementu nadrzędnego dla wszystkich okien dialogowych, które zawiera.

 lpUser

[in, out] Nazwa użytkownika (do SCC_USER_SIZE łącznie z terminatorem NULL).

 lpParentProjPath

[in] Ciąg identyfikujący ścieżkę projektu nadrzędnego (do SCC_PRJPATH_SIZE, łącznie z terminatorem NULL).

 lpSubProjName

[in] Sugerowana nazwa podprojektu (do SCC_PRJPATH_SIZE, w tym terminator NULL).

 lpAuxProjPath

[in, out] Ciąg pomocniczy identyfikujący projekt (do SCC_PRJPATH_SIZE, w tym terminator NULL).

 lpSubProjPath

[in, out] Ciąg wyjściowy identyfikujący ścieżkę dla podprojektu (do SCC_PRJPATH_SIZE, w tym terminator NULL).

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła dla tej funkcji zwraca jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Pomyślnie utworzono podprojekt.|
|SCC_E_INITIALIZEFAILED|Nie można zainicjować projektu nadrzędnego.|
|SCC_E_INVALIDUSER|Użytkownik nie mógł zalogować się do systemu kontroli źródła.|
|SCC_E_COULDNOTCREATEPROJECT|Nie można utworzyć podprojektu.|
|SCC_E_PROJSYNTAXERR|Nieprawidłowa składnia projektu.|
|SCC_E_UNKNOWNPROJECT|Projekt nadrzędny jest nieznany dla wtyczki kontroli źródła.|
|SCC_E_INVALIDFILEPATH|Nieprawidłowa lub nienadatna do użytku ścieżka pliku.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_ACCESSFAILURE|Występuje problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub z powodu wystąpienia problemów z siecią. Zaleca się ponawianie próby.|
|SCC_E_CONNECTIONFAILURE|Występuje problem z połączeniem wtyczki kontroli źródła.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Jeśli podprojekt o nazwie już istnieje, funkcja może zmienić nazwę domyślną, aby utworzyć unikatowy projekt, na przykład dodając do niego \<number> "_". Wywołujący musi być przygotowany do akceptowania zmian `lpUser` w `lpSubProjPath` , i `lpAuxProjPath` . Argumenty `lpSubProjPath` i są następnie używane w `lpAuxProjPath` wywołaniu funkcji [SccOpenProject](../extensibility/sccopenproject-function.md). Nie powinny być modyfikowane przez wywołującego po zwróceniu. Te ciągi zapewniają wtyczkę kontroli źródła w celu śledzenia informacji, które musi skojarzyć z projektem. Po zwróceniu tych dwóch parametrów w idee wywołującego nie będą wyświetlane, ponieważ wtyczka może używać sformatowanych ciągów, które mogą nie być odpowiednie do wyświetlania. Funkcja zwraca kod powodzenia lub niepowodzenia i, jeśli to się powiedzie, wypełnia zmienną pełną ścieżką `lpSubProjPath` projektu do nowego projektu.

 Ta funkcja jest podobna do [funkcji SccGetProjPath,](../extensibility/sccgetprojpath-function.md)z tą różnicą, że tworzy projekt w trybie dyskretnym, zamiast monitować użytkownika o jego wybranie. Gdy funkcja `SccCreateSubProject` zostanie wywołana, funkcja nie będzie pusta i `lpParentProjName` będzie `lpAuxProjPath` odpowiadać prawidłowemu projektowi. Te ciągi są zwykle odbierane przez ideę z poprzedniego wywołania funkcji `SccGetProjPath` lub [ścieżki SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).

 Argument `lpUser` jest nazwą użytkownika. Ide przekaże tę samą nazwę użytkownika, która została wcześniej odebrana z pliku , a wtyczka kontroli źródła powinna używać nazwy `SccGetProjPath` jako domyślnej. Jeśli użytkownik ma już otwarte połączenie z wtyczką, wtyczka powinna próbować wyeliminować wszelkie monity, aby upewnić się, że funkcja działa w trybie dyskretnym. Jeśli jednak logowanie nie powiedzie się, wtyczka powinna monitować użytkownika o zalogowanie i po otrzymaniu prawidłowego identyfikatora logowania przekazać nazwę z powrotem w `lpUser` . Ponieważ wtyczka może zmienić ten ciąg, ide zawsze przydzieli bufor o rozmiarze (SCC_USER_LEN+1 lub SCC_USER_SIZE, który zawiera miejsce dla terminatora wartości null). Jeśli ciąg zostanie zmieniony, nowy ciąg musi być prawidłową nazwą logowania (co najmniej tak prawidłową jak stary ciąg).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Uwagi techniczne dotyczące SccCreateSubProject i SccGetParentProjectPath
 Dodawanie rozwiązań i projektów do kontroli źródła zostało uproszczone w systemie Visual Studio w celu zminimalizowania liczby monitów o wybranie lokalizacji w systemie kontroli źródła przez użytkownika. Te zmiany są aktywowane przez Visual Studio, jeśli wtyczka kontroli źródła obsługuje obie nowe funkcje i `SccCreateSubProject` `SccGetParentProjectPath` . Jednak następującego wpisu rejestru można użyć do wyłączenia tych zmian i przywrócenia poprzedniego zachowania Visual Studio (wtyczki interfejsu API kontroli kodu źródłowego w wersji 1.1):

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Jeśli ten wpis rejestru nie istnieje lub jest ustawiony na dword:000000000, Visual Studio próbuje użyć nowych funkcji i `SccCreateSubProject` `SccGetParentProjectPath` .

 Jeśli wpis rejestru jest ustawiony na dword:00000001, program Visual Studio nie próbuje użyć tych nowych funkcji ani operacji dodawania do kontroli źródła działa tak jak w poprzednich wersjach Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
