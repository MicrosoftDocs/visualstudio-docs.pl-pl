---
title: Zadanie MIDL | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633476"
---
# <a name="midl-task"></a>MIDL — Zadanie

Zawija narzędzie kompilatora języka MIDL (Microsoft Interface Definition Language), *midl.exe*. Aby uzyskać więcej informacji, zobacz [odwołanie do wiersza polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

## <a name="parameters"></a>Parametry

 Poniżej opisano parametry zadania **MIDL.** Większość parametrów zadania i kilka zestawów parametrów odpowiada opcji wiersza polecenia.

- **DodatkoweInobserwająKatary**

     Parametr **Opcjonalny ciąg[].**

     Dodaje katalog do listy katalogów, które są wyszukiwane w poszukiwaniu importowanych plików IDL, dołączonych plików nagłówkowych i plików konfiguracyjnych aplikacji (ACF).

     Aby uzyskać więcej informacji, zobacz **/I** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **Dodatkoweopcje**

     Opcjonalny parametr **String.**

     Lista opcji wiersza polecenia. Na przykład\</ option1>\</ option2\<> / option#>. Ten parametr służy do określania opcji wiersza polecenia, które nie są reprezentowane przez żaden inny parametr zadania MIDL.

     Aby uzyskać więcej informacji, zobacz [odwołanie do wiersza polecenia MIDL](/windows/desktop/Midl/midl-command-line-reference).

- **Tryb konfiguracji aplikacji**

     Opcjonalny parametr **logiczny.**

     Jeśli `true`program umożliwia użycie niektórych słów kluczowych ACF w pliku IDL.

     Aby uzyskać więcej informacji, zobacz **/app_config** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **Plik Klienta**

     Opcjonalny parametr **String.**

     Określa nazwę pliku skrótowego klienta dla interfejsu RPC.

     Aby uzyskać więcej informacji, zobacz **/cstub** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference). Zobacz także **ServerStubFile** parametr w tej tabeli.

