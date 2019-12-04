---
title: NameProfile | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778495"
---
# <a name="nameprofile"></a>NameProfile
Funkcja `NameProfile` przypisuje ciąg do określonego procesu lub wątku.

 Interfejs API NameProfile jest dostępny tylko dla profilowania Instrumentacji. Interfejs API NameProfile nie jest obsługiwany w przypadku profilowania próbkowania.

## <a name="syntax"></a>Składnia

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(
                                   LPCTSTR pszName,
                                   PROFILE_CONTROL_LEVEL Level,
                                   unsigned int dwId);
```

#### <a name="parameters"></a>Parametry
 `pszName`

 Nazwa elementu profilowania. Nazwa jest nieprawidłowa (wynik NameProfileA zwraca NAME_ERROR_INVALID_NAME), jeśli:

- Wskaźnik przesłany do NameProfileA jest wartością NULL

- Dane ciągu pszName rozpoczynają się od liczby

- Dane ciągu pszName zawierają spację

- Ciąg danych pszName zawiera jeden z następujących znaków:,;. "~! @ # $% ^ & * () = []{}&#124;\\?/< >

  `Level`

  Wskazuje poziom profilu, do którego można zastosować zbieranie danych wydajności. Poniższe wartości **PROFILE_CONTROL_LEVEL** mogą służyć do wskazania jednego z trzech poziomów, do których można zastosować zbieranie danych o wydajności:

|Liczeni|Opis|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|Globalne ustawienie poziomu ma wpływ na wszystkie procesy i wątki w przebiegu profilowania.|
|PROFILE_PROCESSLEVEL|Ustawienie poziomu procesu wpływa na wszystkie wątki, które są częścią określonego procesu.|
|PROFILE_THREADLEVEL|Ustawienie poziomu profilowania wątku ma wpływ na określony wątek.|

 `dwId`

 Identyfikator poziomu profilowania. Użyj procesu lub identyfikatora wątku, który jest generowany przez system.

## <a name="property-valuereturn-value"></a>Wartość właściwości/zwracana wartość
 Funkcja wskazuje powodzenie lub niepowodzenie przy użyciu wyliczenia **PROFILE_COMMAND_STATUS** . Zwracana wartość może być jedną z następujących:

|Liczeni|Opis|
|----------------|-----------------|
|NAME_ERROR_ID_NOEXIST|Określony element profilowania nie istnieje.|
|NAME_ERROR_INVALID_NAME|Nazwa jest nieprawidłowa.|
|NAME_ERROR_LEVEL_NOEXIST|Określony poziom profilu nie istnieje.|
|NAME_ERROR_NO_SUPPORT|Określona operacja nie jest obsługiwana.|
|NAME_ERROR_OUTOFMEMORY|Pamięć nie jest dostępna do rejestrowania zdarzenia.|
|NAME_ERROR_REDEFINITION|Nazwa została już przypisana do elementu profilu. Nazwa w tej funkcji jest ignorowana.|
|NAME_ERROR_TEXTTRUNCATED|Tekst nazwy przekracza 32 znaków, w tym znak null, a więc został obcięty.|
|NAME_OK|Nazwa została pomyślnie zarejestrowana.|

## <a name="remarks"></a>Uwagi
 Do każdego procesu lub wątku można przypisać tylko jedną nazwę. Gdy element profilowania ma nazwę, kolejne wywołania NameProfile dla tego elementu zostaną zignorowane.

 Jeśli taka sama nazwa jest określona dla różnych wątków lub procesów, raport będzie zawierać dane ze wszystkich elementów na tym poziomie o tej nazwie.

 Jeśli określisz proces lub wątek inny niż bieżący, musisz upewnić się, że został on zainicjowany i uruchomiony przed napisaniem nazwy. W przeciwnym razie metoda NameProfile kończy się niepowodzeniem.

> [!IMPORTANT]
> Funkcje API CreateProcess () i onthread () mogą zwrócić przed zainicjowaniem wątku lub procesu.

## <a name="net-framework-equivalent"></a>.NET Framework równoważne
 *Microsoft. VisualStudio. Profiler. dll*

## <a name="function-information"></a>Informacje o funkcji

|||
|-|-|
|**Nagłówki**|Uwzględnij *VSPerf. h*|
|**Biblioteki**|Użyj *VSPerf. lib*|
|**Unicode**|Zaimplementowane jako `NameProfileW` (Unicode) i `NameProfileA` (ANSI).|

## <a name="example"></a>Przykład
 Poniższy kod ilustruje wywołanie funkcji NameProfile. W przykładzie założono użycie makr ciągu Win32 i ustawień kompilatora dla ANSI, aby określić, czy kod wywołuje funkcję z obsługą ANSI.

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

## <a name="see-also"></a>Zobacz także
- [Dokumentacja interfejsu API programu Visual Studio profiler (natywna)](../profiling/visual-studio-profiler-api-reference-native.md)
