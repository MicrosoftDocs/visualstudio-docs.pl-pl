---
title: MIDL — zadanie | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a43975244eaf064c9ed7608fa41c16854ca140f
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633476"
---
# <a name="midl-task"></a>MIDL — Zadanie

Zawija narzędzie kompilatora Microsoft Interface Definition Language (MIDL), *MIDL. exe*. Aby uzyskać więcej informacji, zobacz [MIDL — dokumentacja wiersza polecenia](/windows/desktop/Midl/midl-command-line-reference).

## <a name="parameters"></a>Parametry

 Poniżej opisano parametry zadania **MIDL** . Większość parametrów zadań i kilku zestawów parametrów odpowiada opcji wiersza polecenia.

- **AdditionalIncludeDirectories**

     Opcjonalny parametr **String []** .

     Dodaje katalog do listy katalogów przeszukiwanych pod kątem importowanych plików IDL, dołączonych plików nagłówkowych i plików konfiguracji aplikacji (ACF).

     Aby uzyskać więcej informacji, zobacz **/i** opcja w [MIDL wiersza polecenia](/windows/desktop/Midl/midl-command-line-reference).

- **AdditionalOptions**

     Opcjonalny parametr **ciągu** .

     Lista opcji wiersza polecenia. Na przykład/\<opcja1 >/\<opcja2 >/\<opcji # >. Użyj tego parametru, aby określić opcje wiersza polecenia, które nie są reprezentowane przez żaden inny parametr zadania MIDL.

     Aby uzyskać więcej informacji, zobacz [MIDL — dokumentacja wiersza polecenia](/windows/desktop/Midl/midl-command-line-reference).

- **ApplicationConfigurationMode**

     Opcjonalny parametr **logiczny** .

     Jeśli `true`, program pozwala używać niektórych słów kluczowych ACF w pliku IDL.

     Aby uzyskać więcej informacji, zobacz opcję **/app_config** w [dokumentacji wiersza polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **ClientStubFile**

     Opcjonalny parametr **ciągu** .

     Określa nazwę pliku szczątkowego klienta dla interfejsu RPC.

     Aby uzyskać więcej informacji, zobacz **/cstub** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference). Zobacz również parametr **ServerStubFile** w tej tabeli.

- **CPreprocessOptions**

     Opcjonalny parametr **ciągu** .

     Określa opcje do przekazania do języka C/C++ preprocesora. Określ rozdzielaną spacją listę opcji preprocesora.

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
    |**Dawaj**|**/Error brak**|
    |**EnableCustom**|**/Error**|
    |**Wszystkie**|**/Error wszystko**|

     Aby uzyskać więcej informacji, zobacz **/Error** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckAllocations**

     Opcjonalny parametr **logiczny** .

     Jeśli `true`, sprawdź, czy nie występują błędy braku pamięci.

     Aby uzyskać więcej informacji, zobacz opcja **alokacji/Error** w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckBounds**

     Opcjonalny parametr **logiczny** .

     Jeśli `true`, sprawdza rozmiar zgodnych i zróżnicowanych tablic względem specyfikacji długości transmisji.

     Aby uzyskać więcej informacji, zobacz **/error bounds_check** opcja w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckEnumRange**

     Opcjonalny parametr **logiczny** .

     Jeśli `true`, sprawdza, czy wartości wyliczeniowe są w dopuszczalnym zakresie.

     Aby uzyskać więcej informacji, zobacz **/Error enum** w pomocy wiersza polecenia ( **/?** ) dla *MIDL. exe*.

