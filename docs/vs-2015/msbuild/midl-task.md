---
title: MIDL — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7e007830a91f0450f6c26c6c175196db308e3a43
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300211"
---
# <a name="midl-task"></a>MIDL — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawija narzędzie kompilatora Microsoft Interface Definition Language (MIDL), MIDL. exe. Aby uzyskać więcej informacji, zobacz sekcję "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry zadania **MIDL** . Większość parametrów zadań i kilku zestawów parametrów odpowiada opcji wiersza polecenia.  
  
- **AdditionalIncludeDirectories**  
  
     Opcjonalny parametr **String []** .  
  
     Dodaje katalog do listy katalogów przeszukiwanych pod kątem importowanych plików IDL, dołączonych plików nagłówkowych i plików konfiguracji aplikacji (ACF).  
  
     Aby uzyskać więcej informacji, zobacz **/i** opcji w "MIDL wiersza polecenia" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **AdditionalOptions**  
  
     Opcjonalny parametr **ciągu** .  
  
     Lista opcji wiersza polecenia. Na przykład **"** _/option1/option2 Option #_ ". Użyj tego parametru, aby określić opcje wiersza polecenia, które nie są reprezentowane przez żaden inny parametr zadania MIDL.  
  
     Aby uzyskać więcej informacji, zobacz sekcję "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **ApplicationConfigurationMode**  
  
     Opcjonalny parametr **logiczny** .  
  
     Jeśli `true`, program pozwala używać niektórych słów kluczowych ACF w pliku IDL.  
  
     Aby uzyskać więcej informacji, zobacz opcję **/app_config** w artykule "informacje w wierszu polecenia MIDL" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **ClientStubFile**  
  
     Opcjonalny parametr **ciągu** .  
  
     Określa nazwę pliku szczątkowego klienta dla interfejsu RPC.  
  
     Aby uzyskać więcej informacji, zobacz **/cstub** Option in "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web. Zobacz również parametr **ServerStubFile** w tej tabeli.  
  
- **CPreprocessOptions**  
  
     Opcjonalny parametr **ciągu** .  
  
     Określa opcje do przekazania do języka C/C++ preprocesora. Określ rozdzielaną spacją listę opcji preprocesora.  
  
     Aby uzyskać więcej informacji, zobacz opcję **/cpp_opt** w artykule "informacje w wierszu polecenia MIDL" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **DefaultCharType**  
  
     Opcjonalny parametr **ciągu** .  
  
     Określa domyślny typ znaku, który kompilator języka C będzie używał do kompilowania wygenerowanego kodu.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    |Wartość|Opcja wiersza polecenia|  
    |-----------|--------------------------|  
    |**Opatrzon**|**/char podpisany**|  
    |**Bajt**|**/char bez znaku**|  
    |**ASCII**|**/char ascii7**|  
  
     Aby uzyskać więcej informacji, zobacz **/char** Option in "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **DllDataFileName**  
  
     Opcjonalny parametr **ciągu** .  
  
     Określa nazwę pliku dla wygenerowanego pliku *dlldata* dla biblioteki DLL proxy.  
  
     Aby uzyskać więcej informacji, zobacz **/dlldata** Option in "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **EnableErrorChecks**  
  
     Opcjonalny parametr **ciągu** .  
  
     Określa typ błędu podczas sprawdzania, czy generowane wycinki będą wykonywane w czasie wykonywania.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    |Wartość|Opcja wiersza polecenia|  
    |-----------|--------------------------|  
    |**Dawaj**|**/Error brak**|  
    |**EnableCustom**|**/Error**|  
    |**Całą**|**/Error wszystko**|  
  
     Aby uzyskać więcej informacji, zobacz **/Error** Option in "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **ErrorCheckAllocations**  
  
     Opcjonalny parametr **logiczny** .  
  
     Jeśli `true`, sprawdź, czy nie występują błędy braku pamięci.  
  
     Aby uzyskać więcej informacji, zobacz opcja **alokacji/Error** w sekcji "Dokumentacja wiersza polecenia MIDL" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **ErrorCheckBounds**  
  
     Opcjonalny parametr **logiczny** .  
  
     Jeśli `true`, sprawdza rozmiar zgodnych i zróżnicowanych tablic względem specyfikacji długości transmisji.  
  
     Aby uzyskać więcej informacji, zobacz **/error bounds_check** opcja w "MIDL wiersza polecenia" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **ErrorCheckEnumRange**  
  
     Opcjonalny parametr **logiczny** .  
  
     Jeśli `true`, sprawdza, czy wartości wyliczeniowe są w dopuszczalnym zakresie.  
  
     Aby uzyskać więcej informacji, zobacz **/Error enum** w pomocy wiersza polecenia ( **/?** ) dla MIDL. exe.  
  
