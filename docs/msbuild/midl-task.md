---
title: MIDL — zadanie | Microsoft Docs
description: Dowiedz się więcej o zadaniu MSBuild MIDL, które otacza narzędzie kompilatora Microsoft Interface Definition Language (MIDL), midl.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.TypeLibFormat
- vc.task.midl
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (C++), MIDL task
- MIDL task (MSBuild (C++))
ms.assetid: 727efa8c-3336-40b8-8bef-ae6cbd77a422
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eadec17e7c5221f0b169d38b15b9601cec746fa4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094981"
---
# <a name="midl-task"></a>MIDL — Zadanie

Zawija Microsoft Interface Definition Language narzędzia kompilatora (MIDL), *midl.exe*. Aby uzyskać więcej informacji, zobacz [MIDL — dokumentacja wiersza polecenia](/windows/desktop/Midl/midl-command-line-reference).

## <a name="parameters"></a>Parametry

 Poniżej opisano parametry zadania **MIDL** . Większość parametrów zadań i kilku zestawów parametrów odpowiada opcji wiersza polecenia.

- **AdditionalIncludeDirectories**

     Opcjonalny parametr **String []** .

     Dodaje katalog do listy katalogów przeszukiwanych pod kątem importowanych plików IDL, dołączonych plików nagłówkowych i plików konfiguracji aplikacji (ACF).

     Aby uzyskać więcej informacji, zobacz **/i** opcja w [MIDL wiersza polecenia](/windows/desktop/Midl/midl-command-line-reference).

- **AdditionalOptions**

     Opcjonalny parametr **ciągu** .

     Lista opcji wiersza polecenia. Na przykład/ \<option1>  / \<option2>  / \<option#> . Użyj tego parametru, aby określić opcje wiersza polecenia, które nie są reprezentowane przez żaden inny parametr zadania MIDL.

     Aby uzyskać więcej informacji, zobacz [MIDL — dokumentacja wiersza polecenia](/windows/desktop/Midl/midl-command-line-reference).

- **ApplicationConfigurationMode**

     Opcjonalny parametr **logiczny** .

     Jeśli `true` , program pozwala używać niektórych słów kluczowych ACF w pliku IDL.

     Aby uzyskać więcej informacji, zobacz opcję **/app_config** w [dokumentacji wiersza polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **ClientStubFile**

     Opcjonalny parametr **ciągu** .

     Określa nazwę pliku szczątkowego klienta dla interfejsu RPC.

     Aby uzyskać więcej informacji, zobacz **/cstub** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference). Zobacz również parametr **ServerStubFile** w tej tabeli.