- **ErrorCheckRefPointers**

     Opcjonalny parametr **logiczny** .

     Jeśli `true`, sprawdź, czy do wycinków klientów nie są przenoszone żadne wskaźniki odwołań o wartości null.

     Aby uzyskać więcej informacji, zobacz **/Error ref** Option in [MIDL Command-Line Reference](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckStubData**

     Opcjonalny parametr **logiczny** .

     Jeśli `true`, generuje procedurę pośredniczącą, która przechwytuje wyjątki po stronie serwera i propaguje je z powrotem do klienta.

     Aby uzyskać więcej informacji, zobacz **/error stub_data** opcja w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateClientFiles**

     Opcjonalny parametr **ciągu** .

     Określa, czy kompilator generuje pliki źródłowe C po stronie klienta dla interfejsu RPC.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**Dawaj**|**/Client brak**|
    |**Szkieletu**|**/Client**|

     Aby uzyskać więcej informacji, zobacz **/Client** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateServerFiles**

     Opcjonalny parametr **ciągu** .

     Określa, czy kompilator generuje pliki źródłowe C po stronie serwera dla interfejsu RPC.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**Dawaj**|**/Server brak**|
    |**Szkieletu**|**/Server — stub**|

     Aby uzyskać więcej informacji, zobacz opcja **/Server** w [MIDL w wierszu polecenia](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateStublessProxies**

     Opcjonalny parametr **logiczny** .

     W przypadku `true`program generuje w pełni interpretowane klasy zastępcze z niepośredniczącymi serwerami proxy dla interfejsów obiektów.

     Aby uzyskać więcej informacji, zobacz **/Oicf** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateTypeLibrary**

     Opcjonalny parametr **logiczny** .

     Jeśli `true`, plik biblioteki typów (*TLB*) nie zostanie wygenerowany.

     Aby uzyskać więcej informacji, zobacz **/notlb** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **HeaderFileName**

     Opcjonalny parametr **ciągu** .

     Określa nazwę wygenerowanego pliku nagłówkowego.

     Aby uzyskać więcej informacji, zobacz opcja **/h** lub **/header** w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **IgnoreStandardIncludePath**

     Opcjonalny parametr **logiczny** .

     Jeśli `true`, zadanie MIDL przeszukuje tylko katalogi określone za pomocą przełącznika **AdditionalIncludeDirectories** i ignoruje bieżący katalog i katalogi określone przez zmienną środowiskową INCLUDE.

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

     Jeśli `true`, program wymaga, aby format pliku wejściowego był zgodny z *MkTypLib. exe* w wersji 2,03.

     Aby uzyskać więcej informacji, zobacz **/mktyplib203** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference). Zobacz też [składnię pliku ODL](/previous-versions/windows/desktop/automat/odl-file-syntax) w witrynie MSDN.

- **OutputDirectory**

     Opcjonalny parametr **ciągu** .

     Określa domyślny katalog, w którym zadanie MIDL zapisuje pliki wyjściowe.

     Aby uzyskać więcej informacji, zobacz opcję **/out** w [MIDL wiersza polecenia](/windows/desktop/Midl/midl-command-line-reference).

- **PreprocessorDefinitions**

     Opcjonalny parametr **String []** .

     Określa co najmniej jedną *definicję*; oznacza to, że nazwa i wartość opcjonalna, które mają zostać przesłane do preprocesora C, tak jak w przypadku dyrektywy `#define`. Każdy z nich definiuje, *nazwa [= wartość]* .

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

     Wymagany `ITaskItem[]` parametr.

     Określa listę plików źródłowych rozdzielonych spacjami.

- **StructMemberAlignment**

     Opcjonalny parametr **ciągu** .

     Określa wyrównanie (*poziom pakowania*) struktur w systemie docelowym.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**NotSet**|*\<brak >*|
    |**1**|**/ZP1**|
    |**2**|**/Zp2**|
    |**4**|**/Zp4**|
    |**8**|**/ZP8**|

     Aby uzyskać więcej informacji, zobacz **/ZP** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference). Opcja **/ZP** jest równoważna z opcją **/Pack** i starszą opcją **/align** .

- **SuppressCompilerWarnings**

     Opcjonalny parametr **logiczny** .

     Jeśli `true`, program pomija komunikaty ostrzegawcze z zadania MIDL.

     Aby uzyskać więcej informacji, zobacz opcję **/no_warn** w [dokumentacji wiersza polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **SuppressStartupBanner**

     Opcjonalny parametr `Boolean`.

     Jeśli `true`, program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.

     Aby uzyskać więcej informacji, zobacz **/nologo** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **TargetEnvironment**

     Opcjonalny parametr **ciągu** .

     Określa środowisko, w którym jest uruchamiana aplikacja.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**NotSet**|*\<brak >*|
    |**System**|**/ENV Win32**|
    |**Itanium**|**/ENV ia64**|
    |**Procesorów**|**/ENV x64**|

     Aby uzyskać więcej informacji, zobacz **/ENV** opcji w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **Katalog trackerlogdirectory**

     Opcjonalny parametr `String`.

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

     Usuwa wszystkie poprzednie definicje nazw, przekazując nazwę do preprocesora C, tak jak w przypadku dyrektywy `#undefine`. Określ co najmniej jedną wcześniej zdefiniowaną nazwę.

     Aby uzyskać więcej informacji, zobacz **/u** opcji w [MIDL wiersza polecenia](/windows/desktop/Midl/midl-command-line-reference). Zobacz również parametr **PreprocessorDefinitions** w tej tabeli.

- **ValidateAllParameters**

     Opcjonalny parametr `Boolean`.

     Jeśli `true`, program generuje dodatkowe informacje o sprawdzaniu błędów, które są używane do przeprowadzania sprawdzania integralności w czasie wykonywania. W przypadku `false`nie są generowane informacje o sprawdzaniu błędów.

     Aby uzyskać więcej informacji, zobacz Opcje **/Robust** i **/no_robust** w [wierszu polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **Warnaserror —**

     Opcjonalny parametr `Boolean`.

     Jeśli `true`, traktuje wszystkie ostrzeżenia jako błędy.

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

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
