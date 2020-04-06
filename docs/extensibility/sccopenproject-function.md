---
title: Funkcja SccOpenProject | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fbf566e593bb1ddbc31c70de1570d746a14fbdcf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700570"
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

[w] Struktura kontekstu wtyczki formantu źródła.

 Hwnd

[w] Dojście do okna IDE, którego wtyczka formantu źródła może używać jako element nadrzędny dla wszystkich okien dialogowych, które udostępnia.

 lpUżycie

[w, na zewnątrz] Nazwa użytkownika (nie przekracza SCC_USER_SIZE, w tym terminator NULL).

 lpProjName

[w] Ciąg identyfikujący nazwę projektu.

 lpLocalProjPath (Ścieżka lpLocalProjPath)

[w] Ścieżka do folderu roboczego dla projektu.

 lpAuxProjPath (lpAuxProjPath)

[w, na zewnątrz] Opcjonalny ciąg pomocniczy identyfikujący projekt (nie przekraczający SCC_AUXPATH_SIZE, w tym terminator NULL).

 lpKomentuj

[w] Komentarz do nowego projektu, który jest tworzony.

 Lptextoutproc

[w] Opcjonalna funkcja wywołania zwrotnego do wyświetlania wyjścia tekstowego z wtyczki formantu źródłowego.

 Dwflags

