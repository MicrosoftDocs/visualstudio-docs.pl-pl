---
title: Tylko mój kod | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 84f0b3b10ba64a820b1088c381787dd1f7c71b8e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54777898"
---
# <a name="just-my-code"></a>Tylko mój kod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Deweloperzy korzystający z języków .NET Framework znają tylko mój kod funkcji debugera, kroki przez system, framework i innymi wywołaniami niespowodowanymi przez użytkownika, która zwija te wywołania w oknach stos wywołań. Tylko mój kod został rozszerzony dla języków C++ i JavaScript. W tym temacie opisano szczegółowe informacje na temat używania tylko mój kod w .NET Framework, natywnego języka C++ i JavaScript projektów.  
  
##  <a name="BKMK_Enable_or_disable_Just_My_Code"></a> Włącz lub wyłącz opcję tylko mój kod  
 Aby włączyć lub wyłączyć opcję tylko mój kod, wybierz opcję **opcje i ustawienia** na **debugowania** menu. W **debugowanie** / **ogólne** węzła, wybierz lub wyczyść **Włącz tylko mój kod**.  
  
 ![Włącz opcję tylko mój kod w oknie dialogowym Opcje](../debugger/media/dbg-justmycode-options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
>  **Włącz tylko mój kod** ustawienie jest ustawieniem globalnym, która jest stosowana do wszystkich projektów programu Visual Studio, we wszystkich językach.  
  
###  <a name="BKMK_Override_call_stack_filtering"></a> Zastąp filtrowanie stosu wywołań  
 W wyświetlaniu stosu wywołań, takich jak okna stosu wywołań i zadań, tylko mój kod zwinięte niebędący kodem użytkownika do ramka z adnotacją etykietą `[External Code]`. Aby wyświetlić zwinięte ramek, wybierz **Pokaż kod zewnętrzny** na menu kontekstowe stosu wywołań wyświetlane.  
  
> [!NOTE]
>  **Pokaż kod zewnętrzny** ustawienia są zapisywane do profilera bieżącego użytkownika. Jest stosowana do wszystkich projektów we wszystkich językach, które są otwierane przez użytkownika.  
  
##  <a name="BKMK__NET_Framework_Just_My_Code"></a> .NET framework tylko mój kod  
  
###  <a name="BKMK_NET_User_and_non_user_code"></a> Kod użytkownika i niezwiązanych z użytkownikiem  
 Aby rozróżnić kod użytkownika z poziomu kodu niepochodzącego od użytkownika, tylko mój kod patrzy na pliki symboli (.pdb) i optymalizacje program. Debuger uważa kod za niebędący kodem użytkownika, gdy plik binarny jest zoptymalizowane pod kątem lub plik PDB nie jest dostępny.  
  
 Trzy atrybuty wpływa również na debuger uważa się mój kod:  
  
- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> Nakazuje debugerowi, że kod, który jest stosowany do nie jest mój kod.  
  
- <xref:System.Diagnostics.DebuggerHiddenAttribute> Ukrywa kodu z debugerem, nawet wtedy, gdy tylko mój kod jest wyłączona.  
  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> Nakazuje debugerowi, aby przejść przez kod, który zostanie zastosowany do, a nie kod krok po kroku.  
  
  Inny kod jest uważane za kod użytkownika.  
  
###  <a name="BKMK_NET_Stepping_behavior"></a> Zachowanie przechodzenia krok po kroku  
 Gdy użytkownik **Step Into** (skrót klawiaturowy: Kod niezwiązany z użytkownikiem F11), debuger nie wchodzi WE kod do następnej instrukcji użytkownika. Gdy użytkownik **Step Out** (klawiatury: SHIFT + F11), debuger działa do następnego wiersza kodu użytkownika. Jeśli żaden kod użytkownika zostanie osiągnięty, a następnie wykonywanie jest kontynuowane do czasu jej wyjścia, punkt przerwania zostaje trafiony lub wystąpienia wyjątku.  
  
###  <a name="BKMK_NET_Breakpoint_behavior"></a> Zachowanie punktu przerwania  
 Jeśli włączono opcję tylko mój kod, można określić **Przerwij wszystko** (klawiatury: Ctrl + Alt + Break) i zatrzymać wykonywanie w miejscu, w przypadku, gdy nie jest wykonywany kod użytkownika do wyświetlenia. W takiej sytuacji zostanie wyświetlone okno Brak źródła. Jeśli następnie wybierzesz polecenie kroku, debuger spowoduje przejście do następnego wiersza kodu użytkownika.  
  
###  <a name="BKMK_NET_Exception_behavior"></a> Zachowanie wyjątku  
 Jeśli wystąpi nieobsługiwany wyjątek w kodzie niezwiązanych z użytkownikiem, debuger przerywa w wierszu w kodzie użytkownika, w którym został wygenerowany wyjątek.  
  
 Włączenie wyjątku pierwszej szansy wyjątki wiersz kodu użytkownika jest wyróżniony w kolorze zielonym. Stos wywołań Wyświetla ramka z adnotacją etykietą **[kod zewnętrzny]**.  
  
##  <a name="BKMK_C___Just_My_Code"></a> Tylko mój kod w języku C++  
  
###  <a name="BKMK_CPP_User_and_non_user_code"></a> Kod użytkownika i niezwiązanych z użytkownikiem  
 C++ tylko mój kod jest inny niż .NET Framework i JavaScript tylko mój kod, ponieważ przechodzenia krok po kroku zachowanie jest niezależna od zachowania stosu wywołań.  
  
 **Stosy wywołań**  
  
 Domyślnie debuger uważa za kod niezwiązany z użytkownikiem w oknach stos wywołań tych funkcji:  
  
- Funkcje za pomocą informacji o źródle pozbawionego włókien w pliku symboli.  
  
- Funkcje, w której pliki symboli oznacza, że brak pliku źródłowego, odpowiadający ramki stosu.  
  
- Określona w funkcji `*.natjmc` pliki `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` folderu.  
  
  **Przechodzenie krok po kroku**  
  
  Domyślnie tylko funkcje określone w `*.natstepfilter` pliki `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` folderu są uważane za kod niezwiązany z użytkownikiem.  
  
  Możesz utworzyć swój własny `.natstepfilter` i `.natjmc` dostosować przechodzenie krok po kroku i wywoływać zachowanie okna stosu `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`.  
  
###  <a name="BKMK_CPP_Stepping_behavior"></a> Zachowanie przechodzenia krok po kroku  
 Gdy użytkownik **Step Into** (skrót klawiaturowy: Kod niezwiązany z użytkownikiem F11) z kodu użytkownika, debuger nie wchodzi WE kod do następnego wiersza kodu użytkownika. Gdy użytkownik **Step Out** (klawiatury: SHIFT + F11), debuger działa do następnego wiersza kodu użytkownika. Jeśli żaden kod użytkownika zostanie osiągnięty, a następnie wykonywanie jest kontynuowane do czasu jej wyjścia, punkt przerwania zostaje trafiony lub wystąpienia wyjątku.  
  
 Jeśli debuger przerwie działanie na kodzie niezwiązanych z użytkownikiem (na przykład, jeśli polecenie Przerwij wszystko zatrzyma niebędący kodem użytkownika), nadal przechodzenie krok po kroku w kodzie niezwiązanych z użytkownikiem.  
  
###  <a name="BKMK_CPP_Exception_behavior"></a> Zachowanie wyjątku  
 Kiedy debuger uderza w wyjątku, zatrzyma się na wyjątek, niezależnie od tego, czy znajduje się w użytkownika lub kod niezwiązany z użytkownikiem. **User-unhandled** opcji na liście **wyjątki** okno dialogowe, są ignorowane.  
  
###  <a name="BKMK_CPP_Customize_stepping_behavior"></a> Dostosowywanie zachowania przechodzenia krok po kroku  
 Można określić funkcji, aby przejść przez wymienienie ich jako kod niezwiązany z użytkownikiem w `*.natstepfilter` plików.  
  
- Aby określić kod niezwiązany z użytkownikiem dla wszystkich użytkowników komputera programu Visual Studio, należy dodać plik .natstepfilter `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` folderu.  
  
- Aby określić kod niezwiązany z użytkownikiem dla poszczególnych użytkowników, należy dodać plik .natstepfilter `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` folderu.  
  
  .natstepfilter pliki są plikami xml o następującej składni:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<StepFilter xmlns="http://schemas.microsoft.com/vstudio/debugger/natstepfilter/2010">  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Action>StepAction</Action>  
    </Function>  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Module>ModuleSpec</Module>  
        <Action>StepAction</Action>  
    </Function>  
</StepFilter>  
  
```  
  
|Element|Opis|  
|-------------|-----------------|  
|Funkcja|Wymagana. Określa jedną lub więcej funkcji jako funkcje niezwiązanych z użytkownikiem.|  
|`Name`|Wymagana. ECMA 262 sformatowane wyrażeń regularnych, określając nazwę pełne działanie do dopasowania. Na przykład:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> Nakazuje debugerowi, że wszystkie metody w `MyNS::MyClass` należy uznać za kod niezwiązany z użytkownikiem. W dopasowaniu jest uwzględniana wielkość liter.|  
|`Module`|Opcjonalna. ECMA 262 sformatowane wyrażeń regularnych, określić pełną ścieżkę do modułu zawierający funkcję. Dopasowanie jest rozróżniana wielkość liter.|  
|`Action`|Wymagana. Jedną z następujących wartości rozróżniana wielkość liter:<br /><br /> -   `NoStepInto`  — Nakazuje debugerowi na wkroczenie za pośrednictwem funkcji dopasowany.<br />-   `StepInto`  — informuje debuger, aby wejść do funkcji dopasowane zastąpienie wszelkich innych `NoStepInto` dopasowane funkcji.|  
  
###  <a name="BKMK_CPP_Customize_call_stack_behavior"></a> Dostosowywanie zachowania dotyczącego stosu wywołań  
 Można określić moduły, pliki źródłowe i funkcji, które mają być traktowane jako kod niezwiązany z użytkownikiem w stosy wywołań, określając je w `*.natjmc` plików.  
  
- Aby określić kod niezwiązany z użytkownikiem dla wszystkich użytkowników komputera programu Visual Studio, należy dodać plik .natjmc `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` folderu.  
  
- Aby określić kod niezwiązany z użytkownikiem dla poszczególnych użytkowników, należy dodać plik .natjmc `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` folderu.  
  
  .natjmc pliki są plikami xml o następującej składni:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<NonUserCode xmlns="http://schemas.microsoft.com/vstudio/debugger/jmc/2015">  
  
  <!-- Modules -->  
  <Module Name="ModuleSpec" />  
  <Module Name="ModuleSpec" Company="CompanyName" />  
  
  <!-- Files -->  
  <File Name="FileSpec"/>  
  
  <!-- Functions -->  
  <Function Name="FunctionSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" ExceptionImplementation="true" />  
  
</NonUserCode>  
  
```  
  
 **Atrybuty elementu modułów**  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagana. Pełna ścieżka moduł lub moduły. Można używać symboli wieloznacznych Windows `?` (zero lub jeden znak) i `*` (zero lub więcej znaków). Na przykład<br /><br /> `<Module Name=”?:\3rdParty\UtilLibs\*” />`<br /><br /> Nakazuje debugerowi Traktuj wszystkie moduły w `\3rdParty\UtilLibs` na dowolnym dysku jako kodu zewnętrznego.|  
|`Company`|Opcjonalna. Nazwa firmy, która publikuje moduł, który jest osadzony w pliku wykonywalnym. Ten atrybut służy do odróżniania modułów.|  
  
 **Atrybuty elementu pliku**  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagana. Pełna ścieżka pliku źródłowego lub pliki, które mają być traktowane jako kodu zewnętrznego. Można używać symboli wieloznacznych Windows `?` i `*` określając ścieżkę.|  
  
 **Atrybuty elementów — funkcja**  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagana. W pełni kwalifikowaną nazwę funkcji, które mają być traktowane jako kodu zewnętrznego.|  
|`Module`|Opcjonalna. Nazwa lub pełną ścieżkę do modułu, która zawiera funkcję. Ten atrybut służy do odróżniania funkcji o tej samej nazwie.|  
|`ExceptionImplementation`|Po ustawieniu `true`, stos wywołań Wyświetla funkcja, która zgłosiła wyjątek, a nie z tej funkcji.|  
  
##  <a name="BKMK_JavaScript_Just_My_Code"></a> Tylko mój kod języka JavaScript  
  
###  <a name="BKMK_JS_User_and_non_user_code"></a> Kod użytkownika i niezwiązanych z użytkownikiem  
 **Klasyfikacje kodu**  
  
 JavaScript tylko mój kod kontrolki przechodzenie krok po kroku, a następnie wywołać wyświetlanie stosu przez skategoryzowanie kodu w jednym z tych klasyfikacji:  
  
|||  
|-|-|  
|**MyCode**|Kod użytkownika, który umożliwia zbieranie i kontrolowanie.|  
|**LibraryCode**|Kod niezwiązany z użytkownikiem z bibliotek, które regularnie używane i aplikacji zależy od działał poprawnie (na przykład WinJS lub jQuery).|  
|**UnrelatedCode**|Kod niezwiązany z użytkownikiem, które mogą być wykonywane w aplikacji, ale nie jest własnością i aplikacja nie bezpośrednio na niej się opierać działał poprawnie (na przykład reklamą zestaw SDK, który wyświetla reklamy). W przypadku projektów Windows Store wszelki kod, który jest ładowany do aplikacji za pomocą protokołu HTTP lub HTTPS identyfikatora URI jest również uważana za UnrelatedCode.|  
  
 Debuger JavaScript klasyfikuje automatycznie tych typów kodu:  
  
- Skrypt, który jest wykonywany, przekazując ciąg do hosta — pod warunkiem `eval` funkcji zostanie sklasyfikowany jako **MyCode**.  
  
- Skrypt, który jest wykonywany, przekazując ciąg do `Function` Konstruktor jest klasyfikowana jako **LibraryCode**.  
  
- Skrypt, który znajduje się w dokumentacji framework, na przykład WinJS lub zestawu Azure SDK zostanie sklasyfikowany jako **LibraryCode**.  
  
- Skrypt, który jest wykonywany, przekazując ciąg do `setTimeout`, `setImmediate`, lub `setInterval` funkcji zostanie sklasyfikowany jako **UnrelatedCode**.  
  
- `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` Określa innego użytkownika i niezwiązanych z użytkownikiem kodu dla wszystkich projektów języka JavaScript w programie Visual Studio.  
  
  Możesz zmodyfikować domyślne klasyfikacje i klasyfikowania plików i adresy URL Dodaj przez plik JSON o nazwie `mycode.json` do folderu głównego projektu.  
  
  Inny kod jest klasyfikowana jako **MyCode**.  
  
###  <a name="BKMK_JS_Stepping_behavior"></a> Zachowanie przechodzenia krok po kroku  
  
-   Jeśli funkcja nie jest użytkownikiem (**MyCode**) kod, **Step Into** (skrót klawiaturowy: F11), który zachowuje się jak **Step Over** (klawiatury: F10).  
  
-   Jeśli krok rozpoczyna się w niezwiązanych z użytkownikiem (**LibraryCode** lub **UnrelatedCode**) kodu, a następnie tymczasowo przechodzenie krok po kroku zachowuje się tak, jakby nie włączono opcję tylko mój kod. Jak najszybciej po kroku do kodu użytkownika, tylko mój kod przechodzenie krok po kroku zostanie ponownie włączony.  
  
-   Gdy krok w kodzie użytkownika skutkuje opuszczania bieżącego kontekstu wykonywania (takich jak krok w ostatnim wierszu programu obsługi zdarzeń), debuger zatrzymuje się w następnym wierszu wykonywany kod użytkownika. Na przykład, jeśli wykonuje wywołanie zwrotne **LibraryCode** Debuger kontynuuje do czasu następnego wiersza kodu użytkownika wykonuje kod.  
  
-   **Wyjdź** (klawiatury: SHIFT + F11) zatrzymuje się w następnym wierszu kodu użytkownika. Jeśli żaden kod użytkownika zostanie osiągnięty, a następnie wykonywanie jest kontynuowane do czasu jej wyjścia, punkt przerwania zostaje trafiony lub wystąpienia wyjątku.  
  
###  <a name="BKMK_JS_Breakpoint_behavior"></a> Zachowanie punktu przerwania  
  
-   Punkty przerwania, które zostały ustawione w dowolny kod zawsze osiągnie niezależnie od klasyfikacji kod  
  
-   Jeśli `debugger` — słowo kluczowe zostanie napotkany w:  
  
    -   **LibraryCode** kod, debuger zawsze przerywa pracę.  
  
    -   **UnrelatedCode** kod, debuger nie zatrzymuje.  
  
###  <a name="BKMK_JS_Exception_behavior"></a> Zachowanie wyjątku  
 Jeśli wystąpi nieobsługiwany wyjątek w:  
  
- **MyCode** lub **LibraryCode** kod, debuger zawsze przerywa pracę.  
  
- **UnrelatedCode** kodu, i **MyCode** lub **LibraryCode** kod znajduje się na stos wywołań, podziały debugera.  
  
  Jeśli pierwszej szansy wyjątki są włączone dla wyjątku w oknie dialogowym Wyjątki, a wyjątek jest zgłaszany w **LibraryCode** lub **UnrelatedCode** kodu:  
  
- Jeśli wyjątek jest obsługiwany, debuger nie zostanie przerwane.  
  
- Jeśli wyjątek nie jest obsługiwany, debuger przerywa.  
  
###  <a name="BKMK_JS_Customize_Just_My_Code"></a> Dostosowywanie tylko mój kod  
 Kategoryzowanie, użytkownika i kod niezwiązany z użytkownikiem dla pojedynczego projektu programu Visual Studio, należy dodać plik JSON o nazwie `mycode.json` do folderu głównego projektu.  
  
 Klasyfikacje są wykonywane w następującej kolejności:  
  
1. Domyślne klasyfikacje  
  
2. Klasyfikacje w `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` pliku  
  
3. Klasyfikacje w `mycode. json` pliku bieżącego projektu.  
  
   Każdy krok klasyfikacji zastąpienia poprzednich kroków. Plik JSON nie konieczne utworzenie listy wszystkich pary klucz-wartość, a **MyCode**, **bibliotek**, i **Unrelated** wartości mogą być puste tablic.  
  
   Pliki kodu JSON, użyj następującej składni:  
  
```json  
{  
    "Eval" : "Classification",  
    "Function" : "Classification",  
    "ScriptBlock" : "Classification",  
    "MyCode" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ],  
    "Libraries" : [  
        "UrlOrFileSpec”,  
        . .  
        "UrlOrFileSpec”  
    ],  
    "Unrelated" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ]  
}  
  
```  
  
 **Eval, funkcja i ScriptBlock**  
  
 **Eval**, **funkcja**, i **ScriptBlock** pary klucz-wartość jak dynamicznie określać jest klasyfikowany wygenerowanego kodu.  
  
|||  
|-|-|  
|**Eval**|Skrypt, który jest wykonywany, przekazując ciąg do hosta — pod warunkiem `eval` funkcji. Domyślnie skrypt — wersja próbna zostanie sklasyfikowany jako **MyCode**.|  
|**Function**|Skrypt, który jest wykonywany, przekazując ciąg do `Function` konstruktora. Domyślnie funkcja skryptu zostanie sklasyfikowany jako **LibraryCode**.|  
|**ScriptBlock**|Skrypt, który jest wykonywany, przekazując ciąg do `setTimeout`, `setImmediate`, lub `setInterval` funkcji. Domyślnie skryptów w blok skryptu zostanie sklasyfikowany jako **UnrelatedCode**.|  
  
 Możesz zmienić wartość, do jednego z tych słów kluczowych:  
  
- `MyCode`  klasyfikuje skryptu jako **MyCode**.  
  
- `Library`  klasyfikuje skryptu jako **LibraryCode**.  
  
- `Unrelated`  klasyfikuje skryptu jako **UnrelatedCode**.  
  
  **MyCode, biblioteki i niepowiązanych**  
  
  **MyCode**, **bibliotek**, i **Unrelated** pary klucz-wartość Określ adresy URL lub pliki, które mają zostać uwzględnione w klasyfikacji:  
  
|||  
|-|-|  
|**MyCode**|Tablicę adresów URL lub pliki, które są klasyfikowane jako **MyCode**.|  
|**Biblioteki**|Tablicę adresów URL lub pliki, które są klasyfikowane jako **LibraryCode**.|  
|**Niepowiązane**|Tablicę adresów URL lub pliki, które są klasyfikowane jako **UnrelatedCode**.|  
  
 Adres url lub plik ciąg może zawierać jeden lub więcej `*` znaków, które dopasowuje zero lub więcej znaków. `*` jest to równoważne wyrażenie regularne `.*`.
