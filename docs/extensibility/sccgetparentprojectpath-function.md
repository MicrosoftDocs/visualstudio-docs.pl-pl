---
description: Ta funkcja określa ścieżkę projektu nadrzędnego określonego projektu.
title: SccGetParentProjectPath, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 13a0a77808004c7bc8f408bbf34a3ed4f0715b36
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900138"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath, funkcja
Ta funkcja określa ścieżkę projektu nadrzędnego określonego projektu. Ta funkcja jest wywoływana, gdy użytkownik dodaje projekt Visual Studio do kontroli źródła.

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

[in] Wskaźnik kontekstu wtyczki kontroli źródła.

 Hwnd

[in] Dojście do okna IDE, które wtyczka kontroli źródła może używać jako elementu nadrzędnego dla wszystkich okien dialogowych, które udostępnia.

 lpUser

[in, out] Nazwa użytkownika (do SCC_USER_SIZE łącznie z terminatorem NULL).

 lpProjPath

[in] Ciąg identyfikujący ścieżkę projektu (do SCC_PRJPATH_SIZE, w tym terminator NULL).

 lpAuxProjPath

[in, out] Ciąg pomocniczy identyfikujący projekt (do SCC_PRJPATH_SIZE, w tym terminator NULL).

 lpParentProjPath

[in, out] Ciąg wyjściowy identyfikujący nadrzędną ścieżkę projektu (do SCC_PRJPATH_SIZE, w tym terminator NULL).

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła dla tej funkcji zwraca jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Pomyślnie uzyskano nadrzędną ścieżkę projektu.|
|SCC_E_INITIALIZEFAILED|Nie można zainicjować projektu.|
|SCC_E_INVALIDUSER|Użytkownik nie mógł zalogować się do wtyczki kontroli źródła.|
|SCC_E_UNKNOWNPROJECT|Projekt jest nieznany dla wtyczki kontroli źródła.|
|SCC_E_INVALIDFILEPATH|Nieprawidłowa lub nienadatna do użytku ścieżka pliku.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_ACCESSFAILURE|Występuje problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub zdyskulacji. Zaleca się ponawianie próby.|
|SCC_E_PROJSYNTAXERR|Nieprawidłowa składnia projektu.|
|SCC_E_CONNECTIONFAILURE|Problem z połączeniem magazynu.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Ta funkcja zwraca kod powodzenia lub niepowodzenia i, jeśli to się powiedzie, wypełnia zmienną pełną ścieżką `lpParentProjPath` projektu do określonego projektu.

 Ta funkcja zwraca nadrzędną ścieżkę projektu istniejącego projektu. W przypadku projektu głównego funkcja zwraca ścieżkę projektu, która została przekazana (czyli tę samą ścieżkę projektu głównego). Należy pamiętać, że ścieżka projektu jest ciągiem zrozumiałym tylko dla wtyczki kontroli źródła.

 Ide jest przygotowane do akceptowania zmian `lpUser` w parametrach `lpAuxProjPath` i . Ide będzie utrwalać te ciągi i przekazywać je do [projektu SccOpenProject,](../extensibility/sccopenproject-function.md) gdy użytkownik otworzy ten projekt w przyszłości. W związku z tym te ciągi zapewniają wtyczkę kontroli źródła w celu śledzenia informacji, które musi skojarzyć z projektem.

 Ta funkcja jest podobna do [funkcji SccGetProjPath,](../extensibility/sccgetprojpath-function.md)z tą różnicą, że nie monituje użytkownika o wybranie projektu. Ponadto nigdy nie tworzy nowego projektu, ale działa tylko z istniejącym projektem.

 Gdy `SccGetParentProjectPath` zostanie wywołana, `lpProjPath` i nie będzie pusta i będzie `lpAuxProjPath` odpowiadać prawidłowemu projektowi. Te ciągi są zwykle odbierane przez ideę z poprzedniego wywołania `SccGetProjPath` funkcji.

 Argument `lpUser` jest nazwą użytkownika. Ide przekaże tę samą nazwę użytkownika, która została wcześniej odebrana z funkcji, a wtyczka kontroli źródła powinna używać nazwy `SccGetProjPath` jako domyślnej. Jeśli użytkownik ma już otwarte połączenie z wtyczką, wtyczka powinna próbować wyeliminować wszelkie monity, aby upewnić się, że funkcja działa w trybie dyskretnym. Jeśli jednak logowanie nie powiedzie się, wtyczka powinna monitować użytkownika o zalogowanie i po otrzymaniu prawidłowego identyfikatora logowania przekazać nazwę z powrotem w `lpUser` . Ponieważ wtyczka może zmienić ten ciąg, ide zawsze przydzieli bufor o rozmiarze ( `SCC_USER_LEN` +1). Jeśli ciąg zostanie zmieniony, nowy ciąg musi być prawidłową nazwą logowania (co najmniej tak prawidłową jak stary ciąg).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Uwagi techniczne dotyczące SccCreateSubProject i SccGetParentProjectPath
 Dodawanie rozwiązań i projektów do kontroli źródła zostało uproszczone w systemie Visual Studio w celu zminimalizowania liczby monitów o wybranie lokalizacji w systemie kontroli źródła przez użytkownika. Te zmiany są aktywowane przez Visual Studio, jeśli wtyczka kontroli źródła obsługuje obie nowe funkcje: [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) i `SccGetParentProjectPath` funkcję . Jednak następującego wpisu rejestru można użyć do wyłączenia tych zmian i przywrócenia poprzedniego zachowania Visual Studio (wtyczki kontroli kodu źródłowego interfejsu API w wersji 1.1):

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Jeśli ten wpis rejestru nie istnieje lub jest ustawiony na dword:000000000, Visual Studio próbuje użyć nowych funkcji i `SccCreateSubProject` `SccGetParentProjectPath` .

 Jeśli wpis rejestru jest ustawiony na dword:00000001, program Visual Studio nie próbuje użyć tych nowych funkcji ani operacji dodawania do kontroli źródła działa tak jak w poprzednich wersjach Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
