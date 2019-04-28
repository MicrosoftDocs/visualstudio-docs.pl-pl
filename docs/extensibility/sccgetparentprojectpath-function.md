---
title: SccGetParentProjectPath Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e05b66f8168701b23c1638b35957777924f9d815
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433230"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath function
Ta funkcja określa ścieżkę projektu nadrzędny określonego projektu. Ta funkcja jest wywoływana, gdy użytkownik dodaje projekt programu Visual Studio do kontroli źródła.

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

[in] Wskaźnik kontekście wtyczki kontroli źródła.

 hWnd

[in] Uchwyt okna środowiska IDE, które wtyczka do kontroli źródła można użyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.

 lpUser

[out w] Nazwa użytkownika (maksymalnie SCC_USER_SIZE tym terminator o wartości NULL).

 lpProjPath

[in] Ciąg identyfikujący ścieżka projektu (maksymalnie SCC_PRJPATH_SIZE tym terminator o wartości NULL).

 lpAuxProjPath

[out w] Pomocnicze ciąg identyfikujący projekt (maksymalnie SCC_PRJPATH_SIZE tym terminator o wartości NULL).

 lpParentProjPath

[out w] Ciąg wyjściowy identyfikowanie ścieżka projektu nadrzędnego (maksymalnie SCC_PRJPATH_SIZE tym terminator o wartości NULL).

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Pomyślnie uzyskano ścieżka projektu nadrzędnego.|
|SCC_E_INITIALIZEFAILED|Nie można zainicjować projektu.|
|SCC_E_INVALIDUSER|Użytkownik może nie logują się do wtyczki kontroli źródła.|
|SCC_E_UNKNOWNPROJECT|Projekt jest nieznany wtyczka do kontroli źródła.|
|SCC_E_INVALIDFILEPATH|Ścieżka pliku nieprawidłowy lub nie do użytku.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji o zasoby. Ponowienie próby jest zalecane.|
|SCC_E_PROJSYNTAXERR|Składnia nieprawidłowy projekt.|
|SCC_E_CONNECTIONFAILURE|Problem z połączeniem Store.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Wystąpił nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Ta funkcja zwróci kod powodzenia lub niepowodzenia i, jeśli to się powiedzie, wypełnia zmiennej `lpParentProjPath` ze ścieżką pełną projektu do określonego projektu.

 Ta funkcja zwraca element nadrzędny, ścieżka projektu do istniejącego projektu. Dla projektu głównego, funkcja zwraca ścieżkę projektu, który został przekazany w (czyli tej samej ścieżce katalogu głównego projektu). Należy zauważyć, że ścieżka projektu jest ciągiem, który ma znaczenie tylko do wtyczka do kontroli źródła.

 Środowisko IDE jest przygotowana do zaakceptowania zmian wprowadzonych na `lpUser` i `lpAuxProjPath` również parametry. Środowisko IDE będzie zachować te ciągi i przekazywać je do [SccOpenProject](../extensibility/sccopenproject-function.md) po użytkownik otwiera ten projekt w przyszłości. Te ciągi, dlatego umożliwiają dla dodatku plug-in do śledzenia informacji wymaganych do skojarzenia z projektu kontroli źródła.

 Ta funkcja jest podobny do [SccGetProjPath](../extensibility/sccgetprojpath-function.md), z tą różnicą, że nie monituje użytkownika o wybranie projektu. Nigdy nie tworzy nowy projekt, ale działa tylko w przypadku istniejącego projektu.

 Gdy `SccGetParentProjectPath` jest wywoływana, `lpProjPath` i `lpAuxProjPath` nie jest pusty i będą odpowiadać prawidłowym projektem. Te ciągi są zazwyczaj odbierane przez środowisko IDE z poprzedniego wywołania `SccGetProjPath` funkcji.

 `lpUser` Argument jest nazwą użytkownika. IDE przejdzie w tej samej nazwy użytkownika, który poprzednio odbierał z `SccGetProjPath` funkcji i wtyczka do kontroli źródła, należy użyć nazwy jako domyślny. Jeśli użytkownik ma już otwartego połączenia przy użyciu wtyczki, wtyczka powinna spróbuj wyeliminować żadnych monitów, aby upewnić się, że funkcja działa w trybie dyskretnym. Jednakże, jeśli logowanie nie powiedzie się, wtyczka powinien zostać wyświetlony monit użytkownika dla nazwy logowania, a po odebraniu prawidłową nazwą logowania — dostęp próbny nazwę z powrotem w `lpUser`. Ponieważ wtyczki mogą zmienić ten ciąg, IDE będzie zawsze Przydziel bufor o rozmiarze (`SCC_USER_LEN`+ 1). Jeśli ciąg zostanie zmieniona, nowy ciąg musi być prawidłową nazwą logowania (co najmniej jako prawidłowe jako stary ciąg).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Uwagi techniczne SccCreateSubProject i SccGetParentProjectPath
 Dodawanie rozwiązania i projekty do kontroli źródła został uproszczony w programie Visual Studio, aby zminimalizować liczbę przypadków, gdy użytkownik jest monitowany o wybierz lokalizacje w systemie kontroli źródła. Zmiany te zostaną aktywowane przez program Visual Studio, jeśli wtyczka do kontroli źródła, obsługuje zarówno z nowych funkcji [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) i `SccGetParentProjectPath` funkcji. Jednak następujący wpis rejestru można wyłączyć te zmiany i przywrócić poprzednie zachowanie programu Visual Studio (źródło sterowania wtyczki interfejsu API w wersji 1.1):

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = dword: 00000001**

 Jeśli ten wpis rejestru nie istnieje lub ma wartość DWORD: 00000000, Visual Studio próbuje użyć nowych funkcji `SccCreateSubProject`i`SccGetParentProjectPath`.

 Jeśli wpis rejestru DWORD: 00000001 programu Visual Studio nie jest podejmowana próba użycia tych nowych funkcji, a operacje dodania do kontroli źródła działają podobnie jak w poprzednich wersjach programu Visual Studio.

## <a name="see-also"></a>Zobacz także
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)