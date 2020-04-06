---
title: Funkcja SccGetParentProjectPath | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f258558207f86ff76746d18aa432fe4c5850290
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700716"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath, funkcja
Ta funkcja określa ścieżkę projektu nadrzędnego określonego projektu. Ta funkcja jest wywoływana, gdy użytkownik jest dodanie projektu programu Visual Studio do kontroli źródła.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccGetParentProjectPath(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpProjPath,
   LPSTR  lpAuxProjPath,
   LPSTR  lpParentProjPath
);
```

### <a name="parameters"></a>Parametry
 Pcontext

[w] Wskaźnik kontekstu wtyczki formantu źródła.

 Hwnd

[w] Dojście do okna IDE, którego wtyczka formantu źródła może używać jako element nadrzędny dla wszystkich okien dialogowych, które udostępnia.

 lpUżycie

[w, na zewnątrz] Nazwa użytkownika (do SCC_USER_SIZE, w tym terminator NULL).

 lpProjPath (Ścieżka lpProjPath)

[w] Ciąg identyfikujący ścieżkę projektu (do SCC_PRJPATH_SIZE, w tym terminator NULL).

 lpAuxProjPath (lpAuxProjPath)

[w, na zewnątrz] Ciąg pomocniczy identyfikujący projekt (do SCC_PRJPATH_SIZE, w tym terminator NULL).

 lpParentProjPath

[w, na zewnątrz] Ciąg wyjściowy identyfikujący ścieżkę projektu nadrzędnego (do SCC_PRJPATH_SIZE, w tym terminator NULL).

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Ścieżka projektu nadrzędnego została pomyślnie uzyskana.|
|SCC_E_INITIALIZEFAILED|Nie można zainicjować projektu.|
|SCC_E_INVALIDUSER|Użytkownik nie może zalogować się do wtyczki kontroli źródła.|
|SCC_E_UNKNOWNPROJECT|Projekt jest nieznany do wtyczki kontroli źródła.|
|SCC_E_INVALIDFILEPATH|Nieprawidłowa lub niezrozumiasowalna ścieżka pliku.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zaleca się ponowną próbę.|
|SCC_E_PROJSYNTAXERR|Nieprawidłowa składnia projektu.|
|SCC_E_CONNECTIONFAILURE|Problem z połączeniem sklepu.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Niespecyficzna awaria.|

## <a name="remarks"></a>Uwagi
 Ta funkcja zwraca kod sukcesu lub niepowodzenia i, `lpParentProjPath` jeśli się powiedzie, wypełnia zmienną pełną ścieżką projektu do określonego projektu.

 Ta funkcja zwraca ścieżkę projektu nadrzędnego istniejącego projektu. W przypadku projektu głównego funkcja zwraca ścieżkę projektu, która została przekazana w (czyli tej samej głównej ścieżki projektu). Należy zauważyć, że ścieżka projektu jest ciągiem, który ma znaczenie tylko dla wtyczki formantu źródła.

 IDE jest przygotowany do zaakceptowania `lpAuxProjPath` zmian i parametrów, `lpUser` jak również. IDE będzie utrwalić te ciągi i przekazać je do [SccOpenProject,](../extensibility/sccopenproject-function.md) gdy użytkownik otworzy ten projekt w przyszłości. Te ciągi, w związku z tym, umożliwiają wtyczkę formantu źródła do śledzenia informacji, które muszą skojarzyć z projektem.

 Ta funkcja jest podobna do [SccGetProjPath](../extensibility/sccgetprojpath-function.md), z tą różnicą, że nie monituje użytkownika, aby wybrać projekt. Nigdy też nie tworzy nowego projektu, ale działa tylko z istniejącym projektem.

 Po `SccGetParentProjectPath` wywołaniu `lpProjPath` `lpAuxProjPath` i nie będzie pusty i będzie odpowiadać prawidłowego projektu. Te ciągi są zwykle odbierane przez IDE `SccGetProjPath` z poprzedniego wywołania funkcji.

 Argument `lpUser` jest nazwą użytkownika. IDE przekaże w tej samej nazwie użytkownika, `SccGetProjPath` który wcześniej otrzymał od funkcji, a wtyczka formantu źródła powinna używać nazwy jako domyślnej. Jeśli użytkownik ma już otwarte połączenie z wtyczką, wtyczka powinna spróbować wyeliminować wszelkie monity, aby upewnić się, że funkcja działa cicho. Jeśli jednak logowanie nie powiedzie się, wtyczka powinna monitować użytkownika o zalogowanie, a `lpUser`po otrzymaniu prawidłowego logowania przekazać nazwę z powrotem w . Ponieważ dodatek może zmienić ten ciąg, IDE zawsze przydziela`SCC_USER_LEN`bufor o rozmiarze ( +1). Jeśli ciąg zostanie zmieniony, nowy ciąg musi być prawidłową nazwą logowania (co najmniej tak samo prawidłową jak stary ciąg).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Uwagi techniczne dotyczące programu SccCreateSubProject i SccGetParentProjectPath
 Dodawanie rozwiązań i projektów do kontroli źródła zostało uproszczone w programie Visual Studio, aby zminimalizować liczbę monitów użytkownika o wybranie lokalizacji w systemie kontroli źródła. Te zmiany są aktywowane przez program Visual Studio, jeśli wtyczka kontroli źródła obsługuje obie nowe funkcje, [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) i `SccGetParentProjectPath` funkcji. Jednak następujący wpis rejestru może służyć do wyłączenia tych zmian i przywrócić do poprzedniego programu Visual Studio (Source Control Plug-in API w wersji 1.1) zachowanie:

 **[HKEY_CURRENT_USER\Oprogramowanie\Microsoft\VisualStudio\8.0\Kontrola źródła] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Jeśli ten wpis rejestru nie istnieje lub jest ustawiony na dword:00000000, `SccCreateSubProject``SccGetParentProjectPath`program Visual Studio próbuje użyć nowych funkcji i .

 Jeśli wpis rejestru jest ustawiony na dword:00000001, Visual Studio nie próbuje użyć tych nowych funkcji, a operacje dodawania do kontroli źródła działają tak, jak w poprzednich wersjach programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki sterowania źródłem](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