- **ErrorCheckRefPointers**  
  
     Opcjonalny parametr **logiczny** .  
  
     Jeśli `true`, sprawdź, czy do wycinków klientów nie są przenoszone żadne wskaźniki odwołań o wartości null.  
  
     Aby uzyskać więcej informacji, zobacz **/Error ref** Option in "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **ErrorCheckStubData**  
  
     Opcjonalny parametr **logiczny** .  
  
     Jeśli `true`, generuje procedurę pośredniczącą, która przechwytuje wyjątki po stronie serwera i propaguje je z powrotem do klienta.  
  
     Aby uzyskać więcej informacji, zobacz **/error stub_data** opcja w "MIDL wiersza polecenia" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **GenerateClientFiles**  
  
     Opcjonalny parametr **ciągu** .  
  
     Określa, czy kompilator generuje pliki źródłowe C po stronie klienta dla interfejsu RPC.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    |Wartość|Opcja wiersza polecenia|  
    |-----------|--------------------------|  
    |**Dawaj**|**/Client brak**|  
    |**Szkieletu**|**/Client**|  
  
     Aby uzyskać więcej informacji, zobacz **/Client** Option in "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **GenerateServerFiles**  
  
     Opcjonalny parametr **ciągu** .  
  
     Określa, czy kompilator generuje pliki źródłowe C po stronie serwera dla interfejsu RPC.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    |Wartość|Opcja wiersza polecenia|  
    |-----------|--------------------------|  
    |**Dawaj**|**/Server brak**|  
    |**Szkieletu**|**/Server — stub**|  
  
     Aby uzyskać więcej informacji, zobacz opcja **/Server** w artykule "MIDL w wierszu polecenia" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **GenerateStublessProxies**  
  
     Opcjonalny parametr **logiczny** .  
  
     W przypadku `true`program generuje w pełni interpretowane klasy zastępcze z niepośredniczącymi serwerami proxy dla interfejsów obiektów.  
  
     Aby uzyskać więcej informacji, zobacz **/Oicf** Option in "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **GenerateTypeLibrary**  
  
     Opcjonalny parametr **logiczny** .  
  
     Jeśli `true`, plik biblioteki typów (TLB) nie zostanie wygenerowany.  
  
     Aby uzyskać więcej informacji, zobacz **/notlb** Option in "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **HeaderFileName**  
  
     Opcjonalny parametr **ciągu** .  
  
     Określa nazwę wygenerowanego pliku nagłówkowego.  
  
     Aby uzyskać więcej informacji, zobacz opcję **/h** lub **/header** w sekcji "Dokumentacja wiersza polecenia MIDL" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **IgnoreStandardIncludePath**  
  
     Opcjonalny parametr **logiczny** .  
  
     Jeśli `true`, zadanie MIDL przeszukuje tylko katalogi określone za pomocą przełącznika **AdditionalIncludeDirectories** i ignoruje bieżący katalog i katalogi określone przez zmienną środowiskową INCLUDE.  
  
     Aby uzyskać więcej informacji, zobacz opcję **/no_def_idir** w artykule "informacje w wierszu polecenia MIDL" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **InterfaceIdentifierFileName**  
  
     Opcjonalny parametr **ciągu** .  
  
     Określa nazwę *pliku identyfikatora interfejsu* dla interfejsu com. Zastępuje domyślną nazwę uzyskaną przez dodanie "_i. c" do nazwy pliku IDL.  
  
     Aby uzyskać więcej informacji, zobacz **/IID** Option in "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **LocaleID**  
  
     Opcjonalny parametr **int** .  
  
     Określa *identyfikator ustawień regionalnych* , który umożliwia używanie znaków międzynarodowych w plikach wejściowych, nazwach plików i ścieżkach katalogów. Określ identyfikator ustawień regionalnych dziesiętnych.  
  
     Aby uzyskać więcej informacji, zobacz **/LCID** Option in "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web. Zobacz też sekcję "identyfikatory ustawień regionalnych przypisanych przez firmę Microsoft" w witrynie MSDN.  
  
