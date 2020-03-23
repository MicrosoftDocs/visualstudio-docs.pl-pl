---
title: NazwaProfile | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NameProfile
- NameProfileA
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d9f0c9a3259186e1581a4673cdc18d1554e92b3c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778495"
---
# <a name="nameprofile"></a>NameProfile
Funkcja `NameProfile` przypisuje ciąg do określonego procesu lub wątku.

 Interfejs API NameProfile jest dostępny tylko do profilowania instrumentacji. Interfejs API NameProfile nie jest obsługiwany do profilowania próbkowania.

## <a name="syntax"></a>Składnia

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(
                                   LPCTSTR pszName,
                                   PROFILE_CONTROL_LEVEL Level,
                                   unsigned int dwId);
```

#### <a name="parameters"></a>Parametry
 `pszName`

 Nazwa elementu profilowania. Nazwa jest nieprawidłowa (co powoduje, że nameprofileA zwraca NAME_ERROR_INVALID_NAME), jeśli:

- Wskaźnik przekazany do NameProfileA jest wartością NULL

- Dane ciągu pszName zaczynają się od liczby

- Dane ciągu pszName zawiera spację

- Dane ciągu pszName zawierają dowolny z następujących znaków: ,;. '~!@#$%^&*()=[]{}&#124;\\?/<>

  `Level`

  Wskazuje poziom profilu, do którego można zastosować zbieranie danych o wydajności. Następujące **PROFILE_CONTROL_LEVEL** wartości mogą służyć do wskazania jednego z trzech poziomów, do których można zastosować zbieranie danych o wydajności:

|Moduł wyliczający|Opis|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|Ustawienie poziomu globalnego wpływa na wszystkie procesy i wątki w przebiegu profilowania.|
|PROFILE_PROCESSLEVEL|Ustawienie poziomu procesu wpływa na wszystkie wątki, które są częścią określonego procesu.|
|PROFILE_THREADLEVEL|Ustawienie poziom profilowania wątku wpływa na określony wątek.|

 `dwId`

 Identyfikator poziomu profilowania. Użyj identyfikatora procesu lub wątku, który jest generowany przez system.

## <a name="property-valuereturn-value"></a>Wartość właściwości/wartość zwracana
 Funkcja wskazuje sukces lub niepowodzenie przy użyciu **PROFILE_COMMAND_STATUS** wyliczenia. Zwracana wartość może być jedną z następujących wartości:

|Moduł wyliczający|Opis|
|----------------|-----------------|
|NAME_ERROR_ID_NOEXIST|Określony element profilowania nie istnieje.|
|NAME_ERROR_INVALID_NAME|Nazwa jest nieprawidłowa.|
|NAME_ERROR_LEVEL_NOEXIST|Określony poziom profilu nie istnieje.|
|NAME_ERROR_NO_SUPPORT|Określona operacja nie jest obsługiwana.|
|NAME_ERROR_OUTOFMEMORY|Pamięć nie była dostępna do nagrywania zdarzenia.|
|NAME_ERROR_REDEFINITION|Nazwa została już przypisana do elementu profilu. Nazwa w tej funkcji jest ignorowana.|
|NAME_ERROR_TEXTTRUNCATED|Tekst nazwy przekroczył 32 znaki, w tym znak null i dlatego został obcięty.|
|NAME_OK|Nazwa została zarejestrowana pomyślnie.|

## <a name="remarks"></a>Uwagi
 Tylko jedna nazwa może być przypisana do każdego procesu lub wątku. Po nazwie elementu profilowania kolejne wywołania NameProfile dla tego elementu są ignorowane.

 Jeśli ta sama nazwa jest nadana do różnych wątków lub procesów, raport będzie zawierać dane ze wszystkich elementów na tym poziomie o tej nazwie.

 Jeśli określisz proces lub wątek inny niż bieżący, należy upewnić się, że zainicjowano i zaczął działać przed nadawanie mu nazwy. W przeciwnym razie NameProfile metoda kończy się niepowodzeniem.

> [!IMPORTANT]
> Funkcje interfejsu API CreateProcess() i CreateThread() mogą powrócić przed zainicjowaniem wątku lub procesu.

## <a name="net-framework-equivalent"></a>Odpowiednik programu .NET Framework
 *Plik dll Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Informacje o funkcjach

|||
|-|-|
|**Nagłówka**|Uwzględnij *VSPerf.h*|
|**Biblioteka**|Użyj *pliku VSPerf.lib*|
|**Unicode**|Zaimplementowano `NameProfileW` jako `NameProfileA` (Unicode) i (ANSI).|

## <a name="example"></a>Przykład
 Poniższy kod ilustruje wywołanie funkcji NameProfile. W przykładzie przyjęto użycie makr ciągów Win32 i ustawień kompilatora dla interfejsu ANSI w celu ustalenia, czy kod wywołuje funkcję z włączoną funkcją ANSI.

```cpp
void ExerciseNameProfile()
{
    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Create and initialize variables to pass to
    // ExerciseNameProfile.  The value of this
    // parameter is based on the needs of the code;
    // and for the sake of simplicity in this example,
    // the variable is assigned an arbitrary value.
    TCHAR * profileName = TEXT("ExerciseNameProfile");

    // Declare enumeration to hold result of call to
    // ExerciseNameProfle.
    PROFILE_COMMAND_STATUS nameResult;

    nameResult =  NameProfile(
        profileName,
        PROFILE_GLOBALLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("NameProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, nameResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Zobacz też
- [Odwołanie do interfejsu API profilera programu Visual Studio (natywne)](../profiling/visual-studio-profiler-api-reference-native.md)
