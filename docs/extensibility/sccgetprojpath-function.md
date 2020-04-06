---
title: Funkcja SccGetProjPath | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 281787da3499c081fbbe6f59b7b8175a4dbf24d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700704"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath, funkcja
Ta funkcja monituje użytkownika o ścieżkę projektu, która jest ciągiem, który ma znaczenie tylko dla wtyczki formantu źródła. Jest wywoływana, gdy użytkownik jest:

- Tworzenie nowego projektu

- Dodawanie istniejącego projektu do kontroli wersji

- Próba znalezienia istniejącego projektu kontroli wersji

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccGetProjPath (
   LPVOID pvContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPSTR  lpProjName,
   LPSTR  lpLocalPath,
   LPSTR  lpAuxProjPath,
   BOOL   bAllowChangePath,
   LPBOOL pbNew
);
```

### <a name="parameters"></a>Parametry
 pvContext

[w] Struktura kontekstu wtyczki formantu źródła.

 Hwnd

[w] Dojście do okna IDE, którego wtyczka formantu źródła może używać jako element nadrzędny dla wszystkich okien dialogowych, które udostępnia.

 lpUżycie

[w, na zewnątrz] Nazwa użytkownika (nie przekracza SCC_USER_SIZE, w tym terminator NULL)

 lpProjName

[w, na zewnątrz] Nazwa projektu IDE, obszaru roboczego projektu lub pliku makefile (nie może przekraczać SCC_PRJPATH_SIZE, w tym terminator NULL).

 lpLocalPath (Ścieżka lokalna)

[w, na zewnątrz] Ścieżka robocza projektu. Jeśli `bAllowChangePath` `TRUE`tak, wtyczka formantu źródła może zmodyfikować ten ciąg (nie przekraczać _MAX_PATH, w tym null-terminator).

 lpAuxProjPath (lpAuxProjPath)

[w, na zewnątrz] Bufor dla zwróconej ścieżki projektu (nie przekracza SCC_PRJPATH_SIZE, w tym terminatora NULL).

 bAllowChangePath (Ścieżka zmian)

[w] Jeśli tak `TRUE`jest, wtyczka kontroli źródła może `lpLocalPath` monitować i modyfikować ciąg.

 pbNowy

[w, na zewnątrz] Wartość wchodząc wskazuje, czy utworzyć nowy projekt. Zwrócona wartość wskazuje na powodzenie tworzenia projektu:

|Dane|Interpretacja|
|--------------|--------------------|
|Prawda|Użytkownik może utworzyć nowy projekt.|
|FAŁSZ|Użytkownik nie może utworzyć nowego projektu.|

|Wychodzących|Interpretacja|
|--------------|--------------------|
|Prawda|Powstał nowy projekt.|
|FAŁSZ|Wybrano istniejący projekt.|

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Projekt został pomyślnie utworzony lub pobrany.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacją.|
|SCC_E_CONNECTIONFAILURE|Wystąpił problem podczas próby połączenia z systemem kontroli źródła.|
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Celem tej funkcji jest dla IDE do `lpProjName` `lpAuxProjPath`uzyskania parametrów i . Po wtyczki kontroli źródła monituje użytkownika o te informacje, przekazuje te dwa ciągi z powrotem do IDE. IDE utrzymuje te ciągi w pliku rozwiązania i przekazuje je do [SccOpenProject](../extensibility/sccopenproject-function.md) za każdym razem, gdy użytkownik otworzy ten projekt. Te ciągi umożliwiają dodatek do śledzenia informacji skojarzonych z projektem.

 Gdy funkcja jest wywoływana po raz pierwszy, `lpAuxProjPath` jest ustawiona na pusty ciąg. `lProjName`może być również pusta lub może zawierać nazwę projektu IDE, który wtyczka kontroli źródła może używać lub ignorować. Gdy funkcja pomyślnie zwraca, dodatek zwraca dwa odpowiednie ciągi. IDE nie zawiera żadnych założeń dotyczących tych ciągów, nie będzie ich używać i nie pozwoli użytkownikowi na ich modyfikowanie. Jeśli użytkownik chce zmienić ustawienia, IDE `SccGetProjPath` wywoła ponownie, przekazując te same wartości, które otrzymał poprzedni raz. Daje to pełną kontrolę nad tymi dwoma ciągami.

 For `lpUser`, IDE może przekazać w nazwie użytkownika lub może po prostu przekazać w wskaźniku do pustego ciągu. Jeśli istnieje nazwa użytkownika, wtyczka formantu źródła powinna używać jej jako domyślnej. Jeśli jednak żadna nazwa nie została przekazana lub jeśli logowanie nie powiodło się z daną nazwą, wtyczka powinna monitować użytkownika o zalogowanie się i przekazać nazwę z powrotem `lpUser` po otrzymaniu prawidłowego logowania. Ponieważ dodatek może zmienić ten ciąg, IDE zawsze przydziela`SCC_USER_LEN`bufor o rozmiarze ( +1).

> [!NOTE]
> Pierwsza akcja, która wykonuje IDE może być wywołanie `SccOpenProject` funkcji `SccGetProjPath` lub funkcji. W związku z tym `lpUser` oba mają identyczny parametr, który umożliwia wtyczkę kontroli źródła do logowania użytkownika w obu tych porach. Nawet jeśli powrót z funkcji wskazuje na błąd, wtyczka musi wypełnić ten ciąg prawidłową nazwą logowania.

 `lpLocalPath`to katalog, w którym użytkownik przechowuje projekt. Może to być pusty ciąg. Jeśli nie zdefiniowano katalogu (tak jak w przypadku użytkownika próbującego pobrać projekt z systemu `bAllowChangePath` kontroli `TRUE`źródła), a jeśli tak, wtyczka kontroli źródła może monitować użytkownika `lpLocalPath`o wprowadzenie danych lub użyć innej metody, aby umieścić własny ciąg w programie . Jeśli `bAllowChangePath` `FALSE`tak, wtyczka nie powinna zmieniać ciągu, ponieważ użytkownik już pracuje w określonym katalogu.

 Jeśli użytkownik tworzy nowy projekt, który ma być umieszczony pod kontrolą źródła, wtyczka kontroli źródła `SccGetProjPath` może nie faktycznie utworzyć go w systemie kontroli źródła w czasie jest wywoływana. Zamiast tego przekazuje ciąg wraz z wartością niezerową dla `pbNew`, wskazując, że projekt zostanie utworzony w systemie kontroli źródła.

 Na przykład jeśli użytkownik w Kreatorze **nowego projektu** w programie Visual Studio dodaje swój projekt do kontroli źródła, Visual Studio wywołuje tę funkcję, a dodatek określa, czy jest w porządku, aby utworzyć nowy projekt w systemie kontroli źródła, aby zawierać projekt programu Visual Studio. Jeśli użytkownik kliknie przycisk **Anuluj** przed ukończeniem pracy kreatora, projekt nigdy nie zostanie utworzony. Jeśli użytkownik kliknie **przycisk** `SccOpenProject`OK , `SCC_OPT_CREATEIFNEW`Visual Studio wywołuje , przekazywanie , a projekt kontrolowany przez źródło jest tworzony w tym czasie.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki sterowania źródłem](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
