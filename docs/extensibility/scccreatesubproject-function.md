---
title: Funkcja SccCreateSubProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3ed763635d5629400c70c53497c7a798e0ac38f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943130"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject, funkcja
Ta funkcja tworzy podprojekt o podanej nazwie w istniejącym projekcie nadrzędnym określonym przez `lpParentProjPath` argument.

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
 pContext

podczas Wskaźnik kontekstu wtyczki kontroli źródła.

 Właściwość

podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.

 lpUser

[in. out] Nazwa użytkownika (do SCC_USER_SIZE, w tym terminator o wartości NULL).

 lpParentProjPath

podczas Ciąg identyfikujący ścieżkę projektu nadrzędnego (do SCC_PRJPATH_SIZE, w tym terminator o wartości NULL).

 lpSubProjName

podczas Sugerowana nazwa podprojektu (do SCC_PRJPATH_SIZE, w tym terminator o wartości NULL).

 lpAuxProjPath

[in. out] Ciąg pomocniczy identyfikujący projekt (do SCC_PRJPATH_SIZE, w tym terminator o wartości NULL).

 lpSubProjPath

[in. out] Ciąg wyjściowy identyfikujący ścieżkę dla podprojektu (do SCC_PRJPATH_SIZE, w tym terminator o wartości NULL).

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Podprojekt został pomyślnie utworzony.|
|SCC_E_INITIALIZEFAILED|Nie można zainicjować projektu nadrzędnego.|
|SCC_E_INVALIDUSER|Użytkownik nie mógł zalogować się do systemu kontroli źródła.|
|SCC_E_COULDNOTCREATEPROJECT|Nie można utworzyć podprojektu.|
|SCC_E_PROJSYNTAXERR|Nieprawidłowa składnia projektu.|
|SCC_E_UNKNOWNPROJECT|Projekt nadrzędny jest nieznany dla wtyczki kontroli źródła.|
|SCC_E_INVALIDFILEPATH|Nieprawidłowa lub niezdatna do użycia ścieżka pliku.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zalecana jest ponowna próba.|
|SCC_E_CONNECTIONFAILURE|Wystąpił problem z połączeniem wtyczki kontroli źródła.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Jeśli podprojekt o tej nazwie już istnieje, funkcja może zmienić nazwę domyślną, aby utworzyć unikatową, na przykład dodając do niej znak "_ \<number> ". Obiekt wywołujący musi być przygotowany do akceptowania zmian w `lpUser` , `lpSubProjPath` i `lpAuxProjPath` . `lpSubProjPath`Argumenty i `lpAuxProjPath` są następnie używane w wywołaniu [SccOpenProject](../extensibility/sccopenproject-function.md). Nie powinny być modyfikowane przez obiekt wywołujący po powrocie. Te ciągi umożliwiają użycie wtyczki kontroli źródła w celu śledzenia informacji wymaganych do skojarzenia z projektem. W środowisku IDE wywołującym nie będą wyświetlane te dwa parametry po powrocie, ponieważ wtyczka może użyć sformatowanego ciągu, który może być nieodpowiedni do wyświetlania. Funkcja zwraca kod sukcesu lub niepowodzenia, a jeśli to się powiedzie, wypełnia zmienną `lpSubProjPath` pełną ścieżką projektu do nowego projektu.

 Ta funkcja jest podobna do [SccGetProjPath](../extensibility/sccgetprojpath-function.md), z tą różnicą, że w sposób dyskretny tworzy projekt, a nie monituje użytkownika o wybranie go. Gdy `SccCreateSubProject` Funkcja jest wywoływana `lpParentProjName` i `lpAuxProjPath` nie będzie pusta i będzie odpowiadać prawidłowemu projektowi. Te ciągi są zwykle odbierane przez środowisko IDE od poprzedniego wywołania `SccGetProjPath` funkcji lub [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).

 `lpUser`Argument jest nazwą użytkownika. Środowisko IDE zostanie przekazane tej samej nazwie użytkownika, z której wcześniej dotarła `SccGetProjPath` , a wtyczka do kontroli źródła powinna używać nazwy jako domyślnej. Jeśli użytkownik ma już otwarte połączenie z wtyczką, wtyczka powinna próbować wyeliminować wszelkie monity, aby upewnić się, że funkcja działa w trybie dyskretnym. Jeśli jednak logowanie nie powiedzie się, wtyczka powinien monitować użytkownika o zalogowanie i, gdy odbierze prawidłowe logowanie, przekaż nazwę ponownie `lpUser` . Ponieważ wtyczka może zmienić ten ciąg, IDE zawsze przydzieli bufor rozmiaru (SCC_USER_LEN + 1 lub SCC_USER_SIZE, który obejmuje miejsce dla terminatora o wartości null). Jeśli ciąg zostanie zmieniony, nowy ciąg musi być prawidłową nazwą logowania (co najmniej jako stary ciąg).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Uwagi techniczne dotyczące SccCreateSubProject i SccGetParentProjectPath
 Dodawanie rozwiązań i projektów do kontroli źródła zostało uproszczone w programie Visual Studio, aby zminimalizować liczbę prób wyświetlenia monitu użytkownika o wybranie lokalizacji w systemie kontroli źródła. Te zmiany są aktywowane przez program Visual Studio, jeśli wtyczka kontroli źródła obsługuje obie nowe funkcje `SccCreateSubProject` i `SccGetParentProjectPath` . Aby wyłączyć te zmiany i przywrócić poprzednią wersję programu Visual Studio (interfejs API dodatku plug-in kontroli źródła w wersji 1,1), można jednak użyć następującego wpisu rejestru:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001**

 Jeśli ten wpis rejestru nie istnieje lub jest ustawiony na wartość DWORD: 00000000, program Visual Studio próbuje użyć nowych funkcji `SccCreateSubProject` i `SccGetParentProjectPath` .

 Jeśli wpis rejestru jest ustawiony na wartość DWORD: 00000001, program Visual Studio nie próbuje użyć tych nowych funkcji i operacje dodawania do kontroli źródła działają tak jak w poprzednich wersjach programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
