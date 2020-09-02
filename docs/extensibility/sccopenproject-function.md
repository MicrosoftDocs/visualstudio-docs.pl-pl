---
title: Funkcja SccOpenProject | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
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

podczas Struktura kontekstu wtyczki kontroli źródła.

 Właściwość

podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.

 lpUser

[in. out] Nazwa użytkownika (nie przekroczenia SCC_USER_SIZE, w tym terminator o wartości NULL).

 lpProjName

podczas Ciąg identyfikujący nazwę projektu.

 lpLocalProjPath

podczas Ścieżka do folderu roboczego dla projektu.

 lpAuxProjPath

[in. out] Opcjonalny ciąg pomocniczy identyfikujący projekt (nie może przekroczyć SCC_AUXPATH_SIZE, łącznie z terminatorem wartości NULL).

 lpComment

podczas Dodaj komentarz do nowego projektu, który jest tworzony.

 lpTextOutProc

podczas Opcjonalna funkcja wywołania zwrotnego do wyświetlania tekstu wyjściowego z wtyczki kontroli źródła.

 flagiDW

podczas Informuje, czy należy utworzyć nowy projekt, jeśli projekt jest nieznany dla wtyczki kontroli źródła. Wartość może być kombinacją `SCC_OP_CREATEIFNEW` i `SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Sukces w otwieraniu projektu.|
|SCC_E_INITIALIZEFAILED|Nie można zainicjować projektu.|
|SCC_E_INVALIDUSER|Użytkownik nie mógł zalogować się do systemu kontroli źródła.|
|SCC_E_COULDNOTCREATEPROJECT|Projekt nie istniał przed wywołaniem;  `SCC_OPT_CREATEIFNEW` flaga została ustawiona, ale nie można utworzyć projektu.|
|SCC_E_PROJSYNTAXERR|Nieprawidłowa składnia projektu.|
|SCC_E_UNKNOWNPROJECT|Projekt jest nieznany dla wtyczki kontroli źródła, a `SCC_OPT_CREATEIFNEW` flaga nie została ustawiona.|
|SCC_E_INVALIDFILEPATH|Nieprawidłowa lub niezdatna do użycia ścieżka pliku.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zalecana jest ponowna próba.|
|SCC_E_NONSPECFICERROR|Nieokreślony błąd; System kontroli źródła nie został zainicjowany.|

## <a name="remarks"></a>Uwagi
 IDE może przejść do nazwy użytkownika ( `lpUser` ) lub po prostu przekazać wskaźnik do pustego ciągu. Jeśli istnieje nazwa użytkownika, wtyczka do kontroli źródła powinna używać go jako domyślnego. Jeśli jednak nazwa nie została przeniesiona lub logowanie nie powiodło się o podanej nazwie, wtyczka powinna monitować użytkownika o zalogowanie się i zwróci poprawną nazwę w `lpUser` momencie odebrania prawidłowej nazwy logowania, `.` ponieważ wtyczka może zmienić ciąg nazwy użytkownika, IDE zawsze przydzieli bufor rozmiaru ( `SCC_USER_LEN` + 1 lub SCC_USER_SIZE, który obejmuje miejsce dla terminatora o wartości null).

> [!NOTE]
> Pierwszą akcją, jaką może wykonać środowisko IDE, może być wywołanie `SccOpenProject` funkcji lub [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Z tego powodu oba z nich mają identyczny `lpUser` parametr.

 `lpAuxProjPath` i `lpProjName` są odczytywane z pliku rozwiązania lub są zwracane z wywołania `SccGetProjPath` funkcji. Parametry te zawierają ciągi, które są skojarzone z wtyczką kontroli źródła z projektem i są zrozumiałe tylko dla wtyczki. Jeśli takie ciągi nie znajdują się w pliku rozwiązania, a użytkownik nie otrzymał monitu o przeglądanie (która zwróci ciąg za pomocą `SccGetProjPath` funkcji), IDE przekazuje puste ciągi dla obu `lpAuxProjPath` i `lpProjName` , i oczekuje, że te wartości zostaną zaktualizowane przez wtyczkę, gdy ta funkcja zwróci wartość.

 `lpTextOutProc` jest wskaźnikiem do funkcji wywołania zwrotnego dostarczonej przez IDE do wtyczki kontroli źródła na potrzeby wyświetlania danych wyjściowych wyników polecenia. Ta funkcja wywołania zwrotnego została szczegółowo opisana w [lpTextOutProc](../extensibility/lptextoutproc.md).

> [!NOTE]
> Jeśli wtyczka kontroli źródła zamierza korzystać z tego, musi ustawić `SCC_CAP_TEXTOUT` flagę w [SccInitialize](../extensibility/sccinitialize-function.md). Jeśli ta flaga nie została ustawiona lub IDE nie obsługuje tej funkcji, `lpTextOutProc` będzie `NULL` .

 `dwFlags`Parametr kontroluje wynik w przypadku, gdy otwarty projekt nie istnieje. Składa się z dwóch bitflags `SCC_OP_CREATEIFNEW` i `SCC_OP_SILENTOPEN` . Jeśli otwarty projekt już istnieje, funkcja po prostu otwiera projekt i zwraca `SCC_OK` . Jeśli projekt nie istnieje i jeśli `SCC_OP_CREATEIFNEW` flaga jest włączona, wtyczka do kontroli źródła może utworzyć projekt w systemie kontroli źródła, otworzyć go i zwrócić `SCC_OK` . Jeśli projekt nie istnieje i jeśli `SCC_OP_CREATEIFNEW` flaga jest wyłączona, wtyczka powinna sprawdzać `SCC_OP_SILENTOPEN` flagę. Jeśli ta flaga nie jest włączona, wtyczka może monitować użytkownika o nazwę projektu. Jeśli ta flaga jest włączona, wtyczka powinna po prostu zwrócić `SCC_E_UNKNOWNPROJECT` .

## <a name="calling-order"></a>Kolejność wywoływania
 W normalnych warunkach zdarzeń [SccInitialize](../extensibility/sccinitialize-function.md) zostanie wywołana jako pierwsza, aby otworzyć sesję kontroli źródła. Sesja może składać się z wywołania, a `SccOpenProject` następnie innych wywołań funkcji interfejsu API Plug-in kontroli źródła i zostanie zakończona z wywołaniem do [SccCloseProject](../extensibility/scccloseproject-function.md). Takie sesje mogą powtarzać się kilka razy przed wywołaniem [SccUninitialize](../extensibility/sccuninitialize-function.md) .

 Jeśli wtyczka do kontroli źródła ustawia `SCC_CAP_REENTRANT` bit w `SccInitialize` , powyższą sekwencję sesji można powtarzać wielokrotnie. Różne `pvContext` struktury śledzą różne sesje, w których każda `pvContext` z nich jest skojarzona z jednym otwartym projektem w danym momencie. Na podstawie `pvContext` parametru wtyczka może określić, który projekt jest przywoływany w konkretnym wywołaniu. Jeśli bit możliwości `SCC_CAP_REENTRANT` nie jest ustawiony, wtyczki kontroli źródła nonreentrant są ograniczone do pracy z wieloma projektami.

> [!NOTE]
> `SCC_CAP_REENTRANT`Bit został wprowadzony w wersji 1,1 interfejsu API wtyczki kontroli źródła. Nie jest on ustawiony lub jest ignorowany w wersji 1,0 i założono, że wszystkie wtyczki kontroli źródła wersji 1,0 są nonreentrant.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Ograniczenia długości ciągów](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
