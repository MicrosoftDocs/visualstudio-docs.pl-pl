---
title: MIDL — zadanie | Dokumentacja firmy Microsoft
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
- MSBuild (Visual C++), MIDL task
- MIDL task (MSBuild (Visual C++))
ms.assetid: 727efa8c-3336-40b8-8bef-ae6cbd77a422
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 301ca4ee88368b9134bbbcd2dc41435590becaed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62817574"
---
# <a name="midl-task"></a>MIDL — Zadanie
Narzędzie kompilatora języka definicji interfejsu Microsoft (MIDL), jest zawijany *midl.exe*. Aby uzyskać więcej informacji, zobacz [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

## <a name="parameters"></a>Parametry
 Poniżej opisano parametry **MIDL** zadania. Większość parametrów zadania oraz kilka zestawów parametrów, odpowiada opcji wiersza polecenia.

- **AdditionalIncludeDirectories**

     Opcjonalnie **String []** parametru.

     Dodaje katalog do listy katalogów przeszukiwanych w poszukiwaniu zaimportowane pliki IDL, pliki nagłówkowe dołączone i pliki konfiguracyjne aplikacji (ACF).

     Aby uzyskać więcej informacji, zobacz **/I** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **AdditionalOptions**

     Opcjonalnie **ciąg** parametru.

     Listę opcji wiersza polecenia. Na przykład /\<opcja1 > /\<opcja2 > /\<opcja #>. Użyj tego parametru, aby określić opcje wiersza polecenia, które nie są reprezentowane przez inne parametry zadania MIDL.

     Aby uzyskać więcej informacji, zobacz [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **ApplicationConfigurationMode**

     Opcjonalnie **logiczna** parametru.

     Jeśli `true`, umożliwia korzystanie z niektórych słów kluczowych ACF w pliku IDL.

     Aby uzyskać więcej informacji, zobacz **/app_config** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **ClientStubFile**

     Opcjonalnie **ciąg** parametru.

     Określa nazwę plik szczątkowy klienta dla interfejsu RPC.

     Aby uzyskać więcej informacji, zobacz **/cstub** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Zobacz też **ServerStubFile** parametru w tej tabeli.

- **CPreprocessOptions**

     Opcjonalnie **ciąg** parametru.

     Określa opcje do przekazania do C/C++ preprocessor. Określ rozdzieloną spacjami listę opcje preprocesora.

     Aby uzyskać więcej informacji, zobacz **/cpp_opt** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **DefaultCharType**

     Opcjonalnie **ciąg** parametru.

     Określa domyślny typ znakowy kompilatora C użyje do kompilowania wygenerowanego kodu.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**Podpisany**|**podpisana /char**|
    |**Bez znaku**|**/CHAR bez znaku**|
    |**Ascii**|**/CHAR ascii7**|

     Aby uzyskać więcej informacji, zobacz **/char** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **DllDataFileName**

     Opcjonalnie **ciąg** parametru.

     Określa nazwę pliku dla wygenerowanej *dlldata* pliku biblioteki DLL serwera proxy.

     Aby uzyskać więcej informacji, zobacz **/dlldata** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **EnableErrorChecks**

     Opcjonalnie **ciąg** parametru.

     Określa typ błąd podczas sprawdzania, czy wygenerowane klasy zastępcze będzie wykonywać w czasie wykonywania.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**Brak**|**/ Error none**|
    |**EnableCustom**|**/ Error**|
    |**Wszystkie**|**wszystkie/Error**|

     Aby uzyskać więcej informacji, zobacz **/Error** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckAllocations**

     Opcjonalnie **logiczna** parametru.

     Jeśli `true`, sprawdź, czy błędy braku pamięci.

     Aby uzyskać więcej informacji, zobacz **alokacji/Error** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckBounds**

     Opcjonalnie **logiczna** parametru.

     Jeśli `true`, sprawdza, czy rozmiar o różnym poziomie zgodności i różnicując tablic względem Specyfikacja długości transmisji.

     Aby uzyskać więcej informacji, zobacz **/Error bounds_check** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckEnumRange**

     Opcjonalnie **logiczna** parametru.

     Jeśli `true`, sprawdza, czy wartości wyliczeniowe są w dopuszczalnym zakresie.

     Aby uzyskać więcej informacji, zobacz **/Error enum** opcji w wierszu polecenia Pomoc (**/?**) dla *midl.exe*.

- **ErrorCheckRefPointers**

     Opcjonalnie **logiczna** parametru.

     Jeśli `true`, upewnij się, że żadnych wskaźników odwołanie o wartości null są przekazywane do wycinków klienta.

     Aby uzyskać więcej informacji, zobacz **/Error ref** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckStubData**

     Opcjonalnie **logiczna** parametru.

     Jeśli `true`, wygeneruje odcinek, który przechwytuje unmarshaling wyjątki po stronie serwera i propaguje je do klienta.

     Aby uzyskać więcej informacji, zobacz **/Error stub_data** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **GenerateClientFiles**

     Opcjonalnie **ciąg** parametru.

     Określa, czy kompilator generuje pliki źródłowe C po stronie klienta dla interfejsu RPC.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**Brak**|**/ Client none**|
    |**Stub**|**klasy zastępczej/Client**|

     Aby uzyskać więcej informacji, zobacz **/Client** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **GenerateServerFiles**

     Opcjonalnie **ciąg** parametru.

     Określa, czy kompilator generuje pliki źródłowe C po stronie serwera dla interfejsu RPC.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**Brak**|**/ Server none**|
    |**Stub**|**klasy zastępczej/Server**|

     Aby uzyskać więcej informacji, zobacz **/Server** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **GenerateStublessProxies**

     Opcjonalnie **logiczna** parametru.

     Jeśli `true`, generuje w pełni interpretowane klasy zastępcze oraz proxy bez klas zastępczych dla interfejsów obiektów.

     Aby uzyskać więcej informacji, zobacz **/Oicf** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **GenerateTypeLibrary**

     Opcjonalnie **logiczna** parametru.

     Jeśli `true`, bibliotekę typów (*.tlb*) plik nie jest generowany.

     Aby uzyskać więcej informacji, zobacz **notlb** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **HeaderFileName**

     Opcjonalnie **ciąg** parametru.

     Określa nazwę wygenerowanego pliku nagłówka.

     Aby uzyskać więcej informacji, zobacz **/h** lub **/header** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **IgnoreStandardIncludePath**

     Opcjonalnie **logiczna** parametru.

     Jeśli `true`, MIDL — zadanie przeszukuje katalogi określone za pomocą **AdditionalIncludeDirectories** przełącznik, a pomija bieżącego katalogu i katalogi określone przez zmienną środowiskową INCLUDE.

     Aby uzyskać więcej informacji, zobacz **/no_def_idir** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **InterfaceIdentifierFileName**

     Opcjonalnie **ciąg** parametru.

     Określa nazwę *pliku identyfikatora interfejsu* interfejsu COM. Przesłania domyślną nazwę uzyskaną przez dodanie "_i.c" do nazwy pliku IDL.

     Aby uzyskać więcej informacji, zobacz **/iid** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **Identyfikator ustawień regionalnych**

     Opcjonalnie **int** parametru.

     Określa *identyfikator ustawień regionalnych* , który umożliwia korzystanie z znaki międzynarodowe w plików wejściowych, nazw plików i ścieżek katalogów. Określ identyfikator ustawień regionalnych dziesiętną.

     Aby uzyskać więcej informacji, zobacz **/LCID** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Zobacz też [identyfikatory ustawień regionalnych](https://docs.microsoft.com/windows/desktop/intl/locale-identifiers).

- **MkTypLibCompatible**

     Opcjonalnie **logiczna** parametru.

     Jeśli `true`, wymaga formatu pliku wejściowego, aby był zgodny z *mktyplib.exe* w wersji 2.03.

     Aby uzyskać więcej informacji, zobacz **/mktyplib203** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Zobacz też [składni pliku ODL](/previous-versions/windows/desktop/automat/odl-file-syntax) w witrynie MSDN.

- **OutputDirectory**

     Opcjonalnie **ciąg** parametru.

     Określa domyślny katalog, w którym zadanie MIDL zapisuje pliki wyjściowe.

     Aby uzyskać więcej informacji, zobacz **/out** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **PreprocessorDefinitions**

     Opcjonalnie **String []** parametru.

     Określa co najmniej jeden *definiuje*; oznacza to, nazwę i wartość do przekazania do preprocesora C jako opcjonalną Jeśli przez `#define` dyrektywy. Formularz każdego Definiuj jest, *nazwa [= value]*.

     Aby uzyskać więcej informacji, zobacz **/D** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Zobacz też **UndefinePreprocessorDefinitions** parametru w tej tabeli.

- **ProxyFileName**

     Opcjonalnie **ciąg** parametru.

     Określa nazwę pliku proxy interfejsu dla interfejsu COM.

     Aby uzyskać więcej informacji, zobacz **/proxy** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **RedirectOutputAndErrors**

     Opcjonalnie **ciąg** parametru.

     Przekierowuje dane wyjściowe, takie jak komunikaty o błędach i ostrzeżenia, standardowe dane wyjściowe do określonego pliku.

     Aby uzyskać więcej informacji, zobacz **/o** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **ServerStubFile**

     Opcjonalnie **ciąg** parametru.

     Określa nazwę plik szczątkowy serwera dla interfejsu RPC.

     Aby uzyskać więcej informacji, zobacz **/sstub** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Zobacz też **ClientStubFile** parametru w tej tabeli.

- **Element źródłowy**

     Wymagane `ITaskItem[]` parametru.

     Określa listę plików źródłowych, rozdzielone spacjami.

- **StructMemberAlignment**

     Opcjonalnie **ciąg** parametru.

     Określa wyrównanie (*pakowania poziom*) struktur w systemie docelowym.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**NotSet**|*\<Brak >*|
    |**1**|**/Zp1**|
    |**2**|**/Zp2**|
    |**4**|**/Zp4**|
    |**8**|**/Zp8**|

     Aby uzyskać więcej informacji, zobacz **/ZP** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). **/ZP** opcja jest równoznaczna z **/pakiet** opcja i starszej wersji **/ align** opcji.

- **SuppressCompilerWarnings**

     Opcjonalnie **logiczna** parametru.

     Jeśli `true`, pomija komunikaty ostrzegawcze z zadania MIDL.

     Aby uzyskać więcej informacji, zobacz **/no_warn** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **SuppressStartupBanner**

     Opcjonalnie `Boolean` parametru.

     Jeśli `true`, uniemożliwia wyświetlanie wiadomości praw autorskich i wersji, podczas uruchamiania zadania.

     Aby uzyskać więcej informacji, zobacz **/nologo** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **TargetEnvironment**

     Opcjonalnie **ciąg** parametru.

     Określa środowisko, w którym jest uruchomiona aplikacja.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**NotSet**|*\<Brak >*|
    |**Win32**|**/ ENV win32**|
    |**Itanium**|**/ ENV ia64**|
    |**X64**|**/ ENV x64**|

     Aby uzyskać więcej informacji, zobacz **/ENV** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **TrackerLogDirectory**

     Opcjonalnie `String` parametru.

     Określa katalog pośredni, w którym są przechowywane dzienniki śledzenia dla tego zadania.

- **TypeLibFormat**

     Opcjonalnie **ciąg** parametru.

     Określa format pliku biblioteki typów.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**NewFormat**|**/newtlb**|
    |**OldFormat**|**/oldtlb**|

     Aby uzyskać więcej informacji, zobacz **/newtlb** i **/oldtlb** opcji na liście [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **TypeLibraryName**

     Opcjonalnie **ciąg** parametru.

     Określa nazwę pliku biblioteki typów.

     Aby uzyskać więcej informacji, zobacz **/TLB** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **UndefinePreprocessorDefinitions**

     Opcjonalnie **String []** parametru.

     Usuwa wszystkie poprzednią definicję nazwy przez przekazanie nazwy preprocesora C jako Jeśli przez `#undefine` dyrektywy. Określ jedną lub więcej nazw uprzednio zdefiniowany.

     Aby uzyskać więcej informacji, zobacz **/U** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Zobacz też **PreprocessorDefinitions** parametru w tej tabeli.

- **ValidateAllParameters**

     Opcjonalnie `Boolean` parametru.

     Jeśli `true`, generuje dodatkowe informacje sprawdzanie błędów, który jest używany do wykonywania sprawdzania integralności w czasie wykonywania. Jeśli `false`, sprawdzanie błędów informacje nie są generowane.

     Aby uzyskać więcej informacji, zobacz **/ robust** i **/no_robust** opcji na liście [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference).

- **Warnaserror —**

     Opcjonalnie `Boolean` parametru.

     Jeśli `true`, traktuje wszystkie ostrzeżenia jako błędy.

     Jeśli **Poziom_ostrzeżeń** MIDL zadań parametr nie jest określony, ostrzeżenia na poziomie domyślnym poziomie 1, są traktowane jako błędy.

     Aby uzyskać więcej informacji, zobacz **/WX** opcji na liście [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Zobacz też **Poziom_ostrzeżeń** parametru w tej tabeli.

- **Poziom_ostrzeżeń**

     Opcjonalnie **ciąg** parametru.

     Określa ważność (*poziom ostrzeżeń*) ostrzeżeń do emitowania. Ostrzeżenie nie jest emitowane na wartość 0. W przeciwnym razie jest emitowane ostrzeżenie, jeśli jego poziom ostrzeżeń jest wartość liczbowa mniejsza lub równa określonej wartości.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

    |Wartość|Opcja wiersza polecenia|
    |-----------|--------------------------|
    |**0**|**/W0**|
    |**1**|**/W1**|
    |**2**|**/W2**|
    |**3**|**/W3**|
    |**4**|**/W4**|

     Aby uzyskać więcej informacji, zobacz **Wn** opcji [wiersza polecenia MIDL](https://docs.microsoft.com/windows/desktop/Midl/midl-command-line-reference). Zobacz też **WarnAsError** parametru w tej tabeli.

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)