---
description: Ta funkcja monituje użytkownika o ścieżkę projektu, która jest ciągiem zrozumiałym tylko dla wtyczki kontroli źródła.
title: SccGetProjPath, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 93266464249b8de037a618bab55ede31988384cb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901074"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath, funkcja
Ta funkcja monituje użytkownika o ścieżkę projektu, która jest ciągiem zrozumiałym tylko dla wtyczki kontroli źródła. Jest on wywoływany, gdy użytkownik jest:

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

[in] Struktura kontekstu wtyczki kontroli źródła.

 Hwnd

[in] Dojście do okna IDE, które wtyczka kontroli źródła może używać jako elementu nadrzędnego dla wszystkich okien dialogowych, które udostępnia.

 lpUser

[in, out] Nazwa użytkownika (nie może przekraczać SCC_USER_SIZE, łącznie z terminatorem NULL)

 lpProjName

[in, out] Nazwa projektu IDE, obszaru roboczego projektu lub pliku makefile (nie może przekraczać SCC_PRJPATH_SIZE, w tym terminator NULL).

 lpLocalPath

[in, out] Ścieżka robocza projektu. Jeśli wartość to , wtyczka kontroli kodu źródłowego może modyfikować ten ciąg (aby nie przekraczać _MAX_PATH, w tym `bAllowChangePath` `TRUE` wartość null-terminator).

 lpAuxProjPath

[in, out] Bufor dla zwracanej ścieżki projektu (aby nie przekraczać SCC_PRJPATH_SIZE, w tym terminator NULL).

 bAllowChangePath

[in] Jeśli tak `TRUE` jest, wtyczka kontroli źródła może monitować o ciąg i modyfikować `lpLocalPath` go.

 pbNowy

[in, out] Wartość przychodzącą wskazuje, czy utworzyć nowy projekt. Zwrócona wartość wskazuje powodzenie tworzenia projektu:

|Dane|Interpretacja|
|--------------|--------------------|
|TRUE|Użytkownik może utworzyć nowy projekt.|
|FALSE|Użytkownik może nie tworzyć nowego projektu.|

|Wychodzących|Interpretacja|
|--------------|--------------------|
|TRUE|Utworzono nowy projekt.|
|FALSE|Wybrano istniejący projekt.|

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła dla tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Projekt został pomyślnie utworzony lub pobrany.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana.|
|SCC_E_ACCESSFAILURE|Występuje problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub zdyskusją.|
|SCC_E_CONNECTIONFAILURE|Podczas próby nawiązania połączenia z systemem kontroli źródła występuje problem.|
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Celem tej funkcji jest uzyskanie przez ideę parametrów `lpProjName` i `lpAuxProjPath` . Gdy wtyczka kontroli źródła monituje użytkownika o te informacje, przekazuje te dwa ciągi z powrotem do środowiska IDE. Ide utrwala te ciągi w pliku rozwiązania i przekazuje je do [projektu SccOpenProject](../extensibility/sccopenproject-function.md) za każdym razem, gdy użytkownik otworzy ten projekt. Te ciągi umożliwiają wtyczce śledzenie informacji skojarzonych z projektem.

 Gdy funkcja jest wywoływana po raz pierwszy, `lpAuxProjPath` jest ustawiana na pusty ciąg. `lProjName` może być również pusty lub może zawierać nazwę projektu IDE, której wtyczka kontroli źródła może używać lub ignorować. Po pomyślnym powrocie funkcji wtyczka zwraca dwa odpowiadające im ciągi. Ide nie wprowadza żadnych założeń dotyczących tych ciągów, nie będzie ich używać i nie zezwoli użytkownikowi na ich modyfikowanie. Jeśli użytkownik chce zmienić ustawienia, ide zostanie ponownie wywołany, przekazując te same wartości, `SccGetProjPath` które otrzymał w poprzednim czasie. Dzięki temu wtyczka ma pełną kontrolę nad tymi dwoma ciągami.

 W przypadku funkcji ide może przekazać nazwę użytkownika lub po prostu przekazać wskaźnik do `lpUser` pustego ciągu. Jeśli istnieje nazwa użytkownika, wtyczka kontroli źródła powinna używać jej jako domyślnej. Jeśli jednak nazwa nie została przekazana lub jeśli logowanie nie powiodło się z podaną nazwą, wtyczka powinna monitować użytkownika o nazwę logowania i przekazywać ją z powrotem po otrzymaniu prawidłowego identyfikatora `lpUser` logowania. Ponieważ wtyczka może zmienić ten ciąg, ide zawsze przydzieli bufor o rozmiarze ( `SCC_USER_LEN` +1).

> [!NOTE]
> Pierwszą akcją, która wykonuje ide, może być wywołanie funkcji `SccOpenProject` lub `SccGetProjPath` funkcji. W związku z tym oba mają identyczny parametr, który umożliwia wtyczce kontroli źródła logowanie użytkownika `lpUser` w obu przypadkach. Nawet jeśli zwrot z funkcji wskazuje błąd, wtyczka musi wypełnić ten ciąg prawidłową nazwą logowania.

 `lpLocalPath` to katalog, w którym użytkownik przechowuje projekt. Może to być pusty ciąg. Jeśli nie ma aktualnie zdefiniowanego katalogu (tak jak w przypadku użytkownika próbującego pobrać projekt z systemu kontroli źródła), a jeśli jest , wtyczka kontroli źródła może monitować użytkownika o wprowadzenie danych lub użyć innej metody, aby umieścić własny ciąg w pliku `bAllowChangePath` `TRUE` `lpLocalPath` . Jeśli wartość to , wtyczka nie `bAllowChangePath` powinna zmieniać ciągu, ponieważ użytkownik `FALSE` pracuje już w określonym katalogu.

 Jeśli użytkownik tworzy nowy projekt do kontroli źródła, wtyczka kontroli kodu źródłowego może nie tworzyć go w systemie kontroli źródła w tym czasie jest `SccGetProjPath` wywoływana. Zamiast tego przekazuje on z powrotem ciąg wraz z wartością niezerową dla , wskazującą, że projekt zostanie utworzony w `pbNew` systemie kontroli źródła.

 Jeśli na przykład użytkownik  w kreatorze Nowy projekt w programie Visual Studio dodaje swój projekt do kontroli źródła, program Visual Studio wywołuje tę funkcję, a wtyczka określa, czy można utworzyć nowy projekt w systemie kontroli źródła, który będzie zawierał projekt Visual Studio. Jeśli użytkownik kliknie przycisk **Anuluj** przed ukończeniem pracy kreatora, projekt nigdy nie zostanie utworzony. Jeśli użytkownik kliknie przycisk **OK**, program Visual Studio , przekazując , i w tym czasie zostanie utworzony projekt kontrolowany `SccOpenProject` przez `SCC_OPT_CREATEIFNEW` źródło.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
