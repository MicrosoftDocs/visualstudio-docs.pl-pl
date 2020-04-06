---
title: Funkcja SccCreateSubProject | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74354e05b16830f599dd706fbe48aadd75b11a18
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701040"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject, funkcja
Ta funkcja tworzy podprojekt o podanej nazwie w ramach `lpParentProjPath` istniejącego projektu nadrzędnego określonego przez argument.

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

[w] Wskaźnik kontekstu wtyczki formantu źródła.

 Hwnd

[w] Dojście do okna IDE, którego wtyczka formantu źródła może używać jako element nadrzędny dla wszystkich okien dialogowych, które udostępnia.

 lpUżycie

[w, na zewnątrz] Nazwa użytkownika (do SCC_USER_SIZE, w tym terminator NULL).

 lpParentProjPath

[w] Ciąg identyfikujący ścieżkę projektu nadrzędnego (do SCC_PRJPATH_SIZE, w tym terminator NULL).

 lpSubProjName

[w] Sugerowana nazwa podprojektu (do SCC_PRJPATH_SIZE, w tym terminator NULL).

 lpAuxProjPath (lpAuxProjPath)

[w, na zewnątrz] Ciąg pomocniczy identyfikujący projekt (do SCC_PRJPATH_SIZE, w tym terminator NULL).

 lpSubProjPath

[w, na zewnątrz] Ciąg wyjściowy identyfikujący ścieżkę podprojektu (do SCC_PRJPATH_SIZE, w tym terminator NULL).

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Podprojekt został pomyślnie utworzony.|
|SCC_E_INITIALIZEFAILED|Nie można zainicjować projektu nadrzędnego.|
|SCC_E_INVALIDUSER|Użytkownik nie może zalogować się do systemu kontroli źródła.|
|SCC_E_COULDNOTCREATEPROJECT|Nie można utworzyć podprojektu.|
|SCC_E_PROJSYNTAXERR|Nieprawidłowa składnia projektu.|
|SCC_E_UNKNOWNPROJECT|Projekt nadrzędny jest nieznany do wtyczki kontroli źródła.|
|SCC_E_INVALIDFILEPATH|Nieprawidłowa lub niezrozumiasowalna ścieżka pliku.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zaleca się ponowną próbę.|
|SCC_E_CONNECTIONFAILURE|Wystąpił problem z połączeniem wtyczki sterowania źródłem.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Niespecyficzna awaria.|

## <a name="remarks"></a>Uwagi
 Jeśli podprojekt o nazwie już istnieje, funkcja może zmienić nazwę domyślną, aby utworzyć unikatową, na przykład dodając do niej "_\<numer>". Rozmówca musi być przygotowany do `lpUser` `lpSubProjPath`zaakceptowania `lpAuxProjPath`zmian w , i . Argumenty `lpSubProjPath` `lpAuxProjPath` i są następnie używane w wywołaniu [SccOpenProject](../extensibility/sccopenproject-function.md). Nie powinny być modyfikowane przez rozmówcę po zwrocie. Te ciągi umożliwiają wtyczkę formantu źródła do śledzenia informacji, które musi skojarzyć z projektem. Ide wywołującego nie wyświetli tych dwóch parametrów po powrocie, ponieważ dodatek może używać sformatowanego ciągu, który może nie być odpowiedni do wyświetlania. Funkcja zwraca kod sukcesu lub niepowodzenia i, jeśli `lpSubProjPath` się powiedzie, wypełnia zmienną pełną ścieżką projektu do nowego projektu.

 Ta funkcja jest podobna do [SccGetProjPath](../extensibility/sccgetprojpath-function.md), z tą różnicą, że dyskretnie tworzy projekt, a nie monituje użytkownika, aby wybrać jeden. Gdy `SccCreateSubProject` funkcja jest `lpParentProjName` wywoływana i `lpAuxProjPath` nie będzie pusta i będzie odpowiadać prawidłowemu projektowi. Te ciągi są zwykle odbierane przez IDE `SccGetProjPath` z poprzedniego wywołania funkcji lub [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).

 Argument `lpUser` jest nazwą użytkownika. IDE będzie przechodzić w tej samej nazwie `SccGetProjPath`użytkownika, który wcześniej otrzymał od , a wtyczka kontroli źródła powinna używać nazwy jako domyślnej. Jeśli użytkownik ma już otwarte połączenie z wtyczką, wtyczka powinna spróbować wyeliminować wszelkie monity, aby upewnić się, że funkcja działa cicho. Jeśli jednak logowanie nie powiedzie się, wtyczka powinna monitować użytkownika o zalogowanie, a `lpUser`po otrzymaniu prawidłowego logowania przekazać nazwę z powrotem w . Ponieważ dodatek może zmienić ten ciąg, IDE zawsze przydziela bufor o rozmiarze (SCC_USER_LEN +1 lub SCC_USER_SIZE, który zawiera miejsce dla terminatora null). Jeśli ciąg zostanie zmieniony, nowy ciąg musi być prawidłową nazwą logowania (co najmniej tak samo prawidłową jak stary ciąg).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Uwagi techniczne dotyczące programu SccCreateSubProject i SccGetParentProjectPath
 Dodawanie rozwiązań i projektów do kontroli źródła zostało uproszczone w programie Visual Studio, aby zminimalizować liczbę monitów użytkownika o wybranie lokalizacji w systemie kontroli źródła. Te zmiany są aktywowane przez program Visual Studio, jeśli wtyczka `SccCreateSubProject` `SccGetParentProjectPath`formantu źródłowego obsługuje obie nowe funkcje i . Jednak następujący wpis rejestru może służyć do wyłączenia tych zmian i przywrócić do poprzedniego zachowania programu Visual Studio (Source Control Plug-in API w wersji 1.1):

 **[HKEY_CURRENT_USER\Oprogramowanie\Microsoft\VisualStudio\8.0\Kontrola źródła] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Jeśli ten wpis rejestru nie istnieje lub jest ustawiony na dword:00000000, `SccCreateSubProject` `SccGetParentProjectPath`program Visual Studio próbuje użyć nowych funkcji i .

 Jeśli wpis rejestru jest ustawiony na dword:00000001, Visual Studio nie próbuje użyć tych nowych funkcji, a operacje dodawania do kontroli źródła działają tak, jak w poprzednich wersjach programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki sterowania źródłem](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
