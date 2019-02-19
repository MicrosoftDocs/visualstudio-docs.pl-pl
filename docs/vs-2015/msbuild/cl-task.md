---
title: Cl — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
- vc.task.cl
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), CL task
- CL task (MSBuild (Visual C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 136bc554abe6c231dfa80753b19dba89946830c3
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54756666"
---
# <a name="cl-task"></a>CL — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Opakowuje narzędzie kompilatora Visual C++ cl.exe. Kompilator generuje pliki wykonywalne (.exe), pliki biblioteki dołączanej (dynamicznie dll) lub pliki modułów (.netmodule) kodu. Aby uzyskać więcej informacji, zobacz [opcje kompilatora](http://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **CL** zadania. Większość parametrów zadania oraz kilka zestawów parametrów, odpowiada opcji wiersza polecenia.  
  
- **AdditionalIncludeDirectories**  
  
   Opcjonalny parametr typu String [].  
  
   Dodaje katalog do listy katalogów przeszukiwanych w poszukiwaniu plików dołączanych.  
  
   Aby uzyskać więcej informacji, zobacz [/I (dodatkowe katalogi dołączenia)](http://msdn.microsoft.com/library/3e9add2a-5ed8-4d15-ad79-5b411e313a49).  
  
- **AdditionalOptions**  
  
   Parametr opcjonalny ciąg.  
  
   Listę opcji wiersza polecenia. Na przykład "/*opcja1* /*opcja2* /*opcja #*". Użyj tego parametru, aby określić opcje wiersza polecenia, które nie są reprezentowane przez inne parametry zadania.  
  
   Aby uzyskać więcej informacji, zobacz [opcje kompilatora](http://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c).  
  
- **AdditionalUsingDirectories** opcjonalny ciąg [] parametru.  
  
   Określa katalog, który kompilator będzie przeszukiwał, aby rozwiązać odwołania do plików przekazywane do **#using** dyrektywy.  
  
   Aby uzyskać więcej informacji, zobacz [/AI (Określ katalogi metadanych)](http://msdn.microsoft.com/library/fb9c1846-504c-4a3b-bb39-c8696de32f6f).  
  
- **AlwaysAppend**  
  
   Parametr opcjonalny ciąg.  
  
   Ciąg to zawsze pobiera emitowane w wierszu polecenia. Jego wartość domyślna to "**/c**".  
  
- **AssemblerListingLocation**  
  
   Tworzy plik listingu, który zawiera kod zestawu.  
  
   Aby uzyskać więcej informacji, zobacz **/Fa** opcji [/FA, /Fa (wyświetlanie listy plików)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **AssemblerOutput**  
  
   Parametr opcjonalny ciąg.  
  
   Tworzy plik listingu, który zawiera kod zestawu.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **NoListing** - *\<Brak >*  
  
  - **AssemblyCode** - **/FA**  
  
  - **AssemblyAndMachineCode** - **/FAc**  
  
  - **AssemblyAndSourceCode** - **/FAs**  
  
  - **Wszystkie** -  ** /facs**  
  
    Aby uzyskać więcej informacji, zobacz **/FA**, **/FAC**, **/FAS**, i **/facs** opcji na liście [/FA, /Fa (wyświetlanie listy plików)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **BasicRuntimeChecks**  
  
   Parametr opcjonalny ciąg.  
  
   Włącza i wyłącza funkcję Sprawdzanie błędów czasu wykonywania w połączeniu z [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b) pragmy.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Domyślne** -                          *\<Brak >*  
  
  - **StackFrameRuntimeCheck** - **/RTCs**  
  
  - **UninitializedLocalUsageCheck** - **/RTCu**  
  
  - **EnableFastChecks** -                          **/RTC1**  
  
    Aby uzyskać więcej informacji, zobacz [usunęliśmy (kontrole błąd czasu wykonywania)](http://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368).  
  
- **BrowseInformation**  
  
   Opcjonalny parametr typu Boolean.  
  
   Jeśli `true`, tworzy plik informacji przeglądania.  
  
   Aby uzyskać więcej informacji, zobacz **/FR** opcji [/FR, /Fr (Utwórz. Plik SBR)](http://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896).  
  
- **BrowseInformationFile**  
  
   Parametr opcjonalny ciąg.  
  
   Określa nazwę pliku dla pliku informacyjnego przeglądarki.  
  
   Aby uzyskać więcej informacji, zobacz **BrowseInformation** parametru w tej tabeli, a także znaleźć [/FR, /Fr (Utwórz. Plik SBR)](http://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896).  
  
- **BufferSecurityCheck**  
  
   Opcjonalny parametr typu Boolean.  
  
   Jeśli `true`, wykrywa niektóre przepełnienia buforów, które zastępują adres zwrotny technikę wydobywania kod, który nie wymusza ograniczeń rozmiaru buforu.  
  
   Aby uzyskać więcej informacji, zobacz [/GS (Sprawdzanie zabezpieczeń bufora)](http://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e).  
  
- **BuildingInIDE**  
  
   Opcjonalny parametr typu Boolean.  
  
   Jeśli `true`, oznacza to, że **MSBuild** jest wywoływany przez środowisko IDE. W przeciwnym razie **MSBuild** jest wywoływany w wierszu polecenia.  
  
- **CallingConvention**  
  
   Parametr opcjonalny ciąg.  
  
   Określa konwencję wywołania zamówienia w funkcji argumenty są wypychane na stosie, należy określić, czy wywołujący funkcję lub wywołana funkcja usuwa argumenty ze stosu na końcu wywołania, oraz Konwencję dekorowania nazwy, Kompilator używa do identyfikowania poszczególnych funkcji.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Cdecl** - **/Gd**  
  
  - **FastCall** -                          **/Gr**  
  
  - **StdCall** -                          **/Gz**  
  
    Aby uzyskać więcej informacji, zobacz [/Gd, / GR, / GV, /Gz (Konwencja wywoływania)](http://msdn.microsoft.com/library/fd3110cb-2d77-49f2-99cf-a03f9ead00a3).  
  
- **CompileAs**  
  
   Parametr opcjonalny ciąg.  
  
   Określa, czy można skompilować pliku wejściowego jako plik źródłowy C lub C++.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Domyślne** - *\<Brak >*  
  
  - **CompileAsC** - **/TC**  
  
  - **CompileAsCpp** - **/TP**  
  
    Aby uzyskać więcej informacji, zobacz [TP, /Tp, TP, /TP (Określ źródło pliku typu)](http://msdn.microsoft.com/library/7d9d0a65-338b-427c-8b48-fff30e2f9d2b).  
  
- **CompileAsManaged**  
  
   Parametr opcjonalny ciąg.  
  
   Umożliwia aplikacji i składników korzystać z funkcji z środowisko uruchomieniowe języka wspólnego (CLR).  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **FALSE** - *\<Brak >*  
  
  - **true** - **/clr**  
  
  - **Czysty** -  ** /CLR: pure**  
  
  - **Safe** - **/clr:safe**  
  
  - **OldSyntax** - **/clr:oldSyntax**  
  
    Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](http://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).  
  
- **CreateHotpatchableImage**  
  
   Opcjonalny parametr typu Boolean.  
  
   Jeśli `true`, informuje kompilator, aby przygotować obraz dla *poprawki*. Tego parametru gwarantuje, że pierwsza instrukcja każdej funkcji jest dwubajtowa, który jest wymagany dla poprawki.  
  
   Aby uzyskać więcej informacji, zobacz [/hotpatch (Utwórz obraz Hotpatchable)](http://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798).  
  
- **DebugInformationFormat**  
  
   Parametr opcjonalny ciąg.  
  
   Wybiera typ informacji o debugowaniu utworzonych dla programu, czy te informacje są przechowywane w plikach obiektowych (.obj) lub w bazie danych programu (PDB).  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **OldStyle** - **/Z7**  
  
  - **ProgramDatabase** - **/Zi**  
  
  - **EditAndContinue** - **/ZI**  
  
    Aby uzyskać więcej informacji, zobacz [/z7, / zi, /ZI (Format informacji debugowania)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).  
  
- **DisableLanguageExtensions**  
  
   Opcjonalny parametr typu Boolean.  
  
   Jeśli **true**, informuje kompilator będzie emitował błąd dotyczące konstrukcji języka, które nie są zgodne z ANSI C lub ANSI C++.  
  
   Aby uzyskać więcej informacji, zobacz **/Za** opcji [/za, /Ze (Wyłącz rozszerzenia językowe)](http://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2).  
  
- **DisableSpecificWarnings**  
  
   Opcjonalny parametr typu String [].  
  
   Wyłącza numery ostrzeżeń, które są określone w liście rozdzielanej średnikami.  
  
   Aby uzyskać więcej informacji, zobacz `/wd` opcji [Wn /W0, / W1, / W2, / W3, / W4, / W1, / W2, / W3, / W4, / Wall / wo, WV, /WX (poziom ostrzegawczy)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **EnableEnhancedInstructionSet**  
  
   Parametr opcjonalny ciąg.  
  
   Określa architekturę do generowania kodu, który używa rozszerzenia SSE (Streaming SIMD) i instrukcji Streaming SIMD Extensions 2 (SSE2).  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **StreamingSIMDExtensions** - **/arch:SSE**  
  
  - **StreamingSIMDExtensions2** - **SSE2**  
  
    Aby uzyskać więcej informacji, zobacz [/arch (x86)](http://msdn.microsoft.com/library/9dd5a75d-06e4-4674-aade-33228486078d).  
  
- **EnableFiberSafeOptimizations**  
  
   Opcjonalny parametr typu Boolean.  
  
   Jeśli `true`, obsługuje bezpieczeństwo włókien dla danych przydzielonych przy użyciu statycznego magazynu wątków lokalnych, czyli danych przydzielonych przy użyciu `__declspec(thread)`.  
  
   Aby uzyskać więcej informacji, zobacz [/GT (Obsługa włókien magazynu wątków lokalnych)](http://msdn.microsoft.com/library/071fec79-c701-432b-9970-457344133159).  
  
- **EnablePREfast**  
  
   Opcjonalny parametr typu Boolean.  
  
   Jeśli `true`, Włącz analizę kodu.  
  
   Aby uzyskać więcej informacji, zobacz [/ analyze (analiza kodu)](http://msdn.microsoft.com/library/81da536a-e030-4bd4-be18-383927597d08).  
  
- **ErrorReporting**  
  
   Parametr opcjonalny ciąg.  
  
   Pozwala zapewnić wewnętrznych kompilatora-informacje o błędzie (ICE) bezpośrednio do firmy Microsoft. Domyślnie to ustawienie w kompilacjach IDE **monitu** i ustawienie w kompilacji z wiersza polecenia jest **kolejki**.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **None** - **/errorReport:none**  
  
  - **Wiersz** - **/errorReport:prompt**  
  
  - **Queue** - **/errorReport:queue**  
  
  - **Send** - **/errorReport:send**  
  
    Aby uzyskać więcej informacji, zobacz [/errorreport (zgłaszaj wewnętrzne błędy kompilatora)](http://msdn.microsoft.com/library/819828f8-b0a5-412c-9c57-bf822f17e667).  
  
- **ExceptionHandling**  
  
   Parametr opcjonalny ciąg.  
  
   Określa model obsługi wyjątków, aby używane przez kompilator.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **FALSE** - *\<Brak >*  
  
  - **Async** - **/EHa**  
  
  - **Sync** - **/EHsc**  
  
  - **SyncCThrow** - **/EHs**  
  
    Aby uzyskać więcej informacji, zobacz [/EH (Model obsługi wyjątku)](http://msdn.microsoft.com/library/754b916f-d206-4472-b55a-b6f1b0f2cb4d).  
  
- **ExpandAttributedSource**  
  
   Opcjonalny parametr typu Boolean.  
  
   Jeśli `true`, tworzy plik listingu, która została rozszerzona atrybuty, które są wstrzykiwane do pliku źródłowego.  
  
   Aby uzyskać więcej informacji, zobacz [/Fx (Scal wprowadzony kod)](http://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560).  
  
- **FavorSizeOrSpeed**  
  
   Parametr opcjonalny ciąg.  
  
   Określa, czy preferować rozmiar czy prędkość kodu.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Neither** - *\<none>*  
  
  - **Rozmiar** -  ** /OS**  
  
  - **Szybkość** - **/Ot**  
  
    Aby uzyskać więcej informacji, zobacz [/OS, /Ot (Preferuj mały kod, Preferuj szybko kod)](http://msdn.microsoft.com/library/9a340806-fa15-4308-892c-355d83cac0f2).  
  
- **FloatingPointExceptions**  
  
   Opcjonalny parametr typu Boolean.  
  
   Jeśli `true`, umożliwia wiarygodny model wyjątków zmiennopozycyjnych. Wyjątki będą zgłaszane, natychmiast po ich wygenerowaniu.  
  
   Aby uzyskać więcej informacji, zobacz /**fp: except** opcji [/FP (określenie zachowania zmiennopozycyjna)](http://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e).  
  
- **FloatingPointModel**  
  
   Parametr opcjonalny ciąg.  
  
   Ustawia wartość zmiennoprzecinkowa punktu modelu.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Dokładne** -  ** /FP: precise**  
  
  - **Ścisłe** -  ** /FP: strict**  
  
  - **Fast** - **/fp:fast**  
  
    Aby uzyskać więcej informacji, zobacz [/FP (określenie zachowania zmiennopozycyjna)](http://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e).  
  
- **ForceConformanceInForLoopScope**  
  
   Opcjonalny parametr typu Boolean.  
  
   Jeśli `true`, implementuje standardowego zachowania C++ w [dla](http://msdn.microsoft.com/library/6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a) pętli, które należy użyć rozszerzeń firmy Microsoft ([/Ze](http://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2)).  
  
   Aby uzyskać więcej informacji, zobacz [/Zc: forscope (Wymuszaj zgodność w zakresie pętli for)](http://msdn.microsoft.com/library/3031f02d-3b14-4ad0-869e-22b0110c3aed).  
  
- **ForcedIncludeFiles**  
  
   Opcjonalnie `String[]` parametru.  
  
   Powoduje, że preprocesor do przetworzenia jeden lub więcej plików określony nagłówek.  
  
   Aby uzyskać więcej informacji, zobacz [/FI (nazwij wymuszone obejmują plik)](http://msdn.microsoft.com/library/07e79577-8152-4df9-a64c-aae08c603397).  
  
- **ForcedUsingFiles**  
  
   Opcjonalnie **String []** parametru.  
  
   Powoduje, że preprocesora aby przetworzyć jednego lub więcej określonych **#using** plików.  
  
   Aby uzyskać więcej informacji, zobacz [/FU (nazwij wymuszone #using)](http://msdn.microsoft.com/library/698f8603-457f-435a-baff-5ac9243d6ca1).  
  
- **FunctionLevelLinking**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, umożliwia kompilatorowi pakowanie indywidualnych funkcji w formę spakowanych funkcji (Comdat).  
  
   Aby uzyskać więcej informacji, zobacz [/Gy (Włącz łączenie poziomie funkcji)](http://msdn.microsoft.com/library/0d3cf14c-ed7d-4ad3-b4b6-104e56f61046).  
  
- **GenerateXMLDocumentationFiles**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, powoduje, że kompilator, aby przetworzyć dokumentacji komentarzy w kodu pliki źródłowe i Utwórz plik .xdc dla każdego źródła kodu pliku, który ma komentarze dokumentacji.  
  
   Aby uzyskać więcej informacji, zobacz [/doc (Przetwarzaj komentarze dokumentacji) (C/C++)](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Zobacz też **XMLDocumentationFileName** parametru w tej tabeli.  
  
- **IgnoreStandardIncludePath**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, zabezpiecza kompilator przed wyszukiwaniem dołączonych plików w katalogach określonych w zmiennych środowiskowych PATH lub INCLUDE.  
  
   Aby uzyskać więcej informacji, zobacz [/X (Ignoruj standardowe ścieżki dołączanych plików)](http://msdn.microsoft.com/library/16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef).  
  
- **InlineFunctionExpansion**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa poziom rozwijania funkcji inline w kompilacji.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Domyślne** - *\<Brak >*  
  
  - **Wyłączone** - **/Ob0**  
  
  - **OnlyExplicitInline** - **/Ob1**  
  
  - **AnySuitable** - **/Ob2**  
  
    Aby uzyskać więcej informacji, zobacz [/Ob (rozszerzenie funkcji wbudowanej)](http://msdn.microsoft.com/library/f134e6df-e939-4980-a01d-47425dbc562a).  
  
- **IntrinsicFunctions**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, zastępuje niektórych funkcji wywołuje z wewnętrznych lub w przeciwnym razie specjalnych formy funkcji pomagających aplikacji działają szybciej.  
  
   Aby uzyskać więcej informacji, zobacz [/Oi (Generuj funkcje wewnętrzne)](http://msdn.microsoft.com/library/fa4a3bf6-0ed8-481b-91c0-add7636132b4).  
  
- **MinimalRebuild**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, włącza minimalną ponowną kompilację, która określa, czy pliki źródłowe C++, które zawierają zmienione C++ klasy definicje (przechowywane w plikach nagłówków (.h)) musi być ponownie kompilowane.  
  
   Aby uzyskać więcej informacji, zobacz [/Gm (Włącz minimalną ponowną kompilację)](http://msdn.microsoft.com/library/d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59).  
  
- **MultiProcessorCompilation**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, użycie wielu procesorów do skompilowania. Ten parametr tworzy proces dla każdego procesora skuteczne na komputerze.  
  
   Aby uzyskać więcej informacji, zobacz [/MP (kompilacja z wieloma procesami)](http://msdn.microsoft.com/library/a932b14a-74fe-4b45-84e4-6bf53f0f5e07). Zobacz też **ProcessorNumber** parametru w tej tabeli.  
  
- **ObjectFileName**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa nazwę pliku obiektu (.obj) lub katalog ma być używany zamiast domyślnego.  
  
   Aby uzyskać więcej informacji, zobacz [/Fo (nazwa pliku obiektu)](http://msdn.microsoft.com/library/0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6).  
  
- **ObjectFiles**  
  
   Opcjonalnie **String []** parametru.  
  
   Lista plików obiektów.  
  
- **OmitDefaultLibName**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, pomija domyślną nazwę biblioteki wykonawczej języka C z pliku obiektu (.obj). Domyślnie kompilator umieszcza nazwę biblioteki z pliku .obj, aby nakazać konsolidator odpowiedniej biblioteki.  
  
   Aby uzyskać więcej informacji, zobacz [/Zl (Pomiń domyślną nazwę biblioteki)](http://msdn.microsoft.com/library/b27d39d0-44d6-498c-84ae-27c1326fee59).  
  
- **OmitFramePointers**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, pomija tworzenie wskaźników ramek na stosie wywołań.  
  
   Aby uzyskać więcej informacji, zobacz [/Oy (pominięcie wskaźnika ramki)](http://msdn.microsoft.com/library/c451da86-5297-4c5a-92bc-561d41379853).  
  
- **OpenMPSupport**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, powoduje, że kompilator przetwarzania klauzule OpenMP i dyrektywy.  
  
   Aby uzyskać więcej informacji, zobacz [/OpenMP (Włącz obsługę OpenMP 2.0)](http://msdn.microsoft.com/library/9082b175-18d3-4378-86a7-c0eb95664e13).  
  
- **Optymalizacja**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa różne optymalizacje kodu szybkości i rozmiaru.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Wyłączone** - **/Od**  
  
  - **MinSpace** - **/O1**  
  
  - **MaxSpeed** -  ** /O2**  
  
  - **Full** - **/Ox**  
  
    Aby uzyskać więcej informacji, zobacz [/O opcje (Optymalizuj kod)](http://msdn.microsoft.com/library/77997af9-5555-4b3d-aa57-6615b27d4d5d).  
  
- **PrecompiledHeader**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Utwórz lub przy użyciu pliku prekompilowanego pliku nagłówkowego (.pch) podczas kompilacji.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **NotUsing** - *\<Brak >*  
  
  - **Tworzenie** - **/Yc**  
  
  - **Use** - **/Yu**  
  
    Aby uzyskać więcej informacji, zobacz [/Yc (Utwórz prekompilowany plik nagłówkowy)](http://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) i [/Yu (Korzystaj Prekompilowanego pliku nagłówka)](http://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f). Zobacz też **PrecompiledHeaderFile** i **PrecompiledHeaderOutputFile** parametrów w tej tabeli.  
  
- **PrecompiledHeaderFile**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa nazwę prekompilowanego pliku nagłówka do utworzenia lub używania.  
  
   Aby uzyskać więcej informacji, zobacz [/Yc (Utwórz prekompilowany plik nagłówkowy)](http://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) i [/Yu (Korzystaj Prekompilowanego pliku nagłówka)](http://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f).  
  
- **PrecompiledHeaderOutputFile**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa nazwę ścieżki dla prekompilowanego nagłówka, zamiast używać domyślnej nazwy ścieżki.  
  
   Aby uzyskać więcej informacji, zobacz  [ /FP (nazwa. Plik pch)](http://msdn.microsoft.com/library/0fcd9cbd-e09f-44d3-9715-b41efb5d0be2).  
  
- **PreprocessKeepComments**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, zachowuje komentarze podczas przetwarzania wstępnego.  
  
   Aby uzyskać więcej informacji, zobacz [/C (Zachowaj komentarze podczas przetwarzania wstępnego)](http://msdn.microsoft.com/library/944567ca-16bc-4728-befe-d414a7787f26).  
  
- **PreprocessorDefinitions**  
  
   Opcjonalnie `String[]` parametru.  
  
   Definiuje symbol przetwarzania wstępnego dla pliku źródłowego.  
  
   Aby uzyskać więcej informacji, zobacz [/D (definicje preprocesora)](http://msdn.microsoft.com/library/b53fdda7-8da1-474f-8811-ba7cdcc66dba).  
  
- **PreprocessOutput**  
  
   Opcjonalnie `ITaskItem[]` parametru.  
  
   Określa tablicę elementów dane wyjściowe preprocesora, które może być używany i wyemitowane przez zadania.  
  
- **PreprocessOutputPath**  
  
   Opcjonalnie `String` parametru.  
  
   Określa nazwę pliku wyjściowego, do którego **PreprocessToFile** parametr zapisuje wstępnie przetworzone produkty wyjściowe.  
  
   Aby uzyskać więcej informacji, zobacz [/Fi (Przetwarzaj wstępnie dane wyjściowe pliku nazwa)](http://msdn.microsoft.com/library/6d0ba983-a8b7-41ec-84f5-b4688ef8efee).  
  
- **PreprocessSuppressLineNumbers**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`wstępnie przetwarza pliki źródłowe C i C++ oraz kopiuje pliki wstępnie przetworzony do urządzenia wyjścia standardowego.  
  
   Aby uzyskać więcej informacji, zobacz [/EP (wstępnie Przetwórz do stdout bez dyrektyw #line)](http://msdn.microsoft.com/library/6ec411ae-e33d-4ef5-956e-0054635eabea).  
  
- **PreprocessToFile**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`wstępnie przetwarza pliki źródłowe C i C++ i zapisuje wstępnie przetworzone produkty wyjściowe do pliku.  
  
   Aby uzyskać więcej informacji, zobacz [/P (Przetwarzaj wstępnie do pliku)](http://msdn.microsoft.com/library/123ee54f-8219-4a6f-9876-4227023d83fc).  
  
- **ProcessorNumber**  
  
   Opcjonalnie `Integer` parametru.  
  
   Określa maksymalną liczbę procesorów, którą należy używać w kompilacji wieloprocesorowej. Tego parametru należy użyć w połączeniu z **MultiProcessorCompilation** parametru.  
  
- **ProgramDataBaseFileName**  
  
   Opcjonalnie `String` parametru.  
  
   Określa nazwę pliku dla pliku bazy danych (PDB) programu.  
  
   Aby uzyskać więcej informacji, zobacz [/Fd (nazwa pliku bazy danych programu)](http://msdn.microsoft.com/library/3977a9ed-f0ac-45df-bf06-01cedd2ba85a).  
  
- **RuntimeLibrary**  
  
   Opcjonalnie `String` parametru.  
  
   Wskazuje, czy moduł wielowątkowy jest biblioteką DLL i wybiera sprzedaży detalicznej lub debugowania wersji biblioteki wykonawczej.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **MultiThreaded** - **/MT**  
  
  - **MultiThreadedDebug** - **/MTd**  
  
  - **MultiThreadedDLL** - **/MD**  
  
  - **MultiThreadedDebugDLL** - **/MDd**  
  
    Aby uzyskać więcej informacji, zobacz [/ / MD, / MT, /LD (Korzystaj z bibliotek wykonawczych)](http://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579).  
  
- **RuntimeTypeInfo**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, dodaje kod do sprawdzania typów obiektów C++ w czasie wykonywania (informacje typu run-time).  
  
   Aby uzyskać więcej informacji, zobacz [/GR (Włącz Run-Time informacje o typie)](http://msdn.microsoft.com/library/d1f9f850-dcec-49fd-96ef-e72d01148906).  
  
- **ShowIncludes**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, powoduje, że kompilator danych wyjściowych listy plików dołączanych.  
  
   Aby uzyskać więcej informacji, zobacz [/showincludes (Wymień pliki dołączane)](http://msdn.microsoft.com/library/0b74b052-f594-45a6-a7c7-09e1a319547d).  
  
- **SmallerTypeCheck**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, zgłasza błąd w czasie wykonywania, jeśli wartość jest przypisana do mniejszych typów danych i powoduje utratę danych.  
  
   Aby uzyskać więcej informacji, zobacz **/RTCc** opcji [usunęliśmy (kontrole błąd czasu wykonywania)](http://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368).  
  
- **Źródła**  
  
   Wymagane `ITaskItem[]` parametru.  
  
   Określa listę plików źródłowych, rozdzielone spacjami.  
  
- **StringPooling**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, umożliwia kompilatorowi tworzenie po jednej kopii identycznych ciągów w obrazie programu.  
  
   Aby uzyskać więcej informacji, zobacz [/GF (eliminowanie ciągów zduplikowanych)](http://msdn.microsoft.com/library/bb7b5d1c-8e1f-453b-9298-8fcebf37d16c).  
  
- **StructMemberAlignment**  
  
   Opcjonalnie `String` parametru.  
  
   Określa bajtowe wyrównanie dla wszystkich członków w strukturze.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Default** - **/Zp1**  
  
  - **1Byte** - **/Zp1**  
  
  - **2Bytes** - **/Zp2**  
  
  - **4Bytes** - **/Zp4**  
  
  - **8Bytes** - **/Zp8**  
  
  - **16Bytes** - **/Zp16**  
  
    Aby uzyskać więcej informacji, zobacz [/ZP (wyrównanie członka struktury)](http://msdn.microsoft.com/library/5242f656-ed9b-48a3-bc73-cfcf3ed2520f).  
  
- **SuppressStartupBanner**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, uniemożliwia wyświetlanie wiadomości praw autorskich i wersji, podczas uruchamiania zadania.  
  
   Aby uzyskać więcej informacji, zobacz [/nologo (Pomijaj transparent startowy) (C/C++)](http://msdn.microsoft.com/library/75930d8b-b11c-4db8-99e5-b52f97da0693).  
  
- **TrackerLogDirectory**  
  
   Opcjonalnie `String` parametru.  
  
   Określa katalog pośredni, w którym są przechowywane dzienniki śledzenia dla tego zadania.  
  
   Aby uzyskać więcej informacji, zobacz **TLogReadFiles** i **TLogWriteFiles** parametrów w tej tabeli.  
  
- **TreatSpecificWarningsAsErrors**  
  
   Opcjonalnie **String []** parametru.  
  
   Traktuje określona lista ostrzeżenia kompilatora jako błędy.  
  
   Aby uzyskać więcej informacji, zobacz **/we** `n` opcji [Wn /W0, / W1, / W2, / W3, / W4, / W1, / W2, / W3, / W4, / Wall / wo, WV, /WX (poziom ostrzegawczy)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **TreatWarningAsError**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, traktuje wszystkie ostrzeżenia kompilatora jako błędy.  
  
   Aby uzyskać więcej informacji, zobacz **/WX** opcji [Wn /W0, / W1, / W2, / W3, / W4, / W1, / W2, / W3, / W4, / Wall / wo, WV, /WX (poziom ostrzegawczy)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **TreatWChar_tAsBuiltInType**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, Traktuj `wchar_t` typu jako typu natywnego.  
  
   Aby uzyskać więcej informacji, zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](http://msdn.microsoft.com/library/b0de5a84-da72-4e5a-9a4e-541099f939e0).  
  
- **UndefineAllPreprocessorDefinitions**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, jedno anulowanie definicji symboli specyficzne dla firmy Microsoft, które definiuje kompilator.  
  
   Aby uzyskać więcej informacji, zobacz **/u** opcji [/U, /u (Usuń definicje symboli)](http://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a).  
  
- **UndefinePreprocessorDefinitions**  
  
   Opcjonalnie `String[]` parametru.  
  
   Określa listę jednego lub wielu symboli preprocesora usunięcia definicji.  
  
   Aby uzyskać więcej informacji, zobacz **/U** opcji [/U, /u (Usuń definicje symboli)](http://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a).  
  
- **UseFullPaths**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, wyświetla pełną ścieżkę plików kodu źródłowego przekazane do kompilatora w diagnostyce.  
  
   Aby uzyskać więcej informacji, zobacz [/FC (pełna ścieżka z pliku kodu źródłowego w diagnostyce)](http://msdn.microsoft.com/library/1f11414e-cb42-421b-be68-9d369aab036b).  
  
- **UseUnicodeForAssemblerListing**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, powoduje, że plik wyjściowy będzie utworzony w formacie UTF-8.  
  
   Aby uzyskać więcej informacji, zobacz **/fau** opcji [/FA, /Fa (wyświetlanie listy plików)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **Poziom_ostrzeżeń**  
  
   Opcjonalnie `String` parametru.  
  
   Określa najwyższy poziom ostrzeżenia, który ma zostać wygenerowane przez kompilator.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **TurnOffAllWarnings** - **/W0**  
  
  - **Level1** - **/W1**  
  
  - **Level2** - **/W2**  
  
  - **Level3** - **/W3**  
  
  - **Level4** - **/W4**  
  
  - **EnableAllWarnings** -  ** /Wall**  
  
    Aby uzyskać więcej informacji, zobacz **Wn**_n_ opcji [Wn /W0, / W1, / W2, / W3, / W4, / W1, / W2, / W3, / W4, / Wall / wo, WV, /WX (poziom ostrzegawczy)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **WholeProgramOptimization**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, włącza optymalizację całego programu.  
  
   Aby uzyskać więcej informacji, zobacz [/GL (Optymalizacja Całoprogramowa)](http://msdn.microsoft.com/library/09d51e2d-9728-4bd0-b5dc-3b8284aca1d1).  
  
- **XMLDocumentationFileName**  
  
   Opcjonalnie `String` parametru.  
  
   Określa nazwę wygenerowanego pliki dokumentacji XML. Ten parametr może być nazwa pliku lub katalogu.  
  
   Aby uzyskać więcej informacji, zobacz `name` argument [/doc (Przetwarzaj komentarze dokumentacji) (C/C++)](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Zobacz też **GenerateXMLDocumentationFiles** parametru w tej tabeli.  
  
- **MinimalRebuildFromTracking**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, śledzonych kompilacja przyrostowa odbywa się; Jeśli `false`, ponownej kompilacji jest wykonywane.  
  
- **TLogReadFiles**  
  
   Opcjonalnie `ITaskItem[]` parametru.  
  
   Określa tablicę elementów, które reprezentują *odczytać pliku dzienniki śledzenia*.  
  
   Śledzenie odczytu pliku dziennika (.tlog) zawiera nazwy plików wejściowych, które są odczytywane przez zadanie i jest używana przez system kompilacji projektu do obsługi kompilacje przyrostowe. Aby uzyskać więcej informacji, zobacz **katalog TrackerLogDirectory** i **element TrackFileAccess** parametrów w tej tabeli.  
  
- **TLogWriteFiles**  
  
   Opcjonalnie `ITaskItem[]` parametru.  
  
   Określa tablicę elementów, które reprezentują *wpisywanie do pliku tekstowego dzienniki śledzenia*.  
  
   Zapisu pliku dziennika śledzenia (.tlog) zawiera nazwy plików wyjściowych, które są zapisywane przez zadanie i jest używana przez system kompilacji projektu do obsługi kompilacje przyrostowe. Aby uzyskać więcej informacji, zobacz **katalog TrackerLogDirectory** i **element TrackFileAccess** parametrów w tej tabeli.  
  
- **TrackFileAccess**  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, śledzi wzorce dostępu do pliku.  
  
   Aby uzyskać więcej informacji, zobacz **TLogReadFiles** i **TLogWriteFiles** parametrów w tej tabeli.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