- **CPreprocessOptions**

     Opcjonalny parametr **ciągu** .

     Określa opcje do przekazania do preprocesora C/C++. Określ rozdzielaną spacją listę opcji preprocesora. Musi zawierać `/E` opcję.

     Aby uzyskać więcej informacji, zobacz opcję **/cpp_opt** w [dokumentacji wiersza polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **DefaultCharType**

     Opcjonalny parametr **ciągu** .

     Określa domyślny typ znaku, który kompilator języka C będzie używał do kompilowania wygenerowanego kodu.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**Opatrzon**|**/char podpisany**|
    |**Bajt**|**/char bez znaku**|
    |**ASCII**|**/char ascii7**|

     Aby uzyskać więcej informacji, zobacz **/char** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **DllDataFileName**

     Opcjonalny parametr **ciągu** .

     Określa nazwę pliku dla wygenerowanego pliku *dlldata* dla biblioteki DLL proxy.

     Aby uzyskać więcej informacji, zobacz **/dlldata** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **EnableErrorChecks**

     Opcjonalny parametr **ciągu** .

     Określa typ błędu podczas sprawdzania, czy generowane wycinki będą wykonywane w czasie wykonywania.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**Brak**|**/Error brak**|
    |**EnableCustom**|**/Error**|
    |**Wszystko**|**/Error wszystko**|

     Aby uzyskać więcej informacji, zobacz **/Error** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckAllocations**

     Opcjonalny parametr **logiczny** .

     Jeśli jest `true` , sprawdź, czy nie występują błędy braku pamięci.

     Aby uzyskać więcej informacji, zobacz opcja **alokacji/Error** w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckBounds**

     Opcjonalny parametr **logiczny** .

     Jeśli `true` , sprawdza rozmiar zgodnych i zróżnicowanych tablic względem specyfikacji długości transmisji.

     Aby uzyskać więcej informacji, zobacz **/error bounds_check** opcja w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckEnumRange**

     Opcjonalny parametr **logiczny** .

     Jeśli `true` , sprawdza, czy wartości wyliczeniowe znajdują się w dozwolonym zakresie.

     Aby uzyskać więcej informacji, zobacz **/Error enum** w pomocy wiersza polecenia (**/?**) dla *midl.exe*.

- **ErrorCheckRefPointers**

     Opcjonalny parametr **logiczny** .

     Jeśli `true` jest, sprawdź, czy żadne wskaźniki odwołania o wartości null nie są przenoszone do procedury pośredniczącej klienta.

     Aby uzyskać więcej informacji, zobacz **/Error ref** Option in [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckStubData**

     Opcjonalny parametr **logiczny** .

     Jeśli `true` , generuje element zastępczy, który przechwytuje wyjątki po stronie serwera i propaguje je z powrotem do klienta programu.

     Aby uzyskać więcej informacji, zobacz **/error stub_data** opcja w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateClientFiles**

     Opcjonalny parametr **ciągu** .

     Określa, czy kompilator generuje pliki źródłowe C po stronie klienta dla interfejsu RPC.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**Brak**|**/Client brak**|
    |**Szkieletu**|**/Client**|

     Aby uzyskać więcej informacji, zobacz **/Client** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateServerFiles**

     Opcjonalny parametr **ciągu** .

     Określa, czy kompilator generuje pliki źródłowe C po stronie serwera dla interfejsu RPC.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**Brak**|**/Server brak**|
    |**Szkieletu**|**/Server — stub**|

     Aby uzyskać więcej informacji, zobacz opcja **/Server** w [MIDL w wierszu polecenia](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateStublessProxies**

     Opcjonalny parametr **logiczny** .

     Jeśli `true` , program generuje w pełni interpretowane obiekty pośredniczące wraz z niezastępczymi serwerami proxy dla interfejsów obiektów.

     Aby uzyskać więcej informacji, zobacz **/Oicf** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateTypeLibrary**

     Opcjonalny parametr **logiczny** .

     Jeśli `true` plik biblioteki typów (*. tlb*) nie jest generowany.

     Aby uzyskać więcej informacji, zobacz **/notlb** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **HeaderFileName**

     Opcjonalny parametr **ciągu** .

     Określa nazwę wygenerowanego pliku nagłówkowego.

     Aby uzyskać więcej informacji, zobacz opcja **/h** lub **/header** w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **IgnoreStandardIncludePath**

     Opcjonalny parametr **logiczny** .

     Jeśli `true` zadanie MIDL przeszukuje tylko katalogi określone za pomocą przełącznika **AdditionalIncludeDirectories** i ignoruje bieżący katalog i katalogi określone przez ZMIENNĄ środowiskową INCLUDE.

     Aby uzyskać więcej informacji, zobacz opcję **/no_def_idir** w [dokumentacji wiersza polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **InterfaceIdentifierFileName**

     Opcjonalny parametr **ciągu** .

     Określa nazwę *pliku identyfikatora interfejsu* dla interfejsu com. Zastępuje domyślną nazwę uzyskaną przez dodanie "_i. c" do nazwy pliku IDL.

     Aby uzyskać więcej informacji, zobacz **/IID** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **LocaleID**

     Opcjonalny parametr **int** .

     Określa *identyfikator ustawień regionalnych* , który umożliwia używanie znaków międzynarodowych w plikach wejściowych, nazwach plików i ścieżkach katalogów. Określ identyfikator ustawień regionalnych dziesiętnych.

     Aby uzyskać więcej informacji, zobacz **/LCID** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference). Zobacz również [identyfikatory ustawień regionalnych](/windows/desktop/intl/locale-identifiers).

- **MkTypLibCompatible**

     Opcjonalny parametr **logiczny** .

     Jeśli `true` , wymaga formatu pliku wejściowego, aby był zgodny z *mktyplib.exe* wersja 2,03.

     Aby uzyskać więcej informacji, zobacz **/mktyplib203** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference). Zobacz też [składnię pliku ODL](/previous-versions/windows/desktop/automat/odl-file-syntax) w witrynie MSDN.

- **OutputDirectory**

     Opcjonalny parametr **ciągu** .

     Określa domyślny katalog, w którym zadanie MIDL zapisuje pliki wyjściowe.

     Aby uzyskać więcej informacji, zobacz opcję **/out** w [MIDL wiersza polecenia](/windows/desktop/Midl/midl-command-line-reference).

- **PreprocessorDefinitions**

     Opcjonalny parametr **String []** .

     Określa co najmniej jedną *definicję*; oznacza to, że nazwa i wartość opcjonalna, które mają być przenoszone do preprocesora C, zgodnie z `#define` dyrektywą. Każdy z nich definiuje, *nazwa [= wartość]*.

     Aby uzyskać więcej informacji, zobacz **/d** opcja w [MIDL wiersza polecenia](/windows/desktop/Midl/midl-command-line-reference). Zobacz również parametr **UndefinePreprocessorDefinitions** w tej tabeli.

- **ProxyFileName**

     Opcjonalny parametr **ciągu** .

     Określa nazwę pliku serwera proxy interfejsu dla interfejsu COM.

     Aby uzyskać więcej informacji, zobacz **/proxy** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **RedirectOutputAndErrors**

     Opcjonalny parametr **ciągu** .

     Przekierowuje dane wyjściowe, takie jak komunikaty o błędach i ostrzeżenia, ze standardowego wyjścia do określonego pliku.

     Aby uzyskać więcej informacji, zobacz **/o** opcja w [MIDL wiersza polecenia](/windows/desktop/Midl/midl-command-line-reference).

- **ServerStubFile**

     Opcjonalny parametr **ciągu** .

     Określa nazwę pliku szczątkowego serwera dla interfejsu RPC.

     Aby uzyskać więcej informacji, zobacz **/sstub** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference). Zobacz również parametr **ClientStubFile** w tej tabeli.

- **Element źródłowy**

     Wymagany parametr interfejsu `ITaskItem[]`.

     Określa listę plików źródłowych rozdzielonych spacjami.

- **StructMemberAlignment**

     Opcjonalny parametr **ciągu** .

     Określa wyrównanie (*poziom pakowania*) struktur w systemie docelowym.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**NotSet**|*\<none>*|
    |**1**|**/ZP1**|
    |**2**|**/Zp2**|
    |**4**|**/Zp4**|
    |**8**|**/ZP8**|

     Aby uzyskać więcej informacji, zobacz **/ZP** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference). Opcja **/ZP** jest równoważna z opcją **/Pack** i starszą opcją **/align** .