- **MkTypLibCompatible**  
  
     Opcjonalny parametr **logiczny** .  
  
     Jeśli `true`, program wymaga, aby format pliku wejściowego był zgodny z MkTypLib. exe w wersji 2,03.  
  
     Aby uzyskać więcej informacji, zobacz **/mktyplib203** Option in "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web. Zobacz również sekcję "ODL File Syntax" w witrynie MSDN w sieci Web.  
  
- **OutputDirectory**  
  
     Opcjonalny parametr **ciągu** .  
  
     Określa domyślny katalog, w którym zadanie MIDL zapisuje pliki wyjściowe.  
  
     Aby uzyskać więcej informacji, zobacz opcję **/out** w artykule "MIDL w wierszu polecenia" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **PreprocessorDefinitions**  
  
     Opcjonalny parametr **String []** .  
  
     Określa co najmniej jedną *definicję*; oznacza to, że nazwa i wartość opcjonalna, które mają zostać przesłane do preprocesora C, tak jak w przypadku dyrektywy `#define`. Każdy z nich definiuje, *nazwa [= wartość]* .  
  
     Aby uzyskać więcej informacji, zobacz **/d** Option w "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web. Zobacz również parametr **UndefinePreprocessorDefinitions** w tej tabeli.  
  
- **ProxyFileName**  
  
     Opcjonalny parametr **ciągu** .  
  
     Określa nazwę pliku serwera proxy interfejsu dla interfejsu COM.  
  
     Aby uzyskać więcej informacji, zobacz **/proxy** Option in "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **RedirectOutputAndErrors**  
  
     Opcjonalny parametr **ciągu** .  
  
     Przekierowuje dane wyjściowe, takie jak komunikaty o błędach i ostrzeżenia, ze standardowego wyjścia do określonego pliku.  
  
     Aby uzyskać więcej informacji, zobacz **/o** opcja w "MIDL wiersza polecenia" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **ServerStubFile**  
  
     Opcjonalny parametr **ciągu** .  
  
     Określa nazwę pliku szczątkowego serwera dla interfejsu RPC.  
  
     Aby uzyskać więcej informacji, zobacz **/sstub** Option in "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web. Zobacz również parametr **ClientStubFile** w tej tabeli.  
  
- **Zewnętrz**  
  
     Wymagany `ITaskItem[]` parametr.  
  
     Określa listę plików źródłowych rozdzielonych spacjami.  
  
- **StructMemberAlignment**  
  
     Opcjonalny parametr **ciągu** .  
  
     Określa wyrównanie (*poziom pakowania*) struktur w systemie docelowym.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    |Wartość|Opcja wiersza polecenia|  
    |-----------|--------------------------|  
    |**NotSet**|*\<brak >*|  
    |**jedno**|**/ZP1**|  
    |**dwóch**|**/Zp2**|  
    |**czwart**|**/Zp4**|  
    |**0,8**|**/ZP8**|  
  
     Aby uzyskać więcej informacji, zobacz **/ZP** Option in "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web. Opcja **/ZP** jest równoważna z opcją **/Pack** i starszą opcją **/align** .  
  
