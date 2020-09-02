---
title: Funkcja SccGetProjPath | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700704"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath, funkcja
Ta funkcja monituje użytkownika o ścieżkę projektu, która jest ciągiem, który jest zrozumiały tylko dla wtyczki kontroli źródła. Jest wywoływana, gdy użytkownik jest:

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

podczas Struktura kontekstu wtyczki kontroli źródła.

 Właściwość

podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.

 lpUser

[in. out] Nazwa użytkownika (nie przekroczenia SCC_USER_SIZE, łącznie z terminatorem wartości NULL)

 lpProjName

[in. out] Nazwa projektu IDE, obszaru roboczego projektu lub pliku reguł programu make (nie do przekroczenia SCC_PRJPATH_SIZE, łącznie z terminatorem wartości NULL).

 lpLocalPath

[in. out] Ścieżka robocza projektu. Jeśli `bAllowChangePath` tak `TRUE` , wtyczka do kontroli źródła może zmodyfikować ten ciąg (nie przekroczyć _MAX_PATH, łącznie z terminatorem o wartości null).

 lpAuxProjPath

[in. out] Bufor dla zwracanej ścieżki projektu (nie może przekroczyć SCC_PRJPATH_SIZE, łącznie z terminatorem wartości NULL).

 bAllowChangePath

podczas W takim przypadku `TRUE` wtyczka do kontroli źródła może monitować o podanie i zmodyfikować `lpLocalPath` ciąg.

 pbNew

[in. out] Wartość w obszarze wskazuje, czy ma zostać utworzony nowy projekt. Zwracana wartość wskazuje na pomyślne utworzenie projektu:

|Dane|Interpretacja|
|--------------|--------------------|
|TRUE|Użytkownik może utworzyć nowy projekt.|
|FALSE|Użytkownik nie może utworzyć nowego projektu.|

|Przeznaczony|Interpretacja|
|--------------|--------------------|
|TRUE|Utworzono nowy projekt.|
|FALSE|Wybrano istniejący projekt.|

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Projekt został pomyślnie utworzony lub pobrany.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją.|
|SCC_E_CONNECTIONFAILURE|Wystąpił problem podczas próby nawiązania połączenia z systemem kontroli źródła.|
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Celem tej funkcji jest, aby środowisko IDE uzyskało parametry `lpProjName` i `lpAuxProjPath` . Gdy wtyczka do kontroli źródła będzie monitował użytkownika o te informacje, przekazuje te dwa ciągi z powrotem do IDE. IDE utrzymuje te ciągi w pliku rozwiązania i przekazuje je do [SccOpenProject](../extensibility/sccopenproject-function.md) za każdym razem, gdy użytkownik otworzy ten projekt. Te ciągi umożliwiają usłudze Plug-in śledzenie informacji skojarzonych z projektem.

 Gdy funkcja jest wywoływana po raz pierwszy, `lpAuxProjPath` jest ustawiona na pusty ciąg. `lProjName` może być również pusta lub może zawierać nazwę projektu IDE, która może być używana lub ignorowana przez wtyczkę kontroli źródła. Po pomyślnym powrocie funkcji Wtyczka zwraca dwa odpowiednie ciągi. IDE nie tworzy żadnych założeń dotyczących tych ciągów, nie będzie ich używać i nie zezwoli użytkownikowi na ich modyfikowanie. Jeśli użytkownik chce zmienić ustawienia, środowisko IDE będzie ponownie wywoływało `SccGetProjPath` , przekazując te same wartości, które otrzymały w poprzednim czasie. Dzięki temu wtyczka ma pełną kontrolę nad tymi dwoma ciągami.

 W przypadku `lpUser` środowiska IDE może przekazać nazwę użytkownika lub po prostu przekazać wskaźnik do pustego ciągu. Jeśli istnieje nazwa użytkownika, wtyczka do kontroli źródła powinna używać go jako domyślnego. Jeśli jednak nazwa nie została przekazana lub logowanie nie powiodło się o podanej nazwie, wtyczka powinna monitować użytkownika o nazwę logowania i przekazać ją z powrotem w `lpUser` przypadku otrzymania prawidłowej nazwy logowania. Ponieważ wtyczka może zmienić ten ciąg, IDE zawsze przydzieli bufor rozmiaru ( `SCC_USER_LEN` + 1).

> [!NOTE]
> Pierwszą akcją wykonywaną przez środowisko IDE może być wywołanie `SccOpenProject` funkcji lub `SccGetProjPath` funkcji. W związku z tym oba z nich mają identyczny `lpUser` parametr, który umożliwia włączenie wtyczki kontroli źródła w dowolnym momencie. Nawet jeśli powrót z funkcji wskazuje na awarię, wtyczka musi wypełnić ten ciąg prawidłową nazwą logowania.

 `lpLocalPath` jest katalogiem, w którym użytkownik zachowuje projekt. Może być pustym ciągiem. Jeśli nie ma obecnie zdefiniowanego katalogu (jak w przypadku, gdy użytkownik próbuje pobrać projekt z systemu kontroli źródła) i jeśli `bAllowChangePath` tak `TRUE` , wtyczka do kontroli źródła może monitować użytkownika o dane wejściowe lub użyć innej metody, aby umieścić własny ciąg w programie `lpLocalPath` . Jeśli `bAllowChangePath` jest `FALSE` , wtyczka nie powinna zmieniać ciągu, ponieważ użytkownik pracuje już w określonym katalogu.

 Jeśli użytkownik tworzy nowy projekt, który ma zostać umieszczony pod kontrolą źródła, wtyczka do kontroli źródła może nie utworzyć go w systemie kontroli źródła w momencie `SccGetProjPath` wywołania. Zamiast tego przekazuje ciąg wraz z wartością różną od zera dla `pbNew` , wskazując, że projekt zostanie utworzony w systemie kontroli źródła.

 Na przykład, jeśli użytkownik w kreatorze **nowego projektu** w programie Visual Studio dodaje swój projekt do kontroli źródła, program Visual Studio wywołuje tę funkcję, a wtyczka określa, czy można utworzyć nowy projekt w systemie kontroli źródła, aby zawierał projekt programu Visual Studio. Jeśli użytkownik kliknie **przycisk Anuluj** przed ukończeniem działania kreatora, projekt nigdy nie zostanie utworzony. Jeśli użytkownik kliknie przycisk **OK**, `SccOpenProject` w tym momencie zostanie utworzony program Visual Studio Calls, Pass in `SCC_OPT_CREATEIFNEW` oraz projekt z kontrolą źródła.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