- **SuppressCompilerWarnings**

     Opcjonalny parametr **logiczny** .

     Jeśli `true` , pomija komunikaty ostrzegawcze z zadania MIDL.

     Aby uzyskać więcej informacji, zobacz opcję **/no_warn** w [dokumentacji wiersza polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **SuppressStartupBanner**

     Opcjonalny `Boolean` parametr.

     Jeśli `true` , program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.

     Aby uzyskać więcej informacji, zobacz **/nologo** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **TargetEnvironment**

     Opcjonalny parametr **ciągu** .

     Określa środowisko, w którym jest uruchamiana aplikacja.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**NotSet**|*\<none>*|
    |**Win32**|**/ENV Win32**|
    |**Itanium**|**/ENV ia64**|
    |**Procesorów**|**/ENV x64**|

     Aby uzyskać więcej informacji, zobacz **/ENV** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **Katalog trackerlogdirectory**

     Opcjonalny `String` parametr.

     Określa katalog pośredni, w którym są przechowywane dzienniki śledzenia dla tego zadania.

- **TypeLibFormat**

     Opcjonalny parametr **ciągu** .

     Określa format pliku biblioteki typów.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**NewFormat**|**/newtlb**|
    |**OldFormat**|**/oldtlb**|

     Aby uzyskać więcej informacji, zobacz Opcje **/newtlb** i **/oldtlb** w [dokumentacji wiersza polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **TypeLibraryName**

     Opcjonalny parametr **ciągu** .

     Określa nazwę pliku biblioteki typów.

     Aby uzyskać więcej informacji, zobacz **/TLB** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **UndefinePreprocessorDefinitions**

     Opcjonalny parametr **String []** .

     Usuwa wszystkie poprzednie definicje nazw, przekazując nazwę do preprocesora C, jak w przypadku `#undefine` dyrektywy. Określ co najmniej jedną wcześniej zdefiniowaną nazwę.

     Aby uzyskać więcej informacji, zobacz **/u** opcji w [MIDL wiersza polecenia](/windows/desktop/Midl/midl-command-line-reference). Zobacz również parametr **PreprocessorDefinitions** w tej tabeli.

- **ValidateAllParameters**

     Opcjonalny `Boolean` parametr.

     Jeśli `true` program generuje dodatkowe informacje o sprawdzaniu błędów, które są używane do przeprowadzania sprawdzania integralności w czasie wykonywania. Jeśli `false` nie są generowane informacje o sprawdzaniu błędów.

     Aby uzyskać więcej informacji, zobacz Opcje **/Robust** i **/no_robust** w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **Warnaserror —**

     Opcjonalny `Boolean` parametr.

     Jeśli `true` , traktuje wszystkie ostrzeżenia jako błędy.

     Jeśli parametr zadania **WarningLevel** MIDL nie zostanie określony, ostrzeżenia na poziomie domyślnym na poziomie 1 są traktowane jako błędy.

     Aby uzyskać więcej informacji, zobacz Opcje **/WX** w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference). Zobacz również parametr **WarningLevel** w tej tabeli.

- **WarningLevel**

     Opcjonalny parametr **ciągu** .

     Określa ważność (*poziom ostrzeżenia*) ostrzeżeń do emisji. Żadne ostrzeżenie nie jest emitowane dla wartości 0. W przeciwnym razie jest emitowane ostrzeżenie, jeśli jego poziom ostrzeżeń jest numerycznie mniejszy lub równy podanej wartości.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**0**|**/W0**|
    |**1**|**/W1**|
    |**2**|**/W2**|
    |**3**|**/W3**|
    |**4**|**/W4**|

     Aby uzyskać więcej informacji, zobacz opcja **/w** w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference). Zobacz również parametr **warnaserror —** w tej tabeli.

## <a name="see-also"></a>Zobacz też

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