[w] Sygnalizuje, czy nowy projekt musi zostać utworzony, jeśli projekt jest nieznany wtyce kontroli źródła. Wartość może być `SCC_OP_CREATEIFNEW` kombinacją i`SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Sukces w otwarciu projektu.|
|SCC_E_INITIALIZEFAILED|Nie można zainicjować projektu.|
|SCC_E_INVALIDUSER|Użytkownik nie może zalogować się do systemu kontroli źródła.|
|SCC_E_COULDNOTCREATEPROJECT|Projekt nie istniał przed wezwaniem;  flaga `SCC_OPT_CREATEIFNEW` została ustawiona, ale nie można było utworzyć projektu.|
|SCC_E_PROJSYNTAXERR|Nieprawidłowa składnia projektu.|
|SCC_E_UNKNOWNPROJECT|Projekt jest nieznany wtyczki kontroli źródła i `SCC_OPT_CREATEIFNEW` flaga nie została ustawiona.|
|SCC_E_INVALIDFILEPATH|Nieprawidłowa lub niezrozumiasowalna ścieżka pliku.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zaleca się ponowną próbę.|
|SCC_E_NONSPECFICERROR|Niespecyficzna awaria; system kontroli źródła nie został zainicjowany.|

## <a name="remarks"></a>Uwagi
 IDE może przekazać w nazwie`lpUser`użytkownika ( ) lub może po prostu przekazać w wskaźniku do pustego ciągu. Jeśli istnieje nazwa użytkownika, wtyczka formantu źródła powinna używać jej jako domyślnej. Jeśli jednak żadna nazwa nie została przekazana lub jeśli logowanie nie powiodło się z daną nazwą, `lpUser` wtyczka powinna monitować użytkownika o zalogowanie się i zwróci prawidłową nazwę po otrzymaniu prawidłowego logowania`.` Ponieważ dodatek może zmienić ciąg nazwy użytkownika, IDE zawsze przydziela bufor o rozmiarze (`SCC_USER_LEN`+1 lub SCC_USER_SIZE, który zawiera miejsce dla terminatora nullator).

> [!NOTE]
> Pierwsza akcja, do wykonania może być wymagana funkcja `SccOpenProject` IDE, może być wywołaniem funkcji lub [ścieżki SccGetProjPath.](../extensibility/sccgetprojpath-function.md) Z tego powodu oba mają `lpUser` identyczny parametr.

 `lpAuxProjPath`i`lpProjName` są odczytywane z pliku rozwiązania lub są `SccGetProjPath` zwracane z wywołania funkcji. Parametry te zawierają ciągi, które wtyczka formantu źródła kojarzy z projektem i mają znaczenie tylko dla wtyczki. Jeśli nie takie ciągi są w pliku rozwiązania i użytkownik nie został poproszony o `SccGetProjPath` przeglądanie (który zwróci ciąg `lpAuxProjPath` za `lpProjName`pośrednictwem funkcji), IDE przekazuje puste ciągi dla obu i , i oczekuje, że te wartości zostaną zaktualizowane przez wtyczkę, gdy ta funkcja zwraca.

 `lpTextOutProc`jest wskaźnikiem do funkcji wywołania zwrotnego dostarczonej przez IDE do wtyczki kontroli źródła w celu wyświetlenia danych wyjściowych polecenia. Ta funkcja wywołania zwrotnego jest szczegółowo opisana w [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

> [!NOTE]
> Jeśli wtyczka kontroli źródła zamierza skorzystać z tego, musi `SCC_CAP_TEXTOUT` mieć ustawioną flagę w [SccInitialize](../extensibility/sccinitialize-function.md). Jeśli ta flaga nie została ustawiona lub IDE `lpTextOutProc` nie `NULL`obsługuje tej funkcji, będzie .

 Parametr `dwFlags` kontroluje wynik w przypadku, gdy projekt jest otwarty obecnie nie istnieje. Składa się z dwóch bitflags, `SCC_OP_CREATEIFNEW` i `SCC_OP_SILENTOPEN`. Jeśli otwarty projekt już istnieje, funkcja po prostu `SCC_OK`otwiera projekt i zwraca . Jeśli projekt nie istnieje i `SCC_OP_CREATEIFNEW` jeśli flaga jest wł., wtyczka kontroli źródła może utworzyć projekt `SCC_OK`w systemie kontroli źródła, otworzyć go i zwrócić . Jeśli projekt nie istnieje, a `SCC_OP_CREATEIFNEW` flaga jest wyłączona, wtyczka `SCC_OP_SILENTOPEN` powinna następnie sprawdzić flagę. Jeśli ta flaga nie jest wł., dodatek może monitować użytkownika o nazwę projektu. Jeśli ta flaga jest wł., `SCC_E_UNKNOWNPROJECT`wtyczka powinna po prostu powrócić .

## <a name="calling-order"></a>Zamówienie telefoniczne
 W normalnym przebiegu zdarzeń [SccInitialize](../extensibility/sccinitialize-function.md) zostanie wywołana jako pierwsza, aby otworzyć sesję kontroli źródła. Sesja może składać się `SccOpenProject`z wywołania , a następnie innych wywołań funkcji interfejsu API wtyczki źródła i zakończy się wywołaniem [SccCloseProject](../extensibility/scccloseproject-function.md). Takie sesje mogą być powtarzane kilka razy, zanim [SccUninitialize zostanie wywołana.](../extensibility/sccuninitialize-function.md)

 Jeśli wtyczka formantu `SCC_CAP_REENTRANT` źródła `SccInitialize`ustawia bit w , wówczas powyższa sekwencja sesji może być powtarzana wiele razy równolegle. Różne `pvContext` struktury śledzą różne sesje, `pvContext` w których każda jest skojarzona z jednym otwartym projektem naraz. Na podstawie`pvContext` parametru wtyczki można określić, który projekt odwołuje się w danym wywołaniu. Jeśli bit `SCC_CAP_REENTRANT` możliwości nie jest ustawiony, nonreentrant wtyczki kontroli źródła są ograniczone w ich zdolność do pracy z wieloma projektami.

> [!NOTE]
> Bit `SCC_CAP_REENTRANT` został wprowadzony w wersji 1.1 interfejsu API wtyczki kontroli źródła. Nie jest ustawiona lub jest ignorowana w wersji 1.0, a wszystkie wtyczki kontroli źródła w wersji 1.0 są uważane za niereentranta.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Ograniczenia długości ciągów](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
