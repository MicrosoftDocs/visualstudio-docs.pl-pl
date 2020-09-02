---
title: CL — zadanie | Microsoft Docs
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
ms.openlocfilehash: 8307bc2c9efcbbab531754cd2d49fa18b04cc48a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698639"
---
# <a name="cl-task"></a>CL — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawija Visual C++ narzędzia kompilatora, cl.exe. Kompilator tworzy pliki wykonywalne (. exe), pliki bibliotek dołączanych dynamicznie (dll) lub moduły kodu (. module). Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](https://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry zadania **CL** . Większość parametrów zadań i kilku zestawów parametrów odpowiada opcji wiersza polecenia.  
  
- **AdditionalIncludeDirectories**  
  
   Opcjonalny parametr String [].  
  
   Dodaje katalog do listy katalogów, które są przeszukiwane w poszukiwaniu plików dołączanych.  
  
   Aby uzyskać więcej informacji, zobacz [/i (Dodatkowe katalogi dołączane)](https://msdn.microsoft.com/library/3e9add2a-5ed8-4d15-ad79-5b411e313a49).  
  
- **AdditionalOptions**  
  
   Opcjonalny parametr ciągu.  
  
   Lista opcji wiersza polecenia. Na przykład "/*opcja1*  / *opcja2*  / *Option #*". Użyj tego parametru, aby określić opcje wiersza polecenia, które nie są reprezentowane przez żaden inny parametr zadania.  
  
   Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](https://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c).  
  
- **AdditionalUsingDirectories** Opcjonalny parametr String [].  
  
   Określa katalog, który będzie przeszukiwany przez kompilator w celu rozpoznania odwołań do plików przesłanych do dyrektywy **#using** .  
  
   Aby uzyskać więcej informacji, zobacz [/AI (Określ katalogi metadanych)](https://msdn.microsoft.com/library/fb9c1846-504c-4a3b-bb39-c8696de32f6f).  
  
- **AlwaysAppend**  
  
   Opcjonalny parametr ciągu.  
  
   Ciąg, który zawsze jest emitowany w wierszu polecenia. Wartość domyślna to "**/c**".  
  
- **AssemblerListingLocation**  
  
   Tworzy plik listy zawierający kod asemblera.  
  
   Aby uzyskać więcej informacji, zobacz opcja **/Fa** w [/FA,/FA (lista plików)](https://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **AssemblerOutput**  
  
   Opcjonalny parametr ciągu.  
  
   Tworzy plik listy zawierający kod asemblera.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Nolisting** - *\<none>*  
  
  - **AssemblyCode**  -  **/FA**  
  
  - **AssemblyAndMachineCode**  -  **/FAc**  
  
  - **AssemblyAndSourceCode**  -  **/FAS**  
  
  - **Wszystkie**  -  **/FACS**  
  
    Aby uzyskać więcej informacji, zobacz Opcje **/Fa**, **/FAc**, **/FAS**i **/FACS** w [/FA,/FA (lista plików)](https://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **BasicRuntimeChecks**  
  
   Opcjonalny parametr ciągu.  
  
   Włącza i wyłącza funkcję sprawdzania błędów czasu wykonywania w połączeniu z [runtime_checks](https://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b) pragma.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Wartooć** -                          *\<none>*  
  
  - **StackFrameRuntimeCheck**  -  **/RTCs**  
  
  - **UninitializedLocalUsageCheck**  -  **/RTCu**  
  
  - **EnableFastChecks**  -                           **/RTC1**  
  
    Aby uzyskać więcej informacji, zobacz [/RTC (sprawdzanie błędów czasu wykonywania)](https://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368).  
  
- **BrowseInformation**  
  
   Opcjonalny parametr logiczny.  
  
   Jeśli `true` , program tworzy plik informacji o przeglądaniu.  
  
   Aby uzyskać więcej informacji, zobacz opcja **/fr** w [/fr,/fr (Create. Plik SBR)](https://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896).  
  
- **BrowseInformationFile**  
  
   Opcjonalny parametr ciągu.  
  
   Określa nazwę pliku dla pliku informacji o przeglądaniu.  
  
   Aby uzyskać więcej informacji, zobacz **BrowseInformation** parametr w tej tabeli, a także zobacz [/fr,/fr (Create. Plik SBR)](https://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896).  
  
- **BufferSecurityCheck**  
  
   Opcjonalny parametr logiczny.  
  
   Jeśli `true` program wykryje pewne przepełnienia buforów, które zastępują adres zwrotny, typową techniką wykorzystania kodu, który nie wymusza ograniczeń rozmiaru buforu.  
  
   Aby uzyskać więcej informacji, zobacz [/GS (sprawdzanie zabezpieczeń bufora)](https://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e).  
  
- **BuildingInIDE**  
  
   Opcjonalny parametr logiczny.  
  
   Jeśli `true` , wskazuje, że program **MSBuild** jest wywoływany przez IDE. W przeciwnym razie program **MSBuild** jest wywoływany w wierszu polecenia.  
  
- **CallingConvention**  
  
   Opcjonalny parametr ciągu.  
  
   Określa konwencję wywoływania, która określa kolejność, w której argumenty funkcji są wypychane na stosie, niezależnie od tego, czy funkcja wywołująca lub wywoływana funkcja usuwa argumenty ze stosu na końcu wywołania, oraz Konwencję Name-dekorowania nazwy, której kompilator używa do identyfikacji poszczególnych funkcji.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **CDECL**  -  **/GD**  
  
  - **FastCall**  -                           **/Gr**  
  
  - **Stdcall**  -                           **/GZ**  
  
    Aby uzyskać więcej informacji, zobacz [/GD,/gr,/GV,/GZ (Konwencja wywoływania)](https://msdn.microsoft.com/library/fd3110cb-2d77-49f2-99cf-a03f9ead00a3).  
  
- **CompileAs**  
  
   Opcjonalny parametr ciągu.  
  
   Określa, czy kompilować plik wejściowy jako plik źródłowy C lub C++.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Wartooć** - *\<none>*  
  
  - **CompileAsC**  -  **/TC**  
  
  - **CompileAsCpp**  -  **/TP**  
  
    Aby uzyskać więcej informacji, zobacz [/TC,/TP,/TC,/TP (Określ typ pliku źródłowego)](https://msdn.microsoft.com/library/7d9d0a65-338b-427c-8b48-fff30e2f9d2b).  
  
- **CompileAsManaged**  
  
   Opcjonalny parametr ciągu.  
  
   Umożliwia aplikacjom i składnikom korzystanie z funkcji środowiska uruchomieniowego języka wspólnego (CLR).  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **false** - *\<none>*  
  
  - **wartość true**  -  **/CLR**  
  
  - **Czysty**  -  **/CLR: Pure**  
  
  - **Bezpieczne**  -  **/CLR: Safe**  
  
  - **OldSyntax**  -  **/CLR: oldSyntax**  
  
    Aby uzyskać więcej informacji, zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](https://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).  
  
- **CreateHotpatchableImage**  
  
   Opcjonalny parametr logiczny.  
  
   Jeśli `true` , nakazuje kompilatorowi przygotowanie obrazu do zastosowania *poprawek na gorąco*. Ten parametr zapewnia, że pierwsza instrukcja każdej funkcji ma dwa bajty, co jest wymagane w przypadku stosowania poprawek na gorąco.  
  
   Aby uzyskać więcej informacji, zobacz [/hotpatch (Create możliwy do poprawiania Image)](https://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798).  
  
- **DebugInformationFormat**  
  
   Opcjonalny parametr ciągu.  
  
   Wybiera typ informacji o debugowaniu utworzonych dla programu oraz tego, czy te informacje są przechowywane w plikach obiektu (. obj), czy w bazie danych programu (PDB).  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **OldStyle**  -  **/Z7**  
  
  - **ProgramDatabase**  -  **/Zi**  
  
  - **EditAndContinue**  -  **/Zi**  
  
    Aby uzyskać więcej informacji, zobacz [/Z7,/Zi,/ZI (format informacji o debugowaniu)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).  
  
- **DisableLanguageExtensions**  
  
   Opcjonalny parametr logiczny.  
  
   Jeśli **ma wartość true**, instruuje kompilator, aby emituje błąd dla konstrukcji językowych, które nie są zgodne ze standardem ANSI C lub ANSI C++.  
  
   Aby uzyskać więcej informacji, zobacz opcja **/za** w [/za,/ze (Wyłącz rozszerzenia językowe)](https://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2).  
  
- **DisableSpecificWarnings**  
  
   Opcjonalny parametr String [].  
  
   Wyłącza numery ostrzeżeń, które są określone na liście rozdzielanej średnikami.  
  
   Aby uzyskać więcej informacji, zobacz `/wd` Opcje w opcjach [/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/wo,/WV,/WX (poziom ostrzeżeń)](https://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **EnableEnhancedInstructionSet**  
  
   Opcjonalny parametr ciągu.  
  
   Określa architekturę generowania kodu, który używa instrukcji Streaming SIMD Extensions (SSE) i Streaming SIMD Extensions 2 (SSE2).  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **StreamingSIMDExtensions**  -  **/arch: SSE**  
  
  - **StreamingSIMDExtensions2**  -  **/arch: SSE2**  
  
    Aby uzyskać więcej informacji, zobacz [/arch (x86)](https://msdn.microsoft.com/library/9dd5a75d-06e4-4674-aade-33228486078d).  
  
- **EnableFiberSafeOptimizations**  
  
   Opcjonalny parametr logiczny.  
  
   Jeśli `true` firma obsługuje zabezpieczenia włókna danych przydzielone przy użyciu statycznego magazynu wątków lokalnych, to znaczy dane przydzielone za pomocą `__declspec(thread)` .  
  
   Aby uzyskać więcej informacji, zobacz [/gt (Obsługa bezpiecznego włókna — magazyn lokalny)](https://msdn.microsoft.com/library/071fec79-c701-432b-9970-457344133159).  
  
- **EnablePREfast**  
  
   Opcjonalny parametr logiczny.  
  
   Jeśli `true` , Włącz analizę kodu.  
  
   Aby uzyskać więcej informacji, zobacz [/analyze (analiza kodu)](https://msdn.microsoft.com/library/81da536a-e030-4bd4-be18-383927597d08).  
  
- **ErrorReporting**  
  
   Opcjonalny parametr ciągu.  
  
   Umożliwia dostarczenie informacji o wewnętrznym błędzie kompilatora (lodem) bezpośrednio do firmy Microsoft. Domyślnie ustawienie w obszarze kompilacje IDE jest **monitem** , a ustawienie w kompilacjach w wierszu polecenia jest **kolejką**.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Brak**  -  **/errorReport: brak**  
  
  - **Monituj**  -  **/errorReport: Monituj**  
  
  - **Kolejka**  -  **/errorReport: Queue**  
  
  - **Wyślij**  -  **/errorReport: Wyślij**  
  
    Aby uzyskać więcej informacji, zobacz [/errorreport (zgłaszaj wewnętrzne błędy kompilatora)](https://msdn.microsoft.com/library/819828f8-b0a5-412c-9c57-bf822f17e667).  
  
- **ExceptionHandling**  
  
   Opcjonalny parametr ciągu.  
  
   Określa model obsługi wyjątków, który ma być używany przez kompilator.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **false** - *\<none>*  
  
  - **Async**  -  **/EHa**  
  
  - **Synchronizacja**  -  **/EHsc**  
  
  - **SyncCThrow**  -  **/EHS**  
  
    Aby uzyskać więcej informacji, zobacz [/EH (model obsługi wyjątków)](https://msdn.microsoft.com/library/754b916f-d206-4472-b55a-b6f1b0f2cb4d).  
  
- **ExpandAttributedSource**  
  
   Opcjonalny parametr logiczny.  
  
   Jeśli `true` program utworzy plik listy z rozwiniętymi atrybutami, które zostały dodane do pliku źródłowego.  
  
   Aby uzyskać więcej informacji, zobacz [/FX (Scalanie wstrzykniętego kodu)](https://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560).  
  
- **FavorSizeOrSpeed**  
  
   Opcjonalny parametr ciągu.  
  
   Określa, czy ma być preferowany rozmiar kodu czy szybkość kodu.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Zarówno** - *\<none>*  
  
  - **Rozmiar**  -  **/OS**  
  
  - **Szybkość**  -  **/OT**  
  
    Aby uzyskać więcej informacji, zobacz [/OS,/OT (Preferuj mały kod, Preferuj szybki kod)](https://msdn.microsoft.com/library/9a340806-fa15-4308-892c-355d83cac0f2).  
  
- **FloatingPointExceptions**  
  
   Opcjonalny parametr logiczny.  
  
   Jeśli `true` , włącza niezawodny model wyjątku zmiennoprzecinkowego. Wyjątki będą wywoływane natychmiast po ich wyzwoleniu.  
  
   Aby uzyskać więcej informacji, zobacz opcję/**FP: except** w [/FP (Określ zachowanie zmiennoprzecinkowe)](https://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e).  
  
- **FloatingPointModel**  
  
   Opcjonalny parametr ciągu.  
  
   Ustawia model zmiennoprzecinkowy.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Precyzyjna**  -  **/FP: Precyzyjna**  
  
  - **Strict**  -  **/FP: Strict**  
  
  - **Szybkie**  -  **/FP: szybka**  
  
    Aby uzyskać więcej informacji, zobacz [/FP (Określ zachowanie zmiennoprzecinkowe)](https://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e).  
  
- **ForceConformanceInForLoopScope**  
  
   Opcjonalny parametr logiczny.  
  
   Jeśli `true` , implementuje standardowe zachowanie języka C++ w programie [dla](https://msdn.microsoft.com/library/6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a) pętli, które używają rozszerzeń Microsoft ([/ze](https://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2)).  
  
   Aby uzyskać więcej informacji, zobacz [/Zc: forScope (Wymuszaj zgodność w zakresie pętli for)](https://msdn.microsoft.com/library/3031f02d-3b14-4ad0-869e-22b0110c3aed).  
  
- **ForcedIncludeFiles**  
  
   Opcjonalny `String[]` parametr.  
  
   Powoduje, że preprocesor przetwarza jeden lub więcej określonych plików nagłówkowych.  
  
   Aby uzyskać więcej informacji, zobacz [/Fi (Nazwij plik z wymuszonym dołączeniem)](https://msdn.microsoft.com/library/07e79577-8152-4df9-a64c-aae08c603397).  
  
- **ForcedUsingFiles**  
  
   Opcjonalny parametr **String []** .  
  
   Powoduje, że preprocesor przetwarza jeden lub więcej określonych **#using** plików.  
  
   Aby uzyskać więcej informacji, zobacz [/Fu (nazwa pliku wymuszonego #using)](https://msdn.microsoft.com/library/698f8603-457f-435a-baff-5ac9243d6ca1).  
  
- **FunctionLevelLinking**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` , umożliwia kompilatorowi pakowanie poszczególnych funkcji w postaci spakowanych funkcji (COMDAT).  
  
   Aby uzyskać więcej informacji, zobacz [/Gy (Włącz łączenie na poziomie funkcji)](https://msdn.microsoft.com/library/0d3cf14c-ed7d-4ad3-b4b6-104e56f61046).  
  
- **GenerateXMLDocumentationFiles**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` , powoduje, że kompilator przetwarza komentarze dokumentacji w plikach kodu źródłowego i tworzy plik. xdc dla każdego pliku kodu źródłowego, który zawiera komentarze dokumentacji.  
  
   Aby uzyskać więcej informacji, zobacz [/doc (Przetwarzaj komentarze dokumentacji) (C/C++)](https://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Zobacz również parametr **XMLDocumentationFileName** w tej tabeli.  
  
- **IgnoreStandardIncludePath**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` , program uniemożliwia kompilatorowi wyszukiwanie plików dołączanych w katalogach określonych w ścieżce i zawiera zmienne środowiskowe.  
  
   Aby uzyskać więcej informacji, zobacz [/x (Ignoruj standardowe ścieżki dołączanych plików)](https://msdn.microsoft.com/library/16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef).  
  
- **InlineFunctionExpansion**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa poziom rozwinięcia funkcji wbudowanej dla kompilacji.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Wartooć** - *\<none>*  
  
  - **Wyłączony**  -  **/Ob0**  
  
  - **OnlyExplicitInline**  -  **/OB1**  
  
  - **AnySuitable**  -  **/Ob2**  
  
    Aby uzyskać więcej informacji, zobacz [/ob (rozszerzenie funkcji wbudowanej)](https://msdn.microsoft.com/library/f134e6df-e939-4980-a01d-47425dbc562a).  
  
- **IntrinsicFunctions**  
  
   Opcjonalny `Boolean` parametr.  
  
   W przypadku `true` zastąpienia niektórych wywołań funkcji za pomocą wewnętrznych lub w inny sposób specjalnych form funkcji, która ułatwia działanie aplikacji.  
  
   Aby uzyskać więcej informacji, zobacz [/Oi (Generuj funkcje wewnętrzne)](https://msdn.microsoft.com/library/fa4a3bf6-0ed8-481b-91c0-add7636132b4).  
  
- **MinimalRebuild**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` program włączy minimalną ponowną kompilację, która określa, czy pliki źródłowe c++, które zawierają zmienione definicje klas c++ (przechowywane w plikach nagłówkowych (h)), muszą być ponownie skompilowane.  
  
   Aby uzyskać więcej informacji, zobacz [/GM (Włącz minimalną](https://msdn.microsoft.com/library/d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59)ponowną kompilację).  
  
- **MultiProcessorCompilation**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` używasz wielu procesorów do kompilowania. Ten parametr tworzy proces dla każdego efektywnego procesora na komputerze.  
  
   Aby uzyskać więcej informacji, zobacz [/MP (kompilacja z wieloma procesami)](https://msdn.microsoft.com/library/a932b14a-74fe-4b45-84e4-6bf53f0f5e07). Zobacz również parametr **ProcessorNumber** w tej tabeli.  
  
- **ObjectFileName**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa nazwę lub katalog pliku obiektu (. obj), który ma być używany zamiast domyślnego.  
  
   Aby uzyskać więcej informacji, zobacz [/FO (nazwa pliku obiektu)](https://msdn.microsoft.com/library/0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6).  
  
- **ObjectFiles**  
  
   Opcjonalny parametr **String []** .  
  
   Lista plików obiektów.  
  
- **OmitDefaultLibName**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` , pomija domyślną nazwę biblioteki wykonawczej C z pliku obiektu (. obj). Domyślnie kompilator umieszcza nazwę biblioteki w pliku. obj, aby skierować konsolidator do odpowiedniej biblioteki.  
  
   Aby uzyskać więcej informacji, zobacz [/zl (Pomiń domyślną nazwę biblioteki)](https://msdn.microsoft.com/library/b27d39d0-44d6-498c-84ae-27c1326fee59).  
  
- **OmitFramePointers**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` , pomija tworzenie wskaźników ramek na stosie wywołań.  
  
   Aby uzyskać więcej informacji, zobacz [/Oy (pominięcie wskaźnika ramki)](https://msdn.microsoft.com/library/c451da86-5297-4c5a-92bc-561d41379853).  
  
- **OpenMPSupport**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` , powoduje, że kompilator przetwarza klauzule OpenMP i dyrektywy.  
  
   Aby uzyskać więcej informacji, zobacz [/OpenMP (Włączanie obsługi openmp 2,0)](https://msdn.microsoft.com/library/9082b175-18d3-4378-86a7-c0eb95664e13).  
  
- **Optymalizacja**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa różne optymalizacje kodu dla szybkości i rozmiaru.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Wyłączony**  -  **/Od**  
  
  - **MinSpace**  -  **/O1**  
  
  - **MaxSpeed**  -  **/O2**  
  
  - **Pełny**  -  **/OX**  
  
    Aby uzyskać więcej informacji, zobacz [/O opcje (Optymalizuj kod)](https://msdn.microsoft.com/library/77997af9-5555-4b3d-aa57-6615b27d4d5d).  
  
- **PrecompiledHeader**  
  
   Opcjonalny parametr **ciągu** .  
  
   Podczas kompilowania Utwórz lub użyj prekompilowanego pliku nagłówkowego (. pch).  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **NotUsing** - *\<none>*  
  
  - **Utwórz**  -  **/YC**  
  
  - **Użyj**  -  **/Yu**  
  
    Aby uzyskać więcej informacji, zobacz [/YC (Create prekompilowany plik nagłówkowy)](https://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) i [/Yu (Użyj prekompilowanego pliku nagłówkowego)](https://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f). Zobacz również parametry **PrecompiledHeaderFile** i **PrecompiledHeaderOutputFile** w tej tabeli.  
  
- **PrecompiledHeaderFile**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa nazwę prekompilowanego pliku nagłówkowego do utworzenia lub użycia.  
  
   Aby uzyskać więcej informacji, zobacz [/YC (Create prekompilowany plik nagłówkowy)](https://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) i [/Yu (Użyj prekompilowanego pliku nagłówkowego)](https://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f).  
  
- **PrecompiledHeaderOutputFile**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa nazwę ścieżki prekompilowanego nagłówka zamiast używania domyślnej nazwy ścieżki.  
  
   Aby uzyskać więcej informacji, zobacz [/FP (Name. Plik PCH)](https://msdn.microsoft.com/library/0fcd9cbd-e09f-44d3-9715-b41efb5d0be2).  
  
- **PreprocessKeepComments**  
  
   Opcjonalny `Boolean` parametr.  
  
   If `true` zachowuje komentarze podczas przetwarzania wstępnego.  
  
   Aby uzyskać więcej informacji, zobacz [/c (Zachowaj komentarze podczas przetwarzania wstępnego)](https://msdn.microsoft.com/library/944567ca-16bc-4728-befe-d414a7787f26).  
  
- **PreprocessorDefinitions**  
  
   Opcjonalny `String[]` parametr.  
  
   Definiuje symbol przetwarzania wstępnego dla pliku źródłowego.  
  
   Aby uzyskać więcej informacji, zobacz [/d (Definicje preprocesora)](https://msdn.microsoft.com/library/b53fdda7-8da1-474f-8811-ba7cdcc66dba).  
  
- **PreprocessOutput**  
  
   Opcjonalny `ITaskItem[]` parametr.  
  
   Definiuje tablicę elementów wyjściowych preprocesora, które mogą być używane i emitowane przez zadania.  
  
- **PreprocessOutputPath**  
  
   Opcjonalny `String` parametr.  
  
   Określa nazwę pliku wyjściowego, do którego parametr **PreprocessToFile** zapisuje wstępnie przetworzone dane wyjściowe.  
  
   Aby uzyskać więcej informacji, zobacz [/Fi (Przetwarzaj wstępnie nazwę pliku wyjściowego)](https://msdn.microsoft.com/library/6d0ba983-a8b7-41ec-84f5-b4688ef8efee).  
  
- **PreprocessSuppressLineNumbers**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` program wstępnie przetworzy pliki źródłowe C i C++ i skopiuje wstępnie przetworzone pliki na standardowe urządzenie wyjściowe.  
  
   Aby uzyskać więcej informacji, zobacz [/EP (wstępnie przetwórz do stdout bez dyrektyw #line)](https://msdn.microsoft.com/library/6ec411ae-e33d-4ef5-956e-0054635eabea).  
  
- **PreprocessToFile**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` program wstępnie przetworzy pliki źródłowe C i C++ i zapisze wstępnie przetworzone dane wyjściowe do pliku.  
  
   Aby uzyskać więcej informacji, zobacz [/p (Przetwarzaj wstępnie do pliku)](https://msdn.microsoft.com/library/123ee54f-8219-4a6f-9876-4227023d83fc).  
  
- **ProcessorNumber**  
  
   Opcjonalny `Integer` parametr.  
  
   Określa maksymalną liczbę procesorów do użycia w kompilacji wieloprocesorowej. Tego parametru należy używać w połączeniu z parametrem **MultiProcessorCompilation** .  
  
- **ProgramDataBaseFileName**  
  
   Opcjonalny `String` parametr.  
  
   Określa nazwę pliku bazy danych programu (PDB).  
  
   Aby uzyskać więcej informacji, zobacz [/FD (nazwa pliku bazy danych programu)](https://msdn.microsoft.com/library/3977a9ed-f0ac-45df-bf06-01cedd2ba85a).  
  
- **RuntimeLibrary**  
  
   Opcjonalny `String` parametr.  
  
   Wskazuje, czy moduł wielowątkowy jest biblioteką DLL, i wybiera wersje detaliczne lub debugowania biblioteki wykonawczej.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Wielowątkowe**  -  **/MT**  
  
  - **MultiThreadedDebug**  -  **/MTD**  
  
  - **MultiThreadedDLL**  -  **/MD**  
  
  - **MultiThreadedDebugDLL**  -  **/MDD**  
  
    Aby uzyskać więcej informacji, zobacz [/MD,/MT,/LD (Korzystanie z biblioteki wykonawczej)](https://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579).  
  
- **RuntimeTypeInfo**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` , dodaje kod do sprawdzania typów obiektów C++ w czasie wykonywania (informacje o typie czasu wykonywania).  
  
   Aby uzyskać więcej informacji, zobacz [/gr (Włącz informacje typu run-time)](https://msdn.microsoft.com/library/d1f9f850-dcec-49fd-96ef-e72d01148906).  
  
- **ShowIncludes**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` , powoduje, że kompilator wyprowadza listę plików dołączanych.  
  
   Aby uzyskać więcej informacji, zobacz [/showIncludes (lista plików dołączanych)](https://msdn.microsoft.com/library/0b74b052-f594-45a6-a7c7-09e1a319547d).  
  
- **SmallerTypeCheck**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` program zgłosi błąd czasu wykonywania, jeśli wartość zostanie przypisana do mniejszego typu danych i spowoduje utratę danych.  
  
   Aby uzyskać więcej informacji, zobacz **/RTCc** Option in [/RTC (sprawdzanie błędów czasu wykonywania)](https://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368).  
  
- **Źródła**  
  
   Wymagany parametr interfejsu `ITaskItem[]`.  
  
   Określa listę plików źródłowych rozdzielonych spacjami.  
  
- **StringPooling**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` , umożliwia kompilatorowi utworzenie jednej kopii identycznych ciągów w obrazie programu.  
  
   Aby uzyskać więcej informacji, zobacz [/GF (eliminowanie ciągów zduplikowanych)](https://msdn.microsoft.com/library/bb7b5d1c-8e1f-453b-9298-8fcebf37d16c).  
  
- **StructMemberAlignment**  
  
   Opcjonalny `String` parametr.  
  
   Określa wyrównanie bajtów dla wszystkich elementów członkowskich w strukturze.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Wartość domyślna**  -  **/ZP1**  
  
  - **1Byte**  -  **/ZP1**  
  
  - **2Bytes**  -  **/Zp2**  
  
  - **4Bytes**  -  **/Zp4**  
  
  - **8Bytes**  -  **/ZP8**  
  
  - **16Bytes**  -  **/Zp16**  
  
    Aby uzyskać więcej informacji, zobacz [/ZP (wyrównanie składowej struktury)](https://msdn.microsoft.com/library/5242f656-ed9b-48a3-bc73-cfcf3ed2520f).  
  
- **SuppressStartupBanner**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` , program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.  
  
   Aby uzyskać więcej informacji, zobacz [/nologo (Pomijaj transparent startowy) (C/C++)](https://msdn.microsoft.com/library/75930d8b-b11c-4db8-99e5-b52f97da0693).  
  
- **Katalog trackerlogdirectory**  
  
   Opcjonalny `String` parametr.  
  
   Określa katalog pośredni, w którym są przechowywane dzienniki śledzenia dla tego zadania.  
  
   Aby uzyskać więcej informacji, zobacz parametry **TLogReadFiles** i **TLogWriteFiles** w tej tabeli.  
  
- **TreatSpecificWarningsAsErrors**  
  
   Opcjonalny parametr **String []** .  
  
   Traktuje określoną listę ostrzeżeń kompilatora jako błędy.  
  
   Aby uzyskać więcej informacji, zobacz **/we** `n` opcja w [/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/wo,/WV,/WX (poziom ostrzeżenia)](https://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **TreatWarningAsError**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` wszystkie ostrzeżenia kompilatora mają być traktowane jako błędy.  
  
   Aby uzyskać więcej informacji, zobacz **/WX** Option in [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/wo,/WV,/WX (poziom ostrzeżeń)](https://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **TreatWChar_tAsBuiltInType**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` Typ ma być traktowany `wchar_t` jako typ natywny.  
  
   Aby uzyskać więcej informacji, zobacz [/Zc: wchar_t (Wchar_t jest typem natywnym)](https://msdn.microsoft.com/library/b0de5a84-da72-4e5a-9a4e-541099f939e0).  
  
- **UndefineAllPreprocessorDefinitions**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` , definiuje zdefiniowane przez kompilator symbole specyficzne dla firmy Microsoft.  
  
   Aby uzyskać więcej informacji, zobacz **/u** opcji w [/u,/u (Usuń definicje symboli)](https://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a).  
  
- **UndefinePreprocessorDefinitions**  
  
   Opcjonalny `String[]` parametr.  
  
   Określa listę co najmniej jednego symbolu preprocesora do usunięcia.  
  
   Aby uzyskać więcej informacji, zobacz **/u** opcji w [/u,/u (Usuń definicje symboli)](https://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a).  
  
- **UseFullPaths**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` , wyświetla pełną ścieżkę do plików kodu źródłowego przekazaną do kompilatora w diagnostyce.  
  
   Aby uzyskać więcej informacji, zobacz [/FC (Pełna ścieżka pliku kodu źródłowego w diagnostyce)](https://msdn.microsoft.com/library/1f11414e-cb42-421b-be68-9d369aab036b).  
  
- **UseUnicodeForAssemblerListing**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` , powoduje, że plik wyjściowy zostanie utworzony w formacie UTF-8.  
  
   Aby uzyskać więcej informacji, zobacz opcja **/FAU** w [/FA,/FA (lista plików)](https://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
- **WarningLevel**  
  
   Opcjonalny `String` parametr.  
  
   Określa najwyższy poziom ostrzeżeń, który ma zostać wygenerowany przez kompilator.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **TurnOffAllWarnings**  -  **/W0**  
  
  - **Level1**  -  **/W1**  
  
  - **Level2**  -  **/W2**  
  
  - **LEVEL3**  -  **/W3**  
  
  - **Level4**  -  **/W4**  
  
  - **Włącz wszystkie ostrzeżenia**  -  **/Wall**  
  
    Aby uzyskać więcej informacji, zobacz sekcję **/w**_n_ w opcjach [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/wo,/WV,/WX (poziom ostrzeżeń)](https://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
- **WholeProgramOptimization**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` , włącza optymalizację całego programu.  
  
   Aby uzyskać więcej informacji, zobacz [/GL (Optymalizacja całego programu)](https://msdn.microsoft.com/library/09d51e2d-9728-4bd0-b5dc-3b8284aca1d1).  
  
- **XMLDocumentationFileName**  
  
   Opcjonalny `String` parametr.  
  
   Określa nazwę wygenerowanego pliku dokumentacji XML. Ten parametr może być nazwą pliku lub katalogu.  
  
   Aby uzyskać więcej informacji, zobacz `name` argument w [/doc (Przetwarzaj komentarze dokumentacji) (C/C++)](https://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Zobacz również parametr **GenerateXMLDocumentationFiles** w tej tabeli.  
  
- **MinimalRebuildFromTracking**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` jest wykonywana śledzona kompilacja przyrostowa; w przypadku `false` przetworzenia odbudowy.  
  
- **TLogReadFiles**  
  
   Opcjonalny `ITaskItem[]` parametr.  
  
   Określa tablicę elementów, które reprezentują *dzienniki śledzenia plików odczytywane*.  
  
   Dziennik śledzenia plików (. tlog) zawiera nazwy plików wejściowych, które są odczytywane przez zadanie i są używane przez system kompilacji projektu do obsługi kompilacji przyrostowych. Aby uzyskać więcej informacji, zobacz parametry **katalog trackerlogdirectory** i **TrackFileAccess** w tej tabeli.  
  
- **TLogWriteFiles**  
  
   Opcjonalny `ITaskItem[]` parametr.  
  
   Określa tablicę elementów, które reprezentują *dzienniki śledzenia plików zapisu*.  
  
   Dziennik śledzenia plików zapisu (. tlog) zawiera nazwy plików wyjściowych, które są zapisywane przez zadanie, i jest używany przez system kompilacji projektu do obsługi kompilacji przyrostowych. Aby uzyskać więcej informacji, zobacz parametry **katalog trackerlogdirectory** i **TrackFileAccess** w tej tabeli.  
  
- **TrackFileAccess**  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` śledzi wzorce dostępu do plików.  
  
   Aby uzyskać więcej informacji, zobacz parametry **TLogReadFiles** i **TLogWriteFiles** w tej tabeli.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
