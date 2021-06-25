---
description: Ta funkcja otwiera istniejący projekt kontroli źródła lub tworzy nowy.
title: SccOpenProject, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1326319b483aa707b77e0d7142d816b01fc7d3b1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902400"
---
# <a name="sccopenproject-function"></a>SccOpenProject, funkcja
Ta funkcja otwiera istniejący projekt kontroli źródła lub tworzy nowy.

## <a name="syntax"></a>Składnia

```cpp
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

[in] Struktura kontekstu wtyczki kontroli źródła.

 Hwnd

[in] Dojście do okna IDE, które wtyczka kontroli źródła może używać jako elementu nadrzędnego dla wszystkich okien dialogowych, które zawiera.

 lpUser

[in, out] Nazwa użytkownika (nie może przekraczać SCC_USER_SIZE, w tym terminator NULL).

 lpProjName

[in] Ciąg identyfikujący nazwę projektu.

 lpLocalProjPath

[in] Ścieżka do folderu roboczego projektu.

 lpAuxProjPath

[in, out] Opcjonalny ciąg pomocniczy identyfikujący projekt (nie może przekraczać SCC_AUXPATH_SIZE, w tym terminator NULL).

 lpComment

[in] Komentarz do nowego projektu, który jest tworzony.

 Lptextoutproc

[in] Opcjonalna funkcja wywołania zwrotnego do wyświetlania tekstowych danych wyjściowych z wtyczki kontroli źródła.

 Dwflags

[in] Sygnalizuje, czy należy utworzyć nowy projekt, jeśli projekt jest nieznany do wtyczki kontroli źródła. Wartość może być kombinacją `SCC_OP_CREATEIFNEW` elementów i `SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła dla tej funkcji zwraca jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Powodzenie otwierania projektu.|
|SCC_E_INITIALIZEFAILED|Nie można zainicjować projektu.|
|SCC_E_INVALIDUSER|Użytkownik nie mógł zalogować się do systemu kontroli źródła.|
|SCC_E_COULDNOTCREATEPROJECT|Projekt nie istniał przed wywołaniem ;  Flaga `SCC_OPT_CREATEIFNEW` została ustawiona, ale nie można utworzyć projektu.|
|SCC_E_PROJSYNTAXERR|Nieprawidłowa składnia projektu.|
|SCC_E_UNKNOWNPROJECT|Projekt jest nieznany dla wtyczki kontroli źródła i `SCC_OPT_CREATEIFNEW` flaga nie została ustawiona.|
|SCC_E_INVALIDFILEPATH|Nieprawidłowa lub nienadatna do użytku ścieżka pliku.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_ACCESSFAILURE|Występuje problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub z powodu wystąpienia problemów z siecią. Zaleca się ponawianie próby.|
|SCC_E_NONSPECFICERROR|Nieokreślony błąd; system kontroli źródła nie został zainicjowany.|

## <a name="remarks"></a>Uwagi
 Ide może przekazać nazwę użytkownika ( ) lub po prostu przekazać `lpUser` wskaźnik do pustego ciągu. Jeśli istnieje nazwa użytkownika, wtyczka kontroli źródła powinna używać jej jako domyślnej. Jeśli jednak żadna nazwa nie została przekazana lub jeśli logowanie nie powiodło się z podaną nazwą, wtyczka powinna monitować użytkownika o zalogowanie się i zwróci prawidłową nazwę w pliku po otrzymaniu prawidłowego identyfikatora logowania Ponieważ wtyczka może zmienić ciąg nazwy użytkownika, idee zawsze przydzieli bufor rozmiaru `lpUser` `.` (+1 lub SCC_USER_SIZE, który zawiera miejsce dla terminatora wartości `SCC_USER_LEN` null).

