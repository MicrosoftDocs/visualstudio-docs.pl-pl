---
description: Ta funkcja określa ścieżkę projektu nadrzędnego określonego projektu.
title: Funkcja SccGetParentProjectPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e624d8765da65dc6231c0128e87ffd9d6cdf848d
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220615"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath, funkcja
Ta funkcja określa ścieżkę projektu nadrzędnego określonego projektu. Ta funkcja jest wywoływana, gdy użytkownik dodaje projekt programu Visual Studio do kontroli źródła.

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
 pContext

podczas Wskaźnik kontekstu wtyczki kontroli źródła.

 Właściwość

podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.

 lpUser

[in. out] Nazwa użytkownika (do SCC_USER_SIZE, w tym terminator o wartości NULL).

 lpProjPath

podczas Ciąg identyfikujący ścieżkę projektu (do SCC_PRJPATH_SIZE, w tym terminator o wartości NULL).

 lpAuxProjPath

[in. out] Ciąg pomocniczy identyfikujący projekt (do SCC_PRJPATH_SIZE, w tym terminator o wartości NULL).

 lpParentProjPath

[in. out] Ciąg wyjściowy identyfikujący ścieżkę projektu nadrzędnego (do SCC_PRJPATH_SIZE, w tym terminator o wartości NULL).

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Ścieżka projektu nadrzędnego została pomyślnie uzyskana.|
|SCC_E_INITIALIZEFAILED|Nie można zainicjować projektu.|
|SCC_E_INVALIDUSER|Użytkownik nie mógł zalogować się do wtyczki kontroli źródła.|
|SCC_E_UNKNOWNPROJECT|Projekt jest nieznany dla wtyczki kontroli źródła.|
|SCC_E_INVALIDFILEPATH|Nieprawidłowa lub niezdatna do użycia ścieżka pliku.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zalecana jest ponowna próba.|
|SCC_E_PROJSYNTAXERR|Nieprawidłowa składnia projektu.|
|SCC_E_CONNECTIONFAILURE|Problem z połączeniem magazynu.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Ta funkcja zwraca kod sukcesu lub niepowodzenia, a jeśli to się powiedzie, wypełnia zmienną `lpParentProjPath` pełną ścieżką projektu do określonego projektu.

 Ta funkcja zwraca ścieżkę projektu nadrzędnego istniejącego projektu. W przypadku projektu głównego funkcja zwraca ścieżkę projektu, która została przeniesiona (to jest taka sama ścieżka projektu głównego). Należy zauważyć, że ścieżka projektu jest ciągiem, który jest zrozumiały tylko dla wtyczki kontroli źródła.

 IDE jest przygotowana do akceptowania zmian `lpUser` `lpAuxProjPath` parametrów i. IDE będzie utrzymywać te ciągi i przekazać je do [SccOpenProject](../extensibility/sccopenproject-function.md) , gdy użytkownik otworzy ten projekt w przyszłości. W związku z tym te ciągi umożliwiają użycie wtyczki kontroli źródła do śledzenia informacji potrzebnych do skojarzenia z projektem.

 Ta funkcja jest podobna do [SccGetProjPath](../extensibility/sccgetprojpath-function.md), z tą różnicą, że nie monituje użytkownika o wybranie projektu. Również nigdy nie tworzy nowego projektu, ale działa tylko z istniejącym projektem.

 Gdy `SccGetParentProjectPath` jest wywoływana, `lpProjPath` i `lpAuxProjPath` nie będzie puste i będzie odpowiadać prawidłowemu projektowi. Te ciągi są zwykle odbierane przez środowisko IDE od poprzedniego wywołania `SccGetProjPath` funkcji.

 `lpUser`Argument jest nazwą użytkownika. IDE zostanie przekazane tej samej nazwie użytkownika, która wcześniej została odebrana z `SccGetProjPath` funkcji, a wtyczka do kontroli źródła powinna używać nazwy jako domyślnej. Jeśli użytkownik ma już otwarte połączenie z wtyczką, wtyczka powinna próbować wyeliminować wszelkie monity, aby upewnić się, że funkcja działa w trybie dyskretnym. Jeśli jednak logowanie nie powiedzie się, wtyczka powinien monitować użytkownika o zalogowanie i, gdy odbierze prawidłowe logowanie, przekaż nazwę ponownie `lpUser` . Ponieważ wtyczka może zmienić ten ciąg, IDE zawsze przydzieli bufor rozmiaru ( `SCC_USER_LEN` + 1). Jeśli ciąg zostanie zmieniony, nowy ciąg musi być prawidłową nazwą logowania (co najmniej jako stary ciąg).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Uwagi techniczne dotyczące SccCreateSubProject i SccGetParentProjectPath
 Dodawanie rozwiązań i projektów do kontroli źródła zostało uproszczone w programie Visual Studio, aby zminimalizować liczbę prób wyświetlenia monitu użytkownika o wybranie lokalizacji w systemie kontroli źródła. Te zmiany są aktywowane przez program Visual Studio, jeśli wtyczka kontroli źródła obsługuje obie nowe funkcje, [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) i `SccGetParentProjectPath` funkcję. Można jednak użyć następującego wpisu rejestru, aby wyłączyć te zmiany i przywrócić poprzednią wersję programu Visual Studio (interfejs API dodatku plug-in kontroli źródła w wersji 1,1):

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001**

 Jeśli ten wpis rejestru nie istnieje lub jest ustawiony na wartość DWORD: 00000000, program Visual Studio próbuje użyć nowych funkcji `SccCreateSubProject` i `SccGetParentProjectPath` .

 Jeśli wpis rejestru jest ustawiony na wartość DWORD: 00000001, program Visual Studio nie próbuje użyć tych nowych funkcji i operacje dodawania do kontroli źródła działają tak jak w poprzednich wersjach programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