- **CPreprocessOptions**

     Opcjonalny parametr **String.**

     Określa opcje przekazywania do preprocesora C/C++. Określ rozdzieloną spację listę opcji preprocesora.

     Aby uzyskać więcej informacji, zobacz **/cpp_opt** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **DefaultCharType (Typ domyślny)**

     Opcjonalny parametr **String.**

     Określa domyślny typ znaku używany przez kompilator języka C do kompilowania wygenerowanego kodu.

     Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**Podpisane**|**/char podpisana**|
    |**Niepodpisane**|**/char niepodpisany**|
    |**Ascii**|**/char ascii7**|

     Aby uzyskać więcej informacji, zobacz **/char** opcji w [MIDL polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **Nazwa pliku DllData**

     Opcjonalny parametr **String.**

     Określa nazwę pliku wygenerowanego *pliku dlldata* dla biblioteki DLL serwera proxy.

     Aby uzyskać więcej informacji, zobacz **/dlldata** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **EnableErrorChecks (Sprawdzanie włączania errorche.**

     Opcjonalny parametr **String.**

     Określa typ sprawdzania błędów, który generowane wycinki będą wykonywane w czasie wykonywania.

     Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**Brak**|**/error brak**|
    |**EnableCustom (Włącz pozycję bez celu)**|**/error**|
    |**Wszystkie**|**/error wszystkie**|

     Aby uzyskać więcej informacji, zobacz **/error** option w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **Lokalizacja błędów**

     Opcjonalny parametr **logiczny.**

     Jeśli `true`, sprawdź błędy braku pamięci.

     Aby uzyskać więcej informacji, zobacz **/error allocation** option in [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference).

- **Połączenia błędów**

     Opcjonalny parametr **logiczny.**

     Jeśli `true`, sprawdza rozmiar konformantów zmiennych i różne tablice w stosunku do specyfikacji długości transmisji.

     Aby uzyskać więcej informacji, zobacz **/error bounds_check** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **Funkcja ErrorCheckEnumRange**

     Opcjonalny parametr **logiczny.**

     Jeśli `true`, sprawdza, czy wartości wyliczenia znajdują się w dopuszczalnym zakresie.

     Aby uzyskać więcej informacji, zobacz **/error enum** option in command-line help (**/?**) for *midl.exe*.

- **Punkty errorCheckRefPointers**

     Opcjonalny parametr **logiczny.**

     Jeśli `true`, sprawdź, czy żadne wskaźniki odwołania null nie są przekazywane do wycinków klienta.

     Aby uzyskać więcej informacji, zobacz **/error ref** opcja w [midl polecenia odwołania wiersza](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckStubData**

     Opcjonalny parametr **logiczny.**

     Jeśli `true`, generuje skrótowy, który łapie odłączanie wyjątków po stronie serwera i propaguje je z powrotem do klienta.

     Aby uzyskać więcej informacji, zobacz **/error stub_data** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **Generowanie plikówclientfiles**

     Opcjonalny parametr **String.**

     Określa, czy kompilator generuje pliki źródłowe C po stronie klienta dla interfejsu RPC.

     Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**Brak**|**/brak klienta**|
    |**Skrótowej**|**/skrót od klienta**|

     Aby uzyskać więcej informacji, zobacz **/client** option w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **Generowanie plików serwera**

     Opcjonalny parametr **String.**

     Określa, czy kompilator generuje pliki źródłowe C po stronie serwera dla interfejsu RPC.

     Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**Brak**|**/server brak**|
    |**Skrótowej**|**/skrót serwera**|

     Aby uzyskać więcej informacji, zobacz **/server** option w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateStublessProxies (GenerowaniepodsublessProxies)**

     Opcjonalny parametr **logiczny.**

     Jeśli `true`, generuje w pełni interpretowane wycinki wraz z stubless serwerów proxy dla interfejsów obiektów.

     Aby uzyskać więcej informacji, zobacz **/Oicf** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateTypeLibrary**

     Opcjonalny parametr **logiczny.**

     Jeśli `true`plik z biblioteki typów (*.tlb*) nie jest generowany.

     Aby uzyskać więcej informacji, zobacz **/notlb** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **Nazwa pliku nagłówka**

     Opcjonalny parametr **String.**

     Określa nazwę wygenerowanego pliku nagłówka.

     Aby uzyskać więcej informacji, zobacz **/h** lub **/header** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **IgnoreStandardIncludePath**

     Opcjonalny parametr **logiczny.**

     Jeśli `true`zadanie MIDL przeszukuje tylko katalogi określone za pomocą przełącznika **AdditionalIncludeDirectories** i ignoruje bieżący katalog i katalogi określone przez zmienną środowiskową INCLUDE.

     Aby uzyskać więcej informacji, zobacz **/no_def_idir** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **Nazwa pliku InterfaceIdentifierFileName**

     Opcjonalny parametr **String.**

     Określa nazwę pliku *identyfikatora interfejsu* COM. Zastępuje to domyślną nazwę uzyskaną przez dodanie "_i.c" do nazwy pliku IDL.

     Aby uzyskać więcej informacji, zobacz **/iid** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **Localeid**

     Opcjonalny parametr **int.**

     Określa *identyfikator ustawień regionalnych,* który umożliwia używanie znaków międzynarodowych w plikach wejściowych, nazwach plików i ścieżkach katalogów. Określ identyfikator ustawień regionalnych dziesiętnych.

     Aby uzyskać więcej informacji, zobacz **/lcid** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference). Zobacz też [identyfikatory ustawień regionalnych](/windows/desktop/intl/locale-identifiers).

- **Kompatybilność z MkTypLibCompatible**

     Opcjonalny parametr **logiczny.**

     Jeśli `true`, wymaga, aby format pliku wejściowego był zgodny z *mktyplib.exe* w wersji 2.03.

     Aby uzyskać więcej informacji, zobacz **/mktyplib203** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference). Zobacz też [składnia pliku ODL](/previous-versions/windows/desktop/automat/odl-file-syntax) w witrynie sieci Web MSDN.

- **Historia wyjściowa**

     Opcjonalny parametr **String.**

     Określa katalog domyślny, w którym zadanie MIDL zapisuje pliki wyjściowe.

     Aby uzyskać więcej informacji, zobacz **/out** opcja w [MIDL polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **Definicje przedtwarze**

     Parametr **Opcjonalny ciąg[].**

     Określa jedną lub więcej *zdefiniowanych*; oznacza to, że nazwa i wartość opcjonalna, które mają być przekazywane `#define` do preprocesora C, tak jakby przez dyrektywę. Formą każdego zdefiniowania jest *nazwa[=wartość]*.

     Aby uzyskać więcej informacji, zobacz **/D** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference). Ponadto zobacz **UndefinePreprocessorDefinitions** parametr w tej tabeli.

- **Nazwa pliku proxy**

     Opcjonalny parametr **String.**

     Określa nazwę pliku serwera proxy interfejsu COM.

     Aby uzyskać więcej informacji, zobacz **/proxy** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **PrzekierowanieOutputAndErrors**

     Opcjonalny parametr **String.**

     Przekierowuje dane wyjściowe, takie jak komunikaty o błędach i ostrzeżenia, ze standardowego wyjścia do określonego pliku.

     Aby uzyskać więcej informacji, zobacz **/o** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **Plik serwera**

     Opcjonalny parametr **String.**

     Określa nazwę pliku skrótowego serwera dla interfejsu RPC.

     Aby uzyskać więcej informacji, zobacz **/sstub** opcja w [MIDL command-line reference](/windows/desktop/Midl/midl-command-line-reference). Ponadto zobacz **ClientStubFile** parametr w tej tabeli.

- **Źródła**

     Wymagany parametr interfejsu `ITaskItem[]`.

     Określa listę plików źródłowych oddzielonych spacjami.

- **Wyrównanie członków struct**

     Opcjonalny parametr **String.**

     Określa wyrównanie *(poziom pakowania)* struktur w systemie docelowym.

     Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**Notset**|*\<żaden>*|
    |**1**|**/Zp1**|
    |**2**|**/Zp2**|
    |**4**|**/Zp4**|
    |**8**|**/Zp8**|

     Aby uzyskać więcej informacji, zobacz **/Zp** opcja w [MIDL polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference). Opcja **/Zp** jest odpowiednikiem opcji **/pack** i starszej opcji **/align.**

- **Tłumiącefirmy**

     Opcjonalny parametr **logiczny.**

     Jeśli `true`, pomija komunikaty ostrzegawcze z zadania MIDL.

     Aby uzyskać więcej informacji, zobacz **/no_warn** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **SuppressStartupBanner (SuppressStartupBanner)**

     Parametr `Boolean` opcjonalny.

     Jeśli `true`program Zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji po uruchomieniu zadania.

     Aby uzyskać więcej informacji, zobacz **/nologo** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **Doceloweśrodowienie**

     Opcjonalny parametr **String.**

     Określa środowisko, w którym działa aplikacja.

     Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**Notset**|*\<żaden>*|
    |**Win32**|**/env win32**|
    |**Itanium**|**/env ia64**|
    |**X64**|**/env x64**|

     Aby uzyskać więcej informacji, zobacz **/env** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **TrackerLogDirectory (TrackerLogDirectory)**

     Parametr `String` opcjonalny.

     Określa katalog pośredni, w którym są przechowywane dzienniki śledzenia dla tego zadania.

- **TypLibFormat**

     Opcjonalny parametr **String.**

     Określa format pliku biblioteki typów.

     Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**Nowyformat**|**/newtlb**|
    |**StaryFormat**|**/oldtlb**|

     Aby uzyskać więcej informacji, zobacz **/newtlb** i **/oldtlb** opcje w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **TypLibraryName**

     Opcjonalny parametr **String.**

     Określa nazwę pliku biblioteki typów.

     Aby uzyskać więcej informacji, zobacz **/tlb** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **DefinePreprocessorDefinitions**

     Parametr **Opcjonalny ciąg[].**

     Usuwa wszystkie poprzednie definicji nazwy, przekazując nazwę do preprocesora `#undefine` C, tak jakby przez dyrektywę. Określ jedną lub więcej wcześniej zdefiniowanych nazw.

     Aby uzyskać więcej informacji, zobacz **/U** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference). Zobacz także **parametr PreprocessorDefinitions** w tej tabeli.

