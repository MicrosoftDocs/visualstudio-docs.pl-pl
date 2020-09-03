---
title: Tylko mój kod | Microsoft Docs
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
ms.openlocfilehash: 62da3a36a34a2111bb139765268fbb0bef9b500d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85531927"
---
# <a name="just-my-code"></a>Tylko mój kod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Deweloperzy korzystający z języków .NET Framework są zaznajomieni z funkcją debugera Tylko mój kod, która przechodzi przez system, platformę i inne wywołania niezwiązane z użytkownikiem i zwija te wywołania w oknach stosu wywołań. Tylko mój kod został rozszerzony do języków C++ i JavaScript. W tym temacie opisano informacje dotyczące używania Tylko mój kod w .NET Framework, natywnych projektach C++ i JavaScript.  
  
## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a> Włączać lub wyłączać Tylko mój kod  
 Aby włączyć lub wyłączyć Tylko mój kod, wybierz **Opcje i ustawienia** w menu **Debuguj** . W węźle **Debugging**  /  **Ogólne** debugowanie zaznacz lub wyczyść pole wyboru **Włącz tylko mój kod**.  
  
 ![Włącz Tylko mój kod w oknie dialogowym Opcje](../debugger/media/dbg-justmycode-options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
> Ustawienie **włącz tylko mój kod** jest ustawieniem globalnym, które jest stosowane do wszystkich projektów programu Visual Studio we wszystkich językach.  
  
### <a name="override-call-stack-filtering"></a><a name="BKMK_Override_call_stack_filtering"></a> Przesłoń filtrowanie stosu wywołań  
 W przypadku wyświetlania stosu wywołań, takich jak okna stosu wywołań i zadań, Tylko mój kod zwija kod niebędący użytkownikiem do ramki z adnotacją oznaczonej etykietą `[External Code]` . Aby wyświetlić zwinięte ramki, wybierz polecenie **Pokaż kod zewnętrzny** w menu kontekstowym wyświetlania stosu wywołań.  
  
> [!NOTE]
> Ustawienie **Pokaż kod zewnętrzny** jest zapisywane w profilerze bieżącego użytkownika. Jest on stosowany do wszystkich projektów we wszystkich językach, które są otwierane przez użytkownika.  
  
## <a name="net-framework-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a> .NET Framework Tylko mój kod  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_NET_User_and_non_user_code"></a> Użytkownik i kod niebędący użytkownikiem  
 Aby odróżnić kod użytkownika od kodu niezwiązanego z użytkownikiem, Tylko mój kod sprawdza pliki symboli (. pdb) i optymalizacje programu. Debuger traktuje kod jako niebędący kodem użytkownika, gdy plik binarny jest zoptymalizowany lub nie jest dostępny.  
  
 Trzy atrybuty wpływają również na to, co debuger uważa za mój kod:  
  
- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> informuje debuger, że kod, do którego jest stosowany, nie jest mój kod.  
  
- <xref:System.Diagnostics.DebuggerHiddenAttribute> ukrywa kod z debugera, nawet jeśli Tylko mój kod jest wyłączone.  
  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> informuje debuger, aby przeprowadził krok po kodzie, do którego jest stosowany, a nie wkroczyć do kodu.  
  
  Cały inny kod jest uznawany za kod użytkownika.  
  
### <a name="stepping-behavior"></a><a name="BKMK_NET_Stepping_behavior"></a> Zachowanie podczas wykonywania  
 Gdy przeniesiesz się **do** (skrót klawiaturowy: F11) kod niebędący użytkownikiem, debuger przeprowadzi procedurę nad kodem do następnej instrukcji użytkownika. Po zakończeniu **czynności** (klawiatura: Shift + F11) debuger przechodzi do następnego wiersza kodu użytkownika. Jeśli żaden kod użytkownika nie zostanie osiągnięty, wykonywanie będzie kontynuowane do momentu zakończenia działania aplikacji, zostanie trafiony punkt przerwania lub wystąpił wyjątek.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_NET_Breakpoint_behavior"></a> Zachowanie punktu przerwania  
 Gdy Tylko mój kod jest włączona, można wybrać pozycję **Przerwij wszystko** (klawiatura: CTRL + ALT + BREAK) i zatrzymać wykonywanie w lokalizacji, w której nie ma kodu użytkownika do wyświetlenia. W takim przypadku nie zostanie wyświetlone okno bez źródła. Jeśli następnie wybierzesz polecenie krok, debuger przeprowadzi Cię do następnego wiersza kodu użytkownika.  
  
### <a name="exception-behavior"></a><a name="BKMK_NET_Exception_behavior"></a> Zachowanie wyjątków  
 Jeśli wystąpił nieobsługiwany wyjątek w kodzie innym niż użytkownik, debuger przerwie się w wierszu w kodzie użytkownika, w którym został wygenerowany wyjątek.  
  
 Jeśli wyjątki pierwszej szansy są włączone dla wyjątku, wiersz User-Code zostanie wyróżniony kolorem zielonym. Stos wywołań wyświetla ramkę z adnotacjami z etykietą **[kod zewnętrzny]**.  
  
## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a> Tylko mój kod języka C++  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_CPP_User_and_non_user_code"></a> Użytkownik i kod niebędący użytkownikiem  
 Tylko mój kod języka C++ różni się od .NET Framework i języka JavaScript Tylko mój kod ponieważ zachowanie krokowe jest niezależne od zachowania stosu wywołań.  
  
 **Stosy wywołań**  
  
 Domyślnie debuger traktuje te funkcje jako kod niebędący użytkownikiem w oknach stosu wywołań:  
  
- Funkcje z usuniętymi informacjami o źródle w ich pliku symboli.  
  
- Funkcja, w której pliki symboli wskazują, że nie ma pliku źródłowego odpowiadającego ramce stosu.  
  
- Funkcje określone w `*.natjmc` plikach w `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` folderze.  
  
  **Wzmacnia**  
  
  Domyślnie tylko funkcje określone w `*.natstepfilter` plikach w `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` folderze są uznawane za kod niebędący użytkownikiem.  
  
  Możesz utworzyć własne `.natstepfilter` i `.natjmc` dostosować zachowanie funkcji krokowe i stosu wywołań w `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` .  
  
### <a name="stepping-behavior"></a><a name="BKMK_CPP_Stepping_behavior"></a> Zachowanie podczas wykonywania  
 Po przełączeniu się **do** (skrótu klawiaturowego: F11) kodu niepochodzącego od użytkownika z kodu użytkownika debuger przeprowadzi procedurę od kodu do następnego wiersza kodu użytkownika. Po zakończeniu **czynności** (klawiatura: Shift + F11) debuger przechodzi do następnego wiersza kodu użytkownika. Jeśli żaden kod użytkownika nie zostanie osiągnięty, wykonywanie będzie kontynuowane do momentu zakończenia działania aplikacji, zostanie trafiony punkt przerwania lub wystąpił wyjątek.  
  
 Jeśli debuger przerwie się w kodzie nieużytkownika (na przykład jeśli polecenie break All zatrzyma się w kodzie innym niż użytkownik), krok kontynuuje w kodzie niewykonywanym przez użytkownika.  
  
### <a name="exception-behavior"></a><a name="BKMK_CPP_Exception_behavior"></a> Zachowanie wyjątków  
 Gdy debuger trafi na wyjątek, zostanie zatrzymany na wyjątku bez względu na to, czy znajduje się on w kodzie użytkownika, czy nie użytkownika. Opcje **nieobsługiwane przez użytkownika** w oknie dialogowym **wyjątki** są ignorowane.  
  
### <a name="customize-stepping-behavior"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a> Dostosuj zachowanie krok po kroku  
 Możesz określić funkcje do przekroczenia, wymieniając je jako kod niebędący użytkownikiem w `*.natstepfilter` plikach.  
  
- Aby określić kod niebędący użytkownikiem dla wszystkich użytkowników maszyny programu Visual Studio, należy dodać plik. natstepfilter do `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` folderu.  
  
- Aby określić kod niebędący użytkownikiem dla pojedynczego użytkownika, należy dodać plik. natstepfilter do `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` folderu.  
  
  pliki. natstepfilter są plikami XML o następującej składni:  
  
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
|Funkcja|Wymagany. Określa jedną lub więcej funkcji jako funkcji niebędących użytkownikami.|  
|`Name`|Wymagany. Sformatowane wyrażenie regularne ECMA-262 określające pełną nazwę funkcji do dopasowania. Na przykład:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> informuje debuger, że wszystkie metody w `MyNS::MyClass` są uznawane za kod niebędący użytkownikiem. W dopasowaniu jest rozróżniana wielkość liter.|  
|`Module`|Opcjonalny. Sformatowane wyrażenie regularne ECMA-262 określa pełną ścieżkę do modułu zawierającego funkcję. W dopasowaniu nie jest rozróżniana wielkość liter.|  
|`Action`|Wymagany. Jedną z następujących wartości uwzględniających wielkość liter:<br /><br /> -   `NoStepInto`  — informuje debugera, aby przekroczyć dopasowaną funkcję.<br />-   `StepInto`  — informuje debugera, aby przekroczyć dopasowane funkcje, zastępując wszelkie inne `NoStepInto` dla dopasowanych funkcji.|  
  
### <a name="customize-call-stack-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a> Dostosuj zachowanie stosu wywołań  
 Można określić moduły, pliki źródłowe i funkcje, które mają być traktowane jak kod niebędący użytkownikiem w stosach wywołań, określając je w `*.natjmc` plikach.  
  
- Aby określić kod niebędący użytkownikiem dla wszystkich użytkowników maszyny programu Visual Studio, należy dodać plik. natjmc do `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` folderu.  
  
- Aby określić kod niebędący użytkownikiem dla pojedynczego użytkownika, należy dodać plik. natjmc do `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` folderu.  
  
  pliki. natjmc są plikami XML o następującej składni:  
  
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
  
 **Atrybuty elementu modułu**  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagany. Pełna ścieżka modułu lub modułów. Możesz użyć symboli wieloznacznych systemu Windows `?` (zero lub jeden znak) i `*` (zero lub więcej znaków). Przykład:<br /><br /> `<Module Name=”?:\3rdParty\UtilLibs\*” />`<br /><br /> nakazuje debugerowi traktowanie wszystkich modułów `\3rdParty\UtilLibs` na dowolnym dysku jako kod zewnętrzny.|  
|`Company`|Opcjonalny. Nazwa firmy, która publikuje moduł osadzony w pliku wykonywalnym. Tego atrybutu można użyć, aby odróżnić moduły.|  
  
 **Atrybuty elementu pliku**  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagany. Pełna ścieżka pliku źródłowego lub plików, które mają być traktowane jako kod zewnętrzny. Możesz użyć symboli wieloznacznych systemu Windows `?` i `*` podczas określania ścieżki.|  
  
 **Atrybuty elementu funkcji**  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagany. W pełni kwalifikowana nazwa funkcji, która ma być traktowana jako kod zewnętrzny.|  
|`Module`|Opcjonalny. Nazwa lub pełna ścieżka do modułu, który zawiera funkcję. Tego atrybutu można użyć, aby odróżnić funkcje o tej samej nazwie.|  
|`ExceptionImplementation`|Po ustawieniu na `true` , stos wywołań wyświetla funkcję, która wywołała wyjątek, a nie tę funkcję.|  
  
## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a> Tylko mój kod JavaScript  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_JS_User_and_non_user_code"></a> Użytkownik i kod niebędący użytkownikiem  
 **Klasyfikacje kodu**  
  
 Język JavaScript Tylko mój kod kontroluje i wywołają Wyświetlanie stosu przez kategoryzację kodu w jednej z tych klasyfikacji:  
  
|Nazwa|Opis|
|-|-|  
|**Kod**|Kod użytkownika, który posiadasz i kontrolujesz.|  
|**LibraryCode**|Kod niebędący użytkownikiem z bibliotek, które są regularnie używane, a aplikacja polega na poprawnym działaniu (na przykład WinJS lub jQuery).|  
|**UnrelatedCode**|Kod niebędący użytkownikiem, który może być uruchomiony w aplikacji, ale nie jest on używany, a aplikacja nie polega na tym, że nie polega ona na poprawnym działaniu (na przykład z reklamowym zestawem SDK wyświetlającym reklamy). W projektach sklepu Windows każdy kod załadowany do aplikacji z identyfikatora URI HTTP lub HTTPS jest również uznawany za UnrelatedCode.|  
  
 Debuger JavaScript automatycznie klasyfikuje następujące typy kodu:  
  
- Skrypt, który jest wykonywany przez przekazanie ciągu do funkcji dostarczonej `eval` przez hosta, jest klasyfikowany jako **kod**.  
  
- Skrypt, który jest wykonywany przez przekazanie ciągu do `Function` konstruktora, jest klasyfikowany jako **LibraryCode**.  
  
- Skrypt, który jest zawarty w odwołaniu do struktury, taki jak WinJS lub zestaw Azure SDK, został sklasyfikowany jako **LibraryCode**.  
  
- Skrypt, który jest wykonywany przez przekazanie ciągu do `setTimeout` `setImmediate` funkcji,, lub `setInterval` jest sklasyfikowany jako **UnrelatedCode**.  
  
- `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json`Określa inny kod użytkownika i inne niż użytkownika dla wszystkich projektów JavaScript programu Visual Studio.  
  
  Klasyfikacje domyślne i klasyfikowanie określonych plików i adresów URL można modyfikować, dodając plik JSON o nazwie `mycode.json` do folderu głównego projektu.  
  
  Wszystkie inne kody są klasyfikowane jako **kod**.  
  
### <a name="stepping-behavior"></a><a name="BKMK_JS_Stepping_behavior"></a> Zachowanie podczas wykonywania  
  
- Jeśli funkcja nie jest kodem User (mój**kod**), **Wkrocz do** (skrót klawiaturowy: F11) zachowuje się tak, jakby przekroczyć (klawiatura: F10). **Step Over**  
  
- Jeśli krok rozpocznie się w kodzie innym niż użytkownik (**LibraryCode** lub **UnrelatedCode**), wówczas stopniowo działa tak, jakby tylko mój kod nie jest włączona. Gdy tylko powrócisz do kodu użytkownika, Tylko mój kod krok po kroku zostanie ponownie włączony.  
  
- Gdy krok w kodzie użytkownika spowoduje opuszczenie bieżącego kontekstu wykonania (na przykład wykonanie kroku na ostatnim wierszu procedury obsługi zdarzeń), debuger zatrzyma się przy następnym wykonaniu kodu użytkownika. Na przykład, jeśli wywołanie zwrotne jest wykonywane w kodzie **LibraryCode** , debuger kontynuuje działanie aż do następnego wiersza kodu użytkownika.  
  
- **Wyjdź** (klawiatura: Shift + F11) przestaje w następnym wierszu kodu użytkownika. Jeśli żaden kod użytkownika nie zostanie osiągnięty, wykonywanie będzie kontynuowane do momentu zakończenia działania aplikacji, zostanie trafiony punkt przerwania lub wystąpił wyjątek.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_JS_Breakpoint_behavior"></a> Zachowanie punktu przerwania  
  
- Punkty przerwania, które zostały ustawione w dowolnym kodzie, zawsze będą trafiać, niezależnie od klasyfikacji tego kodu  
  
- Jeśli `debugger` słowo kluczowe jest napotkane w:  
  
  - Kod **LibraryCode** , debuger zawsze przerwie.  

  - Kod **UnrelatedCode** , debuger nie zatrzyma.  
  
### <a name="exception-behavior"></a><a name="BKMK_JS_Exception_behavior"></a> Zachowanie wyjątków  
 Jeśli wystąpił nieobsługiwany wyjątek w programie:  
  
- **Kod** **LibraryCode** i debuger zawsze są przerywane.  
  
- Kod **UnrelatedCode** **i kod** **LibraryCode** znajduje się na stosie wywołań, a debuger przerywa.  
  
  Jeśli wyjątki pierwszej szansy są włączone dla wyjątku w oknie dialogowym wyjątki, a wyjątek jest zgłaszany w kodzie **LibraryCode** lub **UnrelatedCode** :  
  
- Jeśli wyjątek jest obsługiwany, debuger nie przerywa.  
  
- Jeśli wyjątek nie jest obsługiwany, debuger przerwie.  
  
### <a name="customize-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a> Dostosowywanie Tylko mój kod  
 Aby przydzielić kod użytkownika i niebędący użytkownikiem dla jednego projektu programu Visual Studio, Dodaj plik JSON o nazwie `mycode.json` do folderu głównego projektu.  
  
 Klasyfikacje są wykonywane w następującej kolejności:  
  
1. Klasyfikacje domyślne  
  
2. Klasyfikacje w `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` pliku  
  
3. Klasyfikacje w `mycode. json` pliku bieżącego projektu.  
  
   Każdy krok klasyfikacji zastępuje poprzednie kroki. Plik. JSON nie musi zawierać listy wszystkich par wartości klucza, a element **webcode**, **biblioteki**i **niepowiązane** wartości mogą być pustymi tablicami.  
  
   Moje pliki Code. JSON używają następującej składni:  
  
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
  
 **Eval, Function i ScriptBlock**  
  
 Pary wartość klucza **eval**, **Function**i **ScriptBlock** określają sposób, w jaki kod jest klasyfikowany dynamicznie.  
  
|Nazwa|Opis|
|-|-|  
|**Eval**|Skrypt, który jest wykonywany przez przekazanie ciągu do funkcji dostarczonej przez hosta `eval` . Domyślnie skrypt Eval jest klasyfikowany jako **kod**.|  
|**Funkcja**|Skrypt, który jest wykonywany przez przekazanie ciągu do `Function` konstruktora. Domyślnie skrypt funkcji jest klasyfikowany jako **LibraryCode**.|  
|**ScriptBlock**|Skrypt, który jest wykonywany przez przekazanie ciągu do `setTimeout` `setImmediate` funkcji,, lub `setInterval` . Domyślnie skrypt ScriptBlock jest klasyfikowany jako **UnrelatedCode**.|  
  
 Można zmienić wartość jednego z następujących słów kluczowych:  
  
- `MyCode`  klasyfikuje skrypt jako mój **kod**.  
  
- `Library`  klasyfikuje skrypt jako **LibraryCode**.  
  
- `Unrelated`  klasyfikuje skrypt jako **UnrelatedCode**.  
  
  **Moje kod, biblioteki i niepowiązane**  
  
  Pary **kod**, **biblioteki**i **niepowiązane** wartości klucza określają adresy URL lub pliki, które mają zostać uwzględnione w klasyfikacji:  
  
|Nazwa|Opis|
|-|-|  
|**Kod**|Tablica adresów URL lub plików, które są klasyfikowane jako **kod**.|  
|**Biblioteki**|Tablica adresów URL lub plików, które są klasyfikowane jako **LibraryCode**.|  
|**Niepowiązanych**|Tablica adresów URL lub plików, które są klasyfikowane jako **UnrelatedCode**.|  
  
 Adres URL lub ciąg pliku może zawierać jeden lub więcej `*` znaków, które pasują do zera lub więcej znaków. `*` jest odpowiednikiem wyrażenia regularnego `.*` .