> [!NOTE]
> Pierwszą akcją, która może być wymagana do wykonania środowiska IDE, może być wywołanie funkcji `SccOpenProject` lub [SccGetProjPath.](../extensibility/sccgetprojpath-function.md) Z tego powodu oba mają identyczny `lpUser` parametr.

 `lpAuxProjPath` i `lpProjName` są odczytywane z pliku rozwiązania lub są zwracane z wywołania `SccGetProjPath` funkcji. Te parametry zawierają ciągi, które wtyczka kontroli źródła kojarzy z projektem i są zrozumiałe tylko dla wtyczki. Jeśli w pliku rozwiązania nie ma żadnych takich ciągów, a użytkownik nie zostanie poproszony o przeglądanie (co zwróci ciąg za pośrednictwem funkcji), idee IDE przekazuje puste ciągi dla zarówno i , jak i oczekuje, że te wartości zostaną zaktualizowane przez wtyczkę po zwróceniu przez tę `SccGetProjPath` `lpAuxProjPath` `lpProjName` funkcję.

 `lpTextOutProc` jest wskaźnikiem do funkcji wywołania zwrotnego dostarczonej przez ideę do wtyczki kontroli źródła na potrzeby wyświetlania danych wyjściowych wyników polecenia. Ta funkcja wywołania zwrotnego jest szczegółowo opisana w [temacie LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

> [!NOTE]
> Jeśli wtyczka kontroli źródła zamierza z tego skorzystać, musi mieć ustawioną flagę w pliku `SCC_CAP_TEXTOUT` [SccInitialize.](../extensibility/sccinitialize-function.md) Jeśli ta flaga nie została ustawiona lub jeśli idee nie obsługuje tej funkcji, `lpTextOutProc` będzie `NULL` to .

 Parametr `dwFlags` kontroluje wynik w przypadku, gdy otwierany projekt nie istnieje obecnie. Składa się z dwóch bitflags i `SCC_OP_CREATEIFNEW` `SCC_OP_SILENTOPEN` . Jeśli otwierany projekt już istnieje, funkcja po prostu otwiera projekt i zwraca wartość `SCC_OK` . Jeśli projekt nie istnieje, a flaga jest wł., wtyczka kontroli źródła może utworzyć projekt w systemie kontroli źródła, otworzyć go `SCC_OP_CREATEIFNEW` i zwrócić . `SCC_OK` Jeśli projekt nie istnieje, a flaga jest wyłączona, wtyczka powinna sprawdzić `SCC_OP_CREATEIFNEW` `SCC_OP_SILENTOPEN` flagę . Jeśli ta flaga nie jest wł., wtyczka może monitować użytkownika o nazwę projektu. Jeśli ta flaga jest wł., wtyczka powinna po prostu zwrócić `SCC_E_UNKNOWNPROJECT` .

## <a name="calling-order"></a>Wywoływanie kolejności
 W normalnym przebiegu zdarzeń najpierw zostanie wywołana wartość [SccInitialize,](../extensibility/sccinitialize-function.md) aby otworzyć sesję kontroli źródła. Sesja może składać się z wywołania funkcji , a następnie innych wywołań funkcji interfejsu API wtyczki kontroli kodu źródłowego i zakończy się wywołaniem funkcji `SccOpenProject` [SccCloseProject.](../extensibility/scccloseproject-function.md) Takie sesje mogą być powtarzane kilka razy przed [wywołaniu SccUninitialize.](../extensibility/sccuninitialize-function.md)

 Jeśli wtyczka kontroli źródła ustawia bit w pliku , powyższe sekwencje sesji mogą być powtarzane `SCC_CAP_REENTRANT` `SccInitialize` wiele razy równolegle. Różne `pvContext` struktury śledzą różne sesje, w których każda z nich jest skojarzona z jednym otwartym projektem na `pvContext` raz. Na podstawie parametru wtyczka może określić, który projekt jest `pvContext` przywołytywowany w każdym konkretnym wywołaniu. Jeśli bit możliwości nie `SCC_CAP_REENTRANT` jest ustawiony, niereententalne wtyczki kontroli źródła mają ograniczoną możliwość pracy z wieloma projektami.

> [!NOTE]
> Bit `SCC_CAP_REENTRANT` został wprowadzony w wersji 1.1 interfejsu API wtyczki kontroli kodu źródłowego. Nie jest ona ustawiona lub jest ignorowana w wersji 1.0, a wszystkie wtyczki kontroli źródła w wersji 1.0 są zakładane jako nieoczywistne.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Ograniczenia długości ciągów](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