- **ValidateAllParameters**

     Parametr `Boolean` opcjonalny.

     Jeśli `true`program , generuje dodatkowe informacje sprawdzające błędy, które są używane do wykonywania kontroli integralności w czasie wykonywania. Jeśli `false`informacje o sprawdzaniu błędów nie są generowane.

     Aby uzyskać więcej informacji, zobacz **/robust** i **/no_robust** options w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference).

- **WarnAsError**

     Parametr `Boolean` opcjonalny.

     Jeśli `true`, traktuje wszystkie ostrzeżenia jako błędy.

     Jeśli parametr zadania **WarningLevel** MIDL nie jest określony, ostrzeżenia na poziomie domyślnym, poziom 1, są traktowane jako błędy.

     Aby uzyskać więcej informacji, zobacz **/WX** opcje w [MIDL polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference). Zobacz także **WarningLevel** parametr w tej tabeli.

- **Warninglevel**

     Opcjonalny parametr **String.**

     Określa ważność *(poziom ostrzeżenia*) ostrzeżeń do emisji. Nie jest emitowane żadne ostrzeżenie dla wartości 0. W przeciwnym razie ostrzeżenie jest emitowane, jeśli jego poziom ostrzeżenia jest numerycznie mniejszy lub równy określonej wartości.

     Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**0**|**/W0**|
    |**1**|**/W1**|
    |**2**|**/W2**|
    |**3**|**/W3**|
    |**4**|**/W4**|

     Aby uzyskać więcej informacji, zobacz **/W** opcja w [midl polecenia wiersza odwołania](/windows/desktop/Midl/midl-command-line-reference). Zobacz też parametr **WarnAsError** w tej tabeli.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