- **SuppressCompilerWarnings**  
  
     Opcjonalny parametr **logiczny** .  
  
     Jeśli `true`, program pomija komunikaty ostrzegawcze z zadania MIDL.  
  
     Aby uzyskać więcej informacji, zobacz opcję **/no_warn** w artykule "informacje w wierszu polecenia MIDL" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **SuppressStartupBanner**  
  
     Opcjonalny parametr `Boolean`.  
  
     Jeśli `true`, program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.  
  
     Aby uzyskać więcej informacji, zobacz **/nologo** Option in "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
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
  
     Aby uzyskać więcej informacji, zobacz **/ENV** Option in "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
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
  
     Aby uzyskać więcej informacji, zobacz Opcje **/newtlb** i **/oldtlb** w sekcji "Dokumentacja wiersza polecenia MIDL" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **TypeLibraryName**  
  
     Opcjonalny parametr **ciągu** .  
  
     Określa nazwę pliku biblioteki typów.  
  
     Aby uzyskać więcej informacji, zobacz **/TLB** Option in "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **UndefinePreprocessorDefinitions**  
  
     Opcjonalny parametr **String []** .  
  
     Usuwa wszystkie poprzednie definicje nazw, przekazując nazwę do preprocesora C, tak jak w przypadku dyrektywy `#undefine`. Określ co najmniej jedną wcześniej zdefiniowaną nazwę.  
  
     Aby uzyskać więcej informacji, zobacz sekcję **/u** opcji w artykule "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web. Zobacz również parametr **PreprocessorDefinitions** w tej tabeli.  
  
- **ValidateAllParameters**  
  
     Opcjonalny parametr `Boolean`.  
  
     Jeśli `true`, program generuje dodatkowe informacje o sprawdzaniu błędów, które są używane do przeprowadzania sprawdzania integralności w czasie wykonywania. W przypadku `false`nie są generowane informacje o sprawdzaniu błędów.  
  
     Aby uzyskać więcej informacji, zobacz Opcje **/Robust** i **/no_robust** w sekcji "Dokumentacja wiersza polecenia MIDL" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **Warnaserror —**  
  
     Opcjonalny parametr `Boolean`.  
  
     Jeśli `true`, traktuje wszystkie ostrzeżenia jako błędy.  
  
     Jeśli parametr zadania **WarningLevel** MIDL nie zostanie określony, ostrzeżenia na poziomie domyślnym na poziomie 1 są traktowane jako błędy.  
  
     Aby uzyskać więcej informacji, zobacz Opcje **/WX** w sekcji "Dokumentacja wiersza polecenia MIDL" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web. Zobacz również parametr **WarningLevel** w tej tabeli.  
  
- **WarningLevel**  
  
     Opcjonalny parametr **ciągu** .  
  
     Określa ważność (*poziom ostrzeżenia*) ostrzeżeń do emisji. Żadne ostrzeżenie nie jest emitowane dla wartości 0. W przeciwnym razie jest emitowane ostrzeżenie, jeśli jego poziom ostrzeżeń jest numerycznie mniejszy lub równy podanej wartości.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    |Wartość|Opcja wiersza polecenia|  
    |-----------|--------------------------|  
    |**0**|**/W0**|  
    |**jedno**|**/W1**|  
    |**dwóch**|**/W2**|  
    |**r.3**|**/W3**|  
    |**czwart**|**/W4**|  
  
     Aby uzyskać więcej informacji, zobacz " **/w** " w artykule "MIDL Command-Line Reference" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web. Zobacz również parametr **warnaserror —** w tej tabeli.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
